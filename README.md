# openihp-proxy

## Service sandbox

See [systemd services](https://github.com/stephan13360/systemd-services) for information on service sandboxing.

## Continuous deployment

The `proxy/nginx` folder will be recursively written into the `/etc/nginx` location on the proxy server and will overwrite similarly named files at existing locations.

The `proxy/usr` folder will be recursively written into the `/usr/` to setup start the systemctl service as the nginx user rather than root.

## Best practices

- [Setting up server blocks](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04#step-5-%E2%80%93-setting-up-server-blocks-(recommended)) in nginx

## SSL Config

For an idea of how to set up the nginx ssl configuration, see the [Mozilla SSL config generator](https://ssl-config.mozilla.org/) for reference.

### Let's Encrypt

When developing for continuous deployment, please make use of the `--test-cert` flag to avoid being [rate limited](https://letsencrypt.org/docs/rate-limits/). This makes use of the [Let's Encrypt staging servers](https://letsencrypt.org/docs/staging-environment/) rather than the production ones.

> **Note:** The staging environment can be unreliable, but it's still better to use than ending up rate limited and having to wait days to deploy again.
