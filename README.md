# Magento Footer JS

A common web development technique to improve page load times is to move JavaScript to the end of the page.  A common frustration for frontend Magento developers is the inability to do this due to the amount of inline JavaScript found in templates.

This is an experimental plugin that observes for the `core_block_abstract_to_html_after` event, removes any javascript it finds and appends it to a block at the end of the page. 

An example of the HTML produced can be found in the attached file `product_page_example.html`.

Prelimnary tests in Chrome Mac OS X show that there are no console errors on home, category, product, cart and checkout pages.

# Known Issues

- The scripts are currently outputted after the closing `</html>` tag.  Trying to attach it to `before_body_end` was causing an issue whereby the obsever was running on the `inline.js` block even after adding exceptions. 

- Currently have to handle IE conditional JS separately to ensure we retain the conditionals once moved.  This should be moved into a function, or one regex to rule them all.

# Ideas

- Write out all inline javascript to a new file and include that.
- Cache this file.
