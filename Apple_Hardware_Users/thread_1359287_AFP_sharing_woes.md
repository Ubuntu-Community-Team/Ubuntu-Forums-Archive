---
title: "AFP sharing woes"
date: 2009-12-19
forum: Apple Hardware Users
---

### Post by maxstahl on 2009-12-19
I recently switched my home server from Gentoo to Ubuntu. The way I had netatalk set up before, I had it so that any user had access to their home directory via AFP, and any user had access to /home/shared, which is a directory with movies and music shared between users. In the installation process I lost my /etc/netatalk/ files but here's my current /etc/netatalk/AppleVolumes.default:

```
~/			"$u" options:rw,nohex,usedots
/home/shared		"shared" options:rw,nohex,usedots
/var/www		"www" options:rw,nohex,usedots
```

Home directories and /var/www mount just fine, but they mount read-only and /home/shared won't mount at all. I get the following message if I use "connect to" in Finder:

> 'There was an error connecting to the server "beignet". Check the server name or IP address, and then try again.'

When I try from the finder sidebar, I get 'The operation cannot be completed because the original item for "shared" can't be found'. Any ideas? :confused:

---

### Post by scorp123 on 2009-12-20
Open this URL:

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Read it. But don't do anything yet. This was written with an older Ubuntu release in mind. Instead go down into the comment sections below and fast-forward to comments No. #501 + ff. where the correct methods on how to implement this on Ubuntu 9.10 (= current release) are being discussed. There are several tips and tricks posted there ... I guess that should help?

---

### Post by maxstahl on 2009-12-21
Kinda.... Good to know all the extra compiling from source isn't necessary anymore, but I'm still having the same problem after re-doing it. What are the requirements for a directory to be shared this way as far as permissions? The directory that's giving me the error has the same permissions as my home directory....

---

### Post by wesli_1 on 2010-03-31
Hey guys

I also had the error

```
The operation can't be completed because the original item for "[share name]" can't be found
```The solution for me was in post #480 of the article at [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

> cainscou: Turns out that Karmic uses a newer version of netatalk and it is incompatible with the hidden .AppleDB folder on the mounted folder on the Ubuntu box. Just sudo rm -rv .AppleDB to delete this folder in your timemachine folder, restart netatalk and away you go.This problem drove me mad for a few days because I thought it might be a problem with permissions or one of my config files.

Cheers
wesli_1

---

