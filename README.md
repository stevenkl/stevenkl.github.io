# stevenkl.github.io



## File structure

* `docs/` -- Contains the generated files, served by github
* `source/` -- Contains all content relevant ressources
* `layout/` -- Contains all templates used for rendering the content
* `meta.ini` -- The content is available in every content and template, accessible like `{{meta.author.name}}`
* `config.ini` -- Contains configuration used by the Loaders and Generators


## Loaders
A Loader is responsible for loading a specific type of ressource, eg. a `*.page/` or `*.post/` ressource.
It must return a valid data structure that is collectible by the main system.

Example `*.post/` ressource
```json
{
	"meta": {}, // content of .meta file
	"content": "Content of file content.md",
	"content_type": "md", // based on the extension of the content file
	"excerpt": "The first paragraph of content",
	"layout": "post", // or whatever is defined in "meta.layout"
}
```


## Generators
A Generator is responsible for generating html from the ressources. Which generator is used for a specific ressource
is determined by its `content_type` field.
The generator uses the defined layout and content data to produce some output. The information from the `meta.ini` file
is always accessible like `{{meta.author.email}}`.
