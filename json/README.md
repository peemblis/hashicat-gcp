
## Using the Terraform API

Run this command to fetch your token and store it as the TOKEN environment variable:

```
export TOKEN=$(grep token /root/.terraform.d/credentials.tfrc.json | cut -d '"' -f4)
```

Next set your ORG variable with the following command, replacing MYORGNAME with your own:

```
export ORG="MYORGNAME"
```

Finally, fetch your workspace id with the following curl command. Curl is a command line tool that is handy for interacting directly with APIs. Note how your TOKEN and ORG variables are automatically embedded in the command:

```
curl -s --header "Authorization: Bearer $TOKEN" --header "Content-Type: application/vnd.api+json"   https://app.terraform.io/api/v2/organizations/$ORG/workspaces/hashicat-gcp | jq -r .data.id
```

(Use Terraform API)[https://www.terraform.io/docs/cloud/api/run.html]

```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request POST \
  --data @apply.json \
  https://app.terraform.io/api/v2/runs
```
