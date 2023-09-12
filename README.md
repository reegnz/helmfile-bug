# Helmfile softlinks bug

## Problem

This works:

```sh
cd ./services/echo-server/
helmfile template
```

This doesn't:

```sh
cd ./accounts/my_aws_account/clusters/my_cluster/services/echo-server/
helmfile template
```

## Solution

The helmfile binary should first resolve the absolute path of PWD before resolving relative paths inside the helmfile.yaml

Tools like direnv for example behave correctly with softlinks:

https://github.com/direnv/direnv/blob/master/stdlib.sh#L193-L206
