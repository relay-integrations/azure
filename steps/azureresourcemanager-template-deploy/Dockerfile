FROM relaysh/core:latest-python

# Override Tekton specified home dir
ENV HOME=/root
ENV PATH="/root/.local/bin:${PATH}"

# Install Azure dependencies
RUN apk add --no-cache gcc musl-dev python3-dev libffi-dev openssl-dev cargo make icu

# Install Azure CLI and libs
RUN pip --no-cache-dir install \
  azure-cli \
  azure-common \
  azure-mgmt-compute \
  azure-mgmt-network \
  azure-mgmt-resource \
  azure-mgmt-resourcegraph \
  azure-mgmt-storage \
  azure.identity \
  azure.storage.queue \
  msrestazure

ADD ./step.sh /nebula/step-azureresourcemanager-deployer.sh
ENTRYPOINT []
CMD ["/bin/bash", "/nebula/step-azureresourcemanager-deployer.sh"]

LABEL "org.opencontainers.image.title"="ARM / Bicep deployer"
LABEL "org.opencontainers.image.description"="A task that deploys (creates or updates) an ARM / Bicep deployment using a provided template."
LABEL "com.puppet.nebula.sdk.version"="v1"
