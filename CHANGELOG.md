# avro-builder changelog

## v1.1.0
- Add support for Avro 1.11
- Add support for decimal logical types.

## v1.0.1
- Bug fix: Fix pretty formatting of schemas for Rails applications that don't 
  use oj or yajl by removing the dependency on multi_json.

## v1.0.0
- Drop support for Avro < 1.9.
- Drop support for Ruby < 2.6.
- Add Ruby 3.0 support.
- Bug fix: Use multi_json to encode schemas and ensure that a JSON encoder
  is always present.

## v0.17.0
- Add support for enum defaults introduced in Avro v1.10.0.

## v0.16.2
- Allow avro version up to v1.10.x. Support will be added for new
  functionality in Avro v1.10 in a later release.

## v0.16.1
- Require avro version prior to v1.10.0.

## v0.16.0
- Add support for providing an explicit `namespace` on `extend`. 
- Default lookup to current namespace before falling back on global search. 

## v0.15.0
- Add support for declaring types as abstract.

## v0.14.1
- File handling fixes.

## v0.14.0
- Allow `filetype` to be specified in rake task to generate Avro JSON schema
  files.

## v0.13.0
- Add support for type macros.

## v0.12.0
- Allow methods for complex and primitive types to be used at the top-level and
  anywhere that a type name is accepted.

## v0.11.0
- Add support for generating schemas that contain logical types. The official
  Ruby `avro` gem does not yet support logical types. The `avro-salsify-fork` gem
  can be used to encode and decode logical types.
- Add support for `union`, `map`, and `array` methods to embed those types
  within other complex types.
- Add methods for primitives types (`string`, `int`, `long`, `float`, etc)
  that allow those types, including a logical type attribute, to be embedded
  within complex types.

## v0.10.0
- Include DSL file line numbers in stack traces.
- Add optional `filename` keyword argument to `Avro::Builder.build` and
  `.build_schema`. Filename can now be used instead of a DSL string to build
  schemas. When a filename is used, the file location of any error is included
  in the stack trace.

## v0.9.0
- Add rake task to generate Avro JSON schema files for all DSL files under a
  configurable root directory.
- Add Railtie to configure `#{Rails.root}/avro/dsl` as a load path, and define
  `avro:generate` rake task.

## v0.8.0
- Add `Avro::Builder::SchemaStore` to load DSL files and return schema objects.

## v0.7.0
- Only allow `type_name` and `type_namespace` options for naming named types
  defined inline.
- Only allow first argument to set name, and `namespace` option for top-level
  types.
- Only allow `aliases` attribute to set aliases for top-level types.

## v0.6.0
- Support recursive definitions.
- Coerce aliases to be represented as an array.
- Only allow name and namespace to be set via options, not via a block, for
  record, enum, and fixed types.
- Allow `doc` and `aliases` to be set on both a field and a type defined inline
  for the field. To set these attributes on the inline type `type_doc` and 
  `type_aliases` must be used in the DSL.

## v0.5.0
- Support references to named types that are defined inline.
- Raise an error for duplicate definitions with the same fullname.

## v0.4.0
- Add validation for required DSL attributes that are not specified.
- Allow name to be configured via a block for top-level record, enum, and fixed
  types.

## v0.3.2
- Fix a bug that allowed the partial matching of filenames.
- Fix a bug that prevented namespace from being specified as an option on
  records.
- Fix a bug that prevented loading references qualified by namespace.
- Do not attempt to import schema files for builtin types.

## v0.3.1
- A `null` default should automatically be added for optional fields to match
  the `:null` first member of the union.

## v0.3.0
- Add support for nested records. This includes the ability to reference a
  previously defined record as a type.

## v0.2.0
- Add support for `:union` type.
- Make `fixed` syntax more flexible. Both `fixed :f, 7` and `fixed :f, size: 7`
  are now supported and equivalent.

## v0.1.0
- Initial release
