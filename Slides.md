# Catalog Next

---

## What is Catalog Next
Catalog Next is the “next” innovation of how unfoldingWord does its resource catalog. It isn't a name for the version of the catalog but the whole process in which resources get into the catalog and can be found & retrieved.

Our previous catalog (but currently used by most apps) could be called the Door43 Catalog, or v3, as it relied on all resources being in the Door43-Catalog org on DCS and updates (new versions of the resource) to be manually merged in by a uW staff member into the master branch. This triggered an outside process on AWS (Amazon Web Servies) to build a static catalog.json file at https://api.door43.org/v3/catalog.json

Catalog Next, instead, has the processing done right in the DCS web app itself when ever a resource is updated, storing data to a database table. This allows for a dynmaic catalog which can be easily queried and filtered. This also allows for other instances of DCS, such as hosted on an intranet or on a develoepr's local machine, to have its own catalog that apps can use.

---

## Versioning

Again, Catalog Next is a process by which anyone can add their content to the catalog on DCS, not a version name nor an organization name.

Versioning within Catalog Next has to do with the API endpoint versions, which "tags" both the request and response parameters & payload respectively with a version.

Catalog Next continues its versioning from Door43 Catalog's, which ended at v3. Catalog Next starts at v4 and currently at v5. Any breaking change to the API (parameters, fields or data removed or restructured, but NOT additions) will result in a new version.

See https://git.door43.org/api/catalog/swagger

---

## What it is NOT

Catalog Next is NOT our API for finding translation projects, creating new ones, etc. We continue to do that with the Gitea API repo and org endpoints which our fork of DCS inherits.

HOWEVER, the initial part of the Catalog Next process does lend new proprties returned by the Gitea API about our translation projects, both new and released. This is primarily seen in the repo and owner API endpoints. We call this the **Door43 Metadata** layer.

---

#### Door43 Metadata - Triggers & Data

![[trigggers.png|600]]

---

### Door43 Metadata - DB table

![[mysql.png]]

---

#### Catalog Next - Stages

![[stages.png|700]]

---

## Catalog Next - Querying

**Filter By:**
-   keywords (q=, searches metadata if flag includeMetadata is true, which is default)
-   owner (owner=)
-   repo name (repo=)
-   tag (tag=)
-   stage (stage=, all latest resources in any given stage or higher, default: prod)
-   subject (subject=)
    For valid subjects, see [github.com/unfoldingword/rc-schema](https://github.com/unfoldingWord/rc-schema/blob/master/rc.schema.json#L238)
-   language code (lang=)
-   book/project (book=)

---

## Catalog Next - Filtering

**Sort By: **
(Default is by "language", "subject" and then "tag")
-   subject
-   title
-   tag
-   released (date release \[prod, preprod\], or date of last commit \[draft, latest\])
-   lang (language code)
-   releases (number of releases the repo has)
-   forks (number of forks the repo has)
-   stars (number of stars repo has)

---

## Links

-  **Catalog Next Proposal (2019):** https://forum.door43.org/t/catalog-next-proposal/387
-  **Catalog Next Implementation Proposal (2020):** https://docs.google.com/document/d/1SLjkqHdPEnHJFxfln5iNxjOI6K0D8uCJQrYGCe4uwok/edit?usp=sharing
-  **RC Schema:** https://github.com/unfoldingWord/rc-schema/blob/master/rc.schema.json
	(for validating manifest.yaml files and lists valid subjects)
-  **Catalog Next UI:** https://git.door43.org/catalog
-  **Catalog Next API Swagger:** https://git.door43.org/api/catalog/swagger
-  **This Slideshow:** https://github.com/richmahn/catalog-next
