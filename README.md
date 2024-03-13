# Sentinel-2 Extension Specification

- **Title:** Sentinel-2
- **Identifier:** <https://stac-extensions.github.io/sentinel-2/v1.0.0/schema.json>
- **Field Name Prefix:** s2
- **Scope:** Item
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Stable
- **Owner**: @philvarner

This document explains the Sentinel-2 Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification.

The intention of the first version of the specification is to define the existing behavior of
the properties prefixed with `s2` as created by the [stactools-sentinel2](https://github.com/stactools-packages/sentinel2)
package and used by [Earth Search](https://earth-search.aws.element84.com/v1) and
[Microsoft Planetary Computer](https://planetarycomputer.microsoft.com/api/stac/v1). Future versions
will aspire to standardize fields such as the numerous coverage calculations into separate extensions
that are not specific to Sentinel-2.

- Examples:
  - [Item example](examples/item.json): Shows the basic usage of the extension in a STAC Item
- [JSON Schema](json-schema/schema.json)
- [Changelog](./CHANGELOG.md)

## Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                              | Type     | Description                                    |
| --------------------------------------- | -------- | ---------------------------------------------- |
| s2:tile_id                              | string   | Tile Identifier                                |
| s2:datatake_id                          | string   | Datatake Identifier                            |
| s2:product_uri                          | string   | Product URI                                    |
| s2:datastrip_id                         | string   | Datastrip Identifier                           |
| s2:product_type                         | string   | Product Type                                   |
| s2:datatake_type                        | string   | Datatake Type                                  |
| s2:generation_time                      | datetime | Generation Time                                |
| s2:processing_baseline                  | string   | [Processing Baseline](https://sentinels.copernicus.eu/web/sentinel/technical-guides/sentinel-2-msi/processing-baseline) |
| s2:reflectance_conversion_factor        | number   | Reflectance Conversion Factor                  |
| s2:water_percentage                     | number   | Water Percentage                               |
| s2:snow_ice_percentage                  | number   | Snow and Ice Percentage                        |
| s2:vegetation_percentage                | number   | Vegetation Percentage                          |
| s2:thin_cirrus_percentage               | number   | Thin Cirrus Percentage                         |
| s2:cloud_shadow_percentage              | number   | Cloud Shadow Percentage                        |
| s2:nodata_pixel_percentage              | number   | No Data Pixel Percentage                       |
| s2:unclassified_percentage              | number   | Unclassified Percentage                        |
| s2:dark_features_percentage             | number   | Dark Features Percentage                       |
| s2:not_vegetated_percentage             | number   | Not Vegetated Percentage                       |
| s2:degraded_msi_data_percentage         | number   | Degraded MSI Data Percentage                   |
| s2:high_proba_clouds_percentage         | number   | High Probability Clouds Percentage             |
| s2:medium_proba_clouds_percentage       | number   | Medium Probability Clouds Percentage           |
| s2:saturated_defective_pixel_percentage | number   | Saturated Defective Pixel Percentage           |
| s2:granule_id                           | string   | **DEPRECATED** Granule Identifier              |
| s2:mgrs_tile                            | string   | **DEPRECATED** Sentinel-2 MGRS Tile Identifier |
| s2:mean_solar_zenith                    | number   | **DEPRECATED** Mean Solar Zenith               |
| s2:mean_solar_azimuth                   | number   | **DEPRECATED** Mean Solar Azimuth              |

### Additional Field Information

**s2:granule_id** is deprecated in favor of `s2:tile_id`

**s2:mean_solar_zenith** is deprecated in favor of the View Extension field `view:sun_elevation`

**s2:mean_solar_azimuth** is deprecated in favor of the View Extension field `view:sun_azimuth`

**s2:mgrs_tile** is deprecated in favor the [MGRS Extension](https://github.com/stac-extensions/mgrs) fields

## Relation types

None

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid.
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this
repository and on your command line run:

```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:

```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:

```bash
npm run format-examples
```
