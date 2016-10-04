#### Page lifecycle

<%- @componentLink('page') %> provides a set of DOM events that will be fired in different moments of its life cycle. Use these events to alter the behavior on each page.

* `init` event is fired after `<ons-page>` is attached to DOM. Use this event to initialize code or dynamic content of a page when it is created.
* `destroy` event is fired before `<ons-page>` is destroyed and prior to DOM detachment. Use this event to clean up or save anything you need.
* `show` event is fired every time `<ons-page>` comes into view, i.e. when a new page is created and shown immediately or when an existing page shows up. Use this event to run code every time a page appears.
* `hide` event is fired every time `<ons-page>` disappear from view, i.e. when a visible page is destroyed or is hidden but still exists in the page stack. Use this event to run code every time a page disappears.

Page lifecycle events will be propagated to the page's descendants so they are correspondingly shown, hidden or destroyed. For example, destroying <%- @componentLink('navigator') %> will throw `hide` event only for the displayed page (navigator's top page) and `destroy` event for every page in navigator's page stack.

```html
<ons-page id="page1">This is a blank page</ons-page>

<script>
document.addEventListener('init', function(event) {
  if (event.target.matches('#page1')) {
    ons.notification.alert('Page 1 is initiated.');
    // Set up content...
  }
}, false);
</script>

```