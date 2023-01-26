# Ansible Role - potos\_gnome\_shortcut

Role to install a Gnome extension which allows for shortcuts in top bar.

[![Test](https://github.com/projectpotos/ansible-role-potos_gnome_shortcut/actions/workflows/test.yml/badge.svg)](https://github.com/projectpotos/ansible-role-potos_gnome_shortcut/actions/workflows/test.yml)

## Example Playbook

As this role is tested via Molecule one can use [that
playbook](./molecule/default/converge.yml) as a starting point:

```yaml
---

- name: Converge
  hosts: all
  gather_facts: yes
  tasks:
    - name: run role
      ansible.builtin.include_role:
        name: 'ansible-role-potos_gnome_shortcut'
```

## Role Variables

The default variables are defined in [defaults/main.yml](./defaults/main.yml):

These values just define how the Gnome Extension is named on the system. Ensure this follows the Gnome requirements!
```yaml
potos_gnome_shortcuts_extention_uuid: "gnomeShortcuts@potos.dev"
potos_gnome_shortcuts_extention_name: "Potos Gnome Shortcuts"
potos_gnome_shortcuts_extention_description: "Provides Shortcut Menu for Potos"
```

This value defines the appearance in the top bar. For one the location, and the icon displayed.
```yaml
potos_gnome_shortcuts_position_index: 20
potos_gnome_shortcuts_position_place: "right"
potos_gnome_shortcuts_icon_file: "potos.svg"
```

This variable defines to which file the dconf enabeling of the gnome extenstion should be saved
```yaml
potos_gnome_shortcuts_dconf_file_location: "/etc/dconf/db/local.d/00-extensions"
```

This variable defines how the shortcut menu looks like.
```yml
potos_gnome_shortcuts_actions:
  - type: "command"
    text: "Hello World!"
    action:
      - "/bin/bash"
      - "-c"
      - "yad --title 'Hello World!' --text='Hello World!' --width=200 --timeout=5 --timeout-indicator=top"
  - type: "separator"
  - type: "command"
    text: "Goodbye"
    action:
      - "/bin/bash"
      - "-c"
      - "yad --title 'Goodbye!' --text='Goodbye!' --width=200 --timeout=5 --timeout-indicator=top"
```

Another option is to use `ansible-doc` to read the argument specification:

```sh
ansible-doc --type role -r . main ansible-role-potos_gnome_shortcut
```

## Requirements

N/A

## License

See [LICENSE](./LICENSE)

## Author Information

[Project Potos](https://github.com/projectpotos)
