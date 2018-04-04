# NSO Ansible MOPs

Ansible playbook to automate MOPs for network device upgrades.

## Requirements

- Ansible 2.6 or later
    - This playbook relies on Ansible modules for NSO available since Ansible 2.5 (nso_action and nso_config). However,
    there are important fixes to those modules which are only available in Ansible 2.6.
    - Before Ansible 2.6 is released, please use the dev branch (https://github.com/ansible/ansible)

- NSO health-snapshots package
    - The health-snapshots package is used for pre-post checks as well as verifying that the device is functional after
    a reload.
    - This package is available here: https://github.com/reismarcelo/device-health-snapshots

- Device to be upgraded
    - This playbook currently only supports XR devices.
    - The XR image tar file needs to be in the location specified by 'xr_package' variable.


## Configuration

Commonly used configuration parameters for the playbook are available in the group_vars/all.yml file.


## Running the playbook

    # ansible-playbook asr9k_upgrade.yaml

Service affecting tasks are tagged with 'service_impact'. The '--skip-tags' option can be used if one needs to run the
playbook without going through service affecting tasks:

    # ansible-playbook asr9k_upgrade.yaml --skip-tags=service_impact

