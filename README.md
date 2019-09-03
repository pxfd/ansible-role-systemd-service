# Simple role for management systemd services

This role can be used to create systemd service from given service definition.

```yaml
systemd_service:
  - service_name: freezer-api.service
    service_enabled: yes
    service_config:
        Unit:
            Description: freezer api
            Before:
            After: network.target
        Service:
            Type: simple
            User: '{{ freezer_user }}'
            WorkingDirectory: '{{ freezer_home }}'
            ExecStart: cmd
            Restart: always
        Install:
            WantedBy: multi-user.target
```