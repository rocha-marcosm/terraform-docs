---
subcategory: "OpsWorks"
layout: "aws"
page_title: "AWS: aws_opsworks_rails_app_layer"
description: |-
  Provides an OpsWorks Ruby on Rails application layer resource.
---

# Resource: aws_opsworks_rails_app_layer

Provides an OpsWorks Ruby on Rails application layer resource.

!> **ALERT:** AWS no longer supports OpsWorks Stacks. All related resources will be removed from the Terraform AWS Provider in the next major version.

## Example Usage

```terraform
resource "aws_opsworks_rails_app_layer" "app" {
  stack_id = aws_opsworks_stack.main.id
}
```

## Argument Reference

This resource supports the following arguments:

* `stack_id` - (Required) ID of the stack the layer will belong to.
* `name` - (Optional) A human-readable name for the layer.
* `app_server` - (Optional) Keyword for the app server to use. Defaults to "apache_passenger".
* `auto_assign_elastic_ips` - (Optional) Whether to automatically assign an elastic IP address to the layer's instances.
* `auto_assign_public_ips` - (Optional) For stacks belonging to a VPC, whether to automatically assign a public IP address to each of the layer's instances.
* `bundler_version` - (Optional) When OpsWorks is managing Bundler, which version to use. Defaults to "1.5.3".
* `custom_instance_profile_arn` - (Optional) The ARN of an IAM profile that will be used for the layer's instances.
* `custom_security_group_ids` - (Optional) Ids for a set of security groups to apply to the layer's instances.
* `auto_healing` - (Optional) Whether to enable auto-healing for the layer.
* `install_updates_on_boot` - (Optional) Whether to install OS and package updates on each instance when it boots.
* `instance_shutdown_timeout` - (Optional) The time, in seconds, that OpsWorks will wait for Chef to complete after triggering the Shutdown event.
* `elastic_load_balancer` - (Optional) Name of an Elastic Load Balancer to attach to this layer
* `drain_elb_on_shutdown` - (Optional) Whether to enable Elastic Load Balancing connection draining.
* `manage_bundler` - (Optional) Whether OpsWorks should manage bundler. On by default.
* `passenger_version` - (Optional) The version of Passenger to use. Defaults to "4.0.46".
* `ruby_version` - (Optional) The version of Ruby to use. Defaults to "2.0.0".
* `rubygems_version` - (Optional) The version of RubyGems to use. Defaults to "2.2.2".
* `system_packages` - (Optional) Names of a set of system packages to install on the layer's instances.
* `use_ebs_optimized_instances` - (Optional) Whether to use EBS-optimized instances.
* `ebs_volume` - (Optional) `ebs_volume` blocks, as described below, will each create an EBS volume and connect it to the layer's instances.
* `custom_json` - (Optional) Custom JSON attributes to apply to the layer.
* `tags` - (Optional) A map of tags to assign to the resource. If configured with a provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block) present, tags with matching keys will overwrite those defined at the provider-level.

The following extra optional arguments, all lists of Chef recipe names, allow
custom Chef recipes to be applied to layer instances at the five different
lifecycle events, if custom cookbooks are enabled on the layer's stack:

* `custom_configure_recipes`
* `custom_deploy_recipes`
* `custom_setup_recipes`
* `custom_shutdown_recipes`
* `custom_undeploy_recipes`

An `ebs_volume` block supports the following arguments:

* `mount_point` - (Required) The path to mount the EBS volume on the layer's instances.
* `size` - (Required) The size of the volume in gigabytes.
* `number_of_disks` - (Required) The number of disks to use for the EBS volume.
* `raid_level` - (Required) The RAID level to use for the volume.
* `type` - (Optional) The type of volume to create. This may be `standard` (the default), `io1` or `gp2`.
* `iops` - (Optional) For PIOPS volumes, the IOPS per disk.

## Attribute Reference

This resource exports the following attributes in addition to the arguments above:

* `id` - The id of the layer.
* `arn` - The Amazon Resource Name(ARN) of the layer.
* `tags_all` - A map of tags assigned to the resource, including those inherited from the provider [`default_tags` configuration block](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#default_tags-configuration-block).
