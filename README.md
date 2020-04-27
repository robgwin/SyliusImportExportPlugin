## This repo is deprecated

InGem's import/export plugin is now maintained here:
https://gitlab.com/challengersports/ingem/shop/plugin-import-export-data

Use that for all new installs.

## Migration

How to migrate an existing install of *this* plugin to the *new* plugin:

1. In your shop's composer.json, *remove* this repository:

```yaml
            "type": "vcs",
            "url": "https://github.com/robgwin/SyliusImportExportPlugin",
            "no-api": true
```

...and *add* the new repository:

```yaml
            "name": "ingem/sylius-plugin-import-export-data",
            "type": "git",
            "url": "ssh://git@gitlab.com/challengersports/ingem/shop/plugin-import-export-data"
```

...and *remove* this from the require block:

`"friendsofsylius/sylius-import-export-plugin": "dev-master"` 

2. Remove the old plugin code:

`rm -r vendor/friendsofsylius/sylius-import-export-plugin`

3. Either run `composer update` or, to avoid a complete update of everything, edit composer.lock and *remove* the old plugin from packages:

```yaml
        {
            "name": "friendsofsylius/sylius-import-export-plugin",
            ...
        },
```

...and remove this from the stability-flags block if it exists:

`friendsofsylius/sylius-import-export-plugin`

4. Add the new plugin:

`composer require ingem/sylius-plugin-import-export-data:dev-master`



