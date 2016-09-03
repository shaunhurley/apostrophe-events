# apostrophe-events

This bundle provides a complete foundation for displaying upcoming events with the [Apostrophe CMS](http://apostrophenow.org).

The bundle consists of three Apostrophe modules (in a single npm module):

* `apostrophe-events`
* `apostrophe-events-pages`
* `apostrophe-events-widgets`

The `apostrophe-events` module provides the ability to create and edit events and manage their start and end dates and times. There is support for repeating events.

The `apostrophe-events-pages` module displays events on a page. It extends the `apostrophe-pieces-pages` module. The default view displays only upcoming events.

The `apostrophe-events-widgets` module provides an `apostrophe-events` widget, which you can use to select events to appear anywhere on your site. Events that have ended do not appear in widgets.

These three modules extend `apostrophe-pieces`, `apostrophe-pieces-pages` and `apostrophe-pieces-widgets`, and you can extend them further as well.

## Example configuration

For a single collection of events:

```javascript
// in app.js
// We must declare the bundle!
bundles: [ 'apostrophe-events' ],
modules: {
  'apostrophe-events': {},
  'apostrophe-events-pages': {},
  'apostrophe-events-widgets': {},
  'apostrophe-pages': {
    // We must list `apostrophe-events-page` as one of the available page types
    types: [
      {
        name: 'apostrophe-events-page',
        label: 'events'
      },
      {
        name: 'default',
        label: 'Default'
      },
      {
        name: 'home',
        label: 'Home'
      }
    ]
  }
}
```

## Multiple collections of events

One way to create two or more distinct collections of events is to create separate events pages on the site, and use the "with these tags" feature to display only events with certain tags.

Another approach is to `extend` the modules, creating new modules and a completely separate admin bar item for managing the content. If you take this approach, you must set a distinct `name` property when configuring your subclass of `apostrophe-events`, such as `meeting`. This will be value of `type` in the database for each event of this subclass.

The latter approach is often best as it requires less user training to avoid confusion. The former approach has its own advantages, notably that it is easier to aggregate content and have it appear in multiple places intentionally.

