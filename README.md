# docker-npm-gyp-onbuild
This is a base image for [node.js][node.js] [npm][npm] projects that need
node-gyp for installation and can execute simple applications
[ONBUILD][ONBUILD].

## Purpose
This docker image builds on top of the [npm-gyp-build][npm-gyp-build] image,
but adds `ONBUILD` instructions to install the project code into the container
and execute `npm install`.  It also sets the default command to the
often-useful `npm start`.  See also [npm-onbuild][npm-onbuild] for projects that don't require node-gyp.

## Usage
This library is useful with a simple `package.json` and `Dockerfile`.
For example, using the `Dockerfile`:

```dockerfile
FROM nubs/npm-gyp-onbuild:latest
```

you can build an image with dependencies installed like so:

```bash
docker build --tag my-image .
```

To execute the default command (`npm start`), you can simply:

```bash
docker run -it --rm my-image
```

Other commands can also be executed.  For example, to run a test task:

```bash
docker run -it --rm my-image npm test
```

## License
docker-npm-gyp-onbuild is licensed under the MIT license.  See [LICENSE] for
the full license text.

[node.js]: http://nodejs.org/
[npm]: https://www.npmjs.org/
[ONBUILD]: https://docs.docker.com/reference/builder/#onbuild
[npm-gyp-build]: https://github.com/nubs/docker-npm-gyp-build
[npm-onbuild]: https://github.com/nubs/docker-npm-onbuild
[LICENSE]: https://github.com/nubs/docker-npm-gyp-onbuild/blob/master/LICENSE
