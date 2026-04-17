# Upgrading Notes

This document captures required refactoring on your part when upgrading to a module version that contains breaking changes.

## Upgrading to v3.0.0

### Key Changes v3.0.0

This module now requires a minimum AWS provider version of 6.0 to support the region parameter. If you are using multiple AWS provider blocks, please read [migrating from multiple provider configurations](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/guides/enhanced-region-support#migrating-from-multiple-provider-configurations).


## Upgrading to v2.0.0

### Key Changes

- Drop support for `var.name`. Changing a security group’s `name` in Terraform forces its replacement, which can cause deployment failures due to dependencies with other AWS resources. Since AWS does not allow deleting a security group that is still associated with another resource. Using `name_prefix` avoids unnecessary recreation, and `create_before_destroy` ensures smooth updates without disruption.

#### Variables

The following variables have been removed:

- `name`

## Upgrading to v1.0.0

### Key Changes

- Introduced support for multiple CIDR blocks in both ingress and egress rules.
- The `cidr_ipv4` and `cidr_ipv6` attributes have been updated from `string` to `list(string)` , allowing multiple CIDR blocks to be specified within `egress_rules` and `ingress_rules`.

#### Variables

The following variables have been modified:

- `egress_rules`:
    - `cidr_ipv4` attribute has changed from `string` to `list(string)`
    - `cidr_ipv6` attribute has changed from `string` to `list(string)`
    
- `ingress_rules`:
    - `cidr_ipv4` attribute has changed from `string` to `list(string)`
    - `cidr_ipv6` attribute has changed from `string` to `list(string)`

Ensure that your configurations are updated accordingly before applying changes. 🚀
