# Terraform Provider Scaffolding (Terraform Plugin Framework)

_This template repository is built on the [Terraform Plugin Framework](https://github.com/hashicorp/terraform-plugin-framework). The template repository built on the [Terraform Plugin SDK](https://github.com/hashicorp/terraform-plugin-sdk) can be found at [terraform-provider-scaffolding](https://github.com/hashicorp/terraform-provider-scaffolding). See [Which SDK Should I Use?](https://developer.hashicorp.com/terraform/plugin/framework-benefits) in the Terraform documentation for additional information._

This repository is a *template* for a [Terraform](https://www.terraform.io) provider. It is intended as a starting point for creating Terraform providers, containing:

- A resource and a data source (`internal/provider/`),
- Examples (`examples/`) and generated documentation (`docs/`),
- Miscellaneous meta files.

These files contain boilerplate code that you will need to edit to create your own Terraform provider. Tutorials for creating Terraform providers can be found on the [HashiCorp Developer](https://developer.hashicorp.com/terraform/tutorials/providers-plugin-framework) platform. _Terraform Plugin Framework specific guides are titled accordingly._

Please see the [GitHub template repository documentation](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) for how to create a new repository from this template on GitHub.

Once you've written your provider, you'll want to [publish it on the Terraform Registry](https://developer.hashicorp.com/terraform/registry/providers/publishing) so that others can use it.

## Requirements

- [Terraform](https://developer.hashicorp.com/terraform/downloads) >= 1.0
- [Go](https://golang.org/doc/install) >= 1.20

## Building The Provider

1. Clone the repository
1. Enter the repository directory
1. Build the provider using the Go `install` command:

```shell
go install
```

## Adding Dependencies

This provider uses [Go modules](https://github.com/golang/go/wiki/Modules).
Please see the Go documentation for the most up to date information about using Go modules.

To add a new dependency `github.com/author/dependency` to your Terraform provider:

```shell
go get github.com/author/dependency
go mod tidy
```

Then commit the changes to `go.mod` and `go.sum`.

## Using the provider

Fill this in for each provider

## Developing the Provider

Just enter a development shell with `nix develop` which will provide `go`, `terraform`, and is the same environment that should be used in production to build the provider.

If you wish to use `zsh` as the shell, `nix develop --command zsh`.

### Compiling
`nix build` will put a binary into `./result/bin`

### Local use
To use the provider locally, move/merge the `./.terraformrc` file provided into `~/.terrformrc`

### Documentation
<!-- TODO: this should be a pre-commit hook -->
To generate or update documentation, run `go generate`.

### Testing
In order to run the full suite of Acceptance tests, run `make testacc`.
Testing should also happen on build, I think.

### Release

Releases go through automatic builds, linting, and testing of the code. For some reason, your linter (mine) may not work s in remote. Use this command to get lint errors:

```sh
docker run -t --rm -v $(pwd):/app -w /app golangci/golangci-lint:v1.55.2 golangci-lint run -v
```

*Note:* Acceptance tests create real resources, and often cost money to run.

```shell
make testacc
```
