# Docker Image Watch
Simple script to watch an image on Docker Hub. If the digest changes an
email is triggered to notify about the new image.

This is a minimal bash script. It could be extended with authentication
or to take action other than sending an email. However, this state is
the bare minimum currently needed. Pull requests welcome, feature requests
will go unanswered on this one.

## Usage
Setup a cron job or systemd timer to periodically call the script. The
environment variables DOCKER_REPOSITORY, DOCKER_IMAGE, and DOCKER_IMAGE_TAG
can be used to configure the image to watch (defaults to drupal:latest).
In DOCKER_IW_RECIPIENT you can configure the email recipient (defaults
to root). Note that your sendmail console tool must be configured properly
to be able to send emails.

The script stores the last know digest in a stamp file. It can be set using
the STAMP_FILE environment variable.

## Image Diff
The script can send a list of differences between the old and the new image
using [container-diff](https://github.com/GoogleCloudPlatform/container-diff).
In order for this to work, install container-diff on your machine and set
ENABLE_DIFF to a non-empty value.
