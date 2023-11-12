# Code snippets for Linode DX clients

## Terraform

```terraform
resource "linode_instance" "web" {
    label = "my-linode"
    image = "linode/ubuntu22.04"
    region = "us-central"
    type = "g6-standard-1"
    authorized_keys = ["ssh-rsa AAAA...Gw== user@example.local"]
    root_pass = "terr4form-test"

    group = "foo"
    tags = [ "foo" ]
    swap_size = 256
    private_ip = true
}
```

## Ansible

```yaml
- name: Create a new Linode instance.
  linode.cloud.instance:
    label: my-linode
    type: g6-nanode-1
    region: us-central
    image: linode/ubuntu22.04
    root_pass: this-is-a-p@ssword-and-its-very-long
    private_ip: true
    authorized_keys:
      - "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAINPMWRkxDy7UKyRVutujsq7rUpHE6VAtJ0nvar/58RNB"
    stackscript_id: 1337
    stackscript_data:
      var1: value1
    tags:
      - env=prod
    state: present
```

## Go SDK (linodego)

```go
linodeClient.CreateInstance(
    context.Background(),
    linodego.InstanceCreateOptions{
        Region: "us-central",
        Label: "my-linode",
        Type: "g6-nanode-1",
        RootPass: "this-is-very-looooooong-password",
    },
)
```


##  Python SDK (linode_api4-python)

```python
client = LinodeClient(token=os.getenv("LINODE_TOKEN"))
new_linode, root_pass = client.linode.instance_create(
    ltype="g6-nanode-1",
    region="us-central",
    image="linode/ubuntu22.04",
    label="my-linode"
)
```
