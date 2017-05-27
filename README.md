# Official Storyblok Node.js client

This client will provide you some helpers for the Storyblok publishing API.

## Install

```
npm install storyblok-node-client
```

## Usage

### Class `Storyblok`

**Parameters**

- `config` Object
- (`endpoint` optional)

**Example**

```javascript
// 1. Require the Storyblok node client
const StoryblokClient = require('./storyblok-node-client');

// 2. Initialize the client with the private key 
// from your space dashboard at https://app.storyblok.com
let Storyblok = new StoryblokClient({
  privateToken: 'xf5dRMMjltLzKOcNgMaU9Att'
});
```

### Activating request cache

The Storyblok nodejs client comes with a caching mechanism.
When initializing the Storyblok client you can define a cache provider for caching the requests on the filesystem or in memory.
To clear the cache you can call `Storyblok.flushCache();`.

```
// For a filesystem cache the path parameter is mandatory
let Storyblok = new StoryblokClient({
  privateToken: 'xf5dRMMjltLzKOcNgMaU9Att',
  cache: {
    type: 'filesystem',
    path: './public/datastorage/'
  }
});

// For the memory cache only the type paramter is required
let Storyblok = new StoryblokClient({
  privateToken: 'xf5dRMMjltLzKOcNgMaU9Att',
  cache: {
    type: 'memory'
  }
});
```

### Method `Storyblok#get`

**Parameters**
- `[return]` Promise, Object `response`
- `path` String, Path (can be `stories`, `stories/*`, `tags`, `datasources`)
- `options` Object, Options can be found in the [API documentation](https://www.storyblok.com/docs/Delivery-Api/get-a-story).

**Example**

```javascript
Storyblok
  .get('stories/home', {
    version: 'draft'
  })
  .then((response) => {
    console.log(response);
  })
  .catch((error) => {
    console.log(error);
  });
```

### Method `Storyblok#flushCache`

**Parameters**

- `[return]` Object, returns the Storyblok client

**Example**

```javascript
Storyblok.flushCache();
```

## Contribution

Fork me on [Github](https://github.com/storyblok/storyblok-node-client)