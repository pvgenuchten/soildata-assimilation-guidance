---
title: Overview Download Services
summary: 
authors:
    - Paul van Genuchten
date: 2022-11-10
---

# Overview Download Services

Download services facilitate the download of vector or grid data.

### Minimal

The INSPIRE Atom Service provides a minimal download service implementation on a series of downloadable files placed in a web accessible folder. For every file a 'dataset feed' document can be generated and linked to a service feed describing the 'service'. A metadata record points to the service feed to complete the implementation.

Alternatively, products like [GeoNetwork](https://geonetwork-opensource.org/manuals/3.10.x/en/tutorials/inspire/download-atom.html) and Hale Connect (Annex 1) can provide an Atom interface on top of a set of registered datasets. The [TG download services](https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services) also provides some PHP scripts which create an Atom OpenSearch interface for a series of files.

| Cookbook | Software | Description |
| --- | --- | --- |
| [Webdav](tools/webdav.md) | [Wsgidav](https://wsgidav.readthedocs.io) | Setting up atom service using webdav |
| [GeoNetwork Atom](tools/geonetwork.md) | [GeoNetwork](https://geonetwork-opensource.org) | Atom download service from GeoNetwork |

### Traditional

[Web Feature Service](https://www.ogc.org/standards/wfs) (WFS) and [Web Coverage Service](https://www.ogc.org/standards/wcs) (WCS) are commonly used to download Featurecollections (vector) and Coverages (grids). Consider that most of the INSPIRE themes (including soil) require publication of hierarchical (app-schema) features, this aspect is not supported by many WFS server implementations. Some tools with this capability are listed in the table below. For WCS a [good practice](https://inspire-wcs.eu/) is available to facilitate implementation.

| Cookbook | Software | Description |
| --- | --- | --- |
| [deegree](tools/deegree.md) | [deegree](https://deegree.org) | Java based feature server implementations which also includes WMS, WMTS, CSW, WCS interfaces, deegree facilitates on the fly transformation from relational data as well as publication of pregenerated xml fragments.|
| Xtraserver | [XtraServer](https://www.interactive-instruments.de/en/xtraserver/) / [ArcGIS](https://enterprise.arcgis.com/en/inspire/) | Xtraserver, either standalone or as INSPIRE plugin for ArcGIS, facilitates on the fly transformation of relational data to INSPIRE GML as part of the WFS service definition. The developers of Xtraserver lead the GML working group at OGC |
| [GeoServer](tools/geoserver.md) | [GeoServer](https://geoserver.org/) | The app-schema plugin extends the WFS implementation with support for hierarchical features. On the fly transformation is managed from a configuration file. Marcus Sen (Onegeology) create a [cookbook for this approach](http://www.onegeology.org/docs/technical/OneGeologyWFSCookbook_v1.4.pdf). |
| [Get started with Hale Connect](https://help.wetransform.to/docs/getting-started/2018-04-28-quick-start) | [Hale Connect](https://www.wetransform.to/products/haleconnect/) | Optimized for performance, stores pregeneralised xml fragments in combination with an elastic search index for filtering |
| [Good practice on coverage data](https://inspire.rasdaman.org/) | [Rasdaman](http://www.rasdaman.org/) | A Web Coverage Service implementation |

Consider that a product advertising WFS support does not automatically qualify for INSPIRE, the product has to support hierarchical GML.

### Experimental

As described in the harmonization paragraph, Sensor Observation Service and SensorThings API offer an alternative download option for themes including much observation data, such as Soil.

A good practice document has been adopted on the [use of OGC API Features as download service](https://inspire.ec.europa.eu/good-practice/ogc-api-%E2%80%93-features-inspire-download-service). With its 20 years of history WFS and GML are out of synch with current IT practices. OGC API is a new direction of standards within OGC adopting some of the latest IT conventions, such as Open API, Rest services, JSON encodings, content negotiation, etc. The use of OGC API will increase in coming years while OGC adopts more standards and good practice documents around these standards will be written and adopted by JRC. Various products exist implementing the final and/or draft specifications.

A SPARQL endpoint is a typical endpoint for downloading data within the semantic web. In the table below some guidance on various approaches to the semantic web.

GraphQL is an industry standard for queries on hierarchical data using modern api concepts. GraphQL is not frequently associated to Geospatial data, but it would be a good fit for soil data.

| Cookbook | Software | Description |
| --- | --- | --- |
| [pygeoapi](tools/pygeoapi.md) | [pygeoapi](tools/pygeoapi.md) | A python based open source implementation of OGC APIs including OGC API Features. Configuration is managed from a configuration file. |
| LDProxy | [ldproxy](tools/ldproxy.md) | A java based open source implementation of OGC APIs. Originally developed by Interactive Instruments as an easy way to consume API (proxy) on top of existing WFS. These experiments were a main driver for OGC in the direction of OGC API. Configuration is managed from a web interface. |
| [GeoServer](tools/geoserver.md) | [GeoServer](https://geoserver.org) | OGC API is a community plugin of GeoServer, it publishes an alternative endpoint for the datasets published as WFS. |
| [QGIS server](tools/qgis.md) | [QGIS](https://qgis.org) | QGIS Server includes the option to enable OGC API Features access to datasets published as WFS |
| [Cookbook Semantic Web](https://doi.org/10.15454/YJLFZI/OGHA0V) | [Blazegraph](https://blazegraph.com/) / [Coby](https://forgemia.inra.fr/anaee-dev/coby) | INRAE prepared a linked data primer for semantic soil data
| [Virtuoso & skosmos](tools/virtuoso.md) | [Virtuoso](https://virtuoso.openlinksw.com/) | Triple store providing a SPARQL endpoint |
| [YARRRML](tools/yarrrml.md) | [yarrrml](https://rml.io/yarrrml) | Human readable declaritive mapping rules for semantic web |
| [Postgraphile](tools/postgraphile.md) | [Postgraphile](https://www.graphile.org/postgraphile/) | Plugin offering graphile access to postgres databases |
