# Getting started

The OneupFlysystemBundle was developed and tested for Symfony2 version 2.2+.

## Installation
Perform the following steps to install and use the basic functionality of the OneupFlysystemBundle:

* Download OneupFlysystemBundle using Composer
* Enable the bundle
* Configure your filesystems

### Step 1: Download the bundle
Add OneupFlysystemBundle to your composer.json using the following construct:

```json
{
    "require": {
        "oneup/flysystem-bundle": "@stable"
    }
}
```

Now tell composer to download the bundle by running the following command:

```
$> php composer.phar update oneup/flysystem-bundle
```

Composer will now fetch and install this bundle in the vendor directory `vendor/oneup`

**Note**: There are some additional dependencies you will need to install for some of the features:

* The AwsS3v3 adapter requires `"league/flysystem-aws-s3-v3"`
* The AwsS3v2 adapter requires `"league/flysystem-aws-s3-v2"`
* The Azure adapter requires `"league/flysystem-azure"`
* The Copy adapter requires `"league/flysystem-copy"`
* The Dropbox adapter requires `"league/flysystem-dropbox"`
* The GridFS adapter requires `"league/flysystem-gridfs"`
* The Rackspace adapter requires `"league/flysystem-rackspace"`
* The Sftp adapter requires `"league/flysystem-sftp"`
* The WebDav adapter requires `"league/flysystem-webdav"`
* The ZipAdapter adapter requires `"league/flysystem-ziparchive"`
* The adapter caching support requires `"league/flysystem-cached-adapter"`
* The eventable filesystem support requires `"league/flysystem-eventable-filesystem"`

### Step 2: Enable the bundle
Enable the bundle in the kernel:

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Oneup\FlysystemBundle\OneupFlysystemBundle(),
    );
}
```

### Step3: Configure your filesystems
In order to create a filesystem, you first need to create an adapter. An easy example is to define a local adapter
and afterwards create a filesystem based on it.

```yaml
# app/config/config.yml
oneup_flysystem:
    adapters:
        my_adapter:
            local:
                directory: %kernel.root_dir%/cache

    filesystems:
        my_filesystem:
            adapter: my_adapter
```

There are a bunch of adapters for you to use:

* [AwsS3](adapter_awss3.md)
* [Dropbox](adapter_dropbox.md)
* [Ftp](adapter_ftp.md)
* [Local filesystem](adapter_local.md)
* [NullAdapter](adapter_nulladapter.md)
* [Rackspace](adapter_rackspace.md)
* [Sftp](adapter_sftp.md)
* [WebDav](adapter_webdav.md)
* [ZipArchive](adapter_ziparchive.md)
* [GridFS](adapter_gridfs.md)
* [Copy.com](https://github.com/copy-app/php-client-library)

### Step 4: Next steps

After installing and setting up the basic functionality of this bundle you can move on and integrate some more advanced features.

* [Create and use your filesystems](filesystem_create.md)
* [Cache your filesystems](filesystem_cache.md)
* [Plugin filesystems](filesystem_plugin.md)
* [Running the tests](tests.md)
