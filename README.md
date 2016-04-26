## README

This application should illustrate a bug in sprockets 4.0 sourcemaps generation.

When you run the application, a file sub/directory.js is generated which requires a file sub/a.js.

sub/directory.js contains a sourcemap comment:

```javascript
//# sourceMappingURL=sub/directory.js-814a27ea6902791e96d5fd073c38824839b809b36f0bbc826c29cb9536a067bc.map
```

This comment contains a relative URL, so Chrome DevTools does a request to `/assets/sub/sub/directory.js-814a27ea6902791e96d5fd073c38824839b809b36f0bbc826c29cb9536a067bc.map`. This 404s due to the duplicate `sub` path.
