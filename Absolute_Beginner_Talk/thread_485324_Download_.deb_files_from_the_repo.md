---
title: "Download .deb files from the repo"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by gustavocm on 2007-06-26
Is there a way to download the package files from the repository?

it's because i'll have to install the package in another pc that will be offline, but i can't find the .deb file on internet. The app is network-manager for amd64.

---

### Post by Gen2ly on 2007-06-26
Yeah, it's just an ftp, you can do it from your web browser there.

[ftp://ftp.ubuntu.com/ubuntu/dists/feisty](ftp://ftp.ubuntu.com/ubuntu/dists/feisty)

---

### Post by supersonicdarky on 2007-06-26
also through synaptic, you can tell it to download the package files only

---

### Post by gustavocm on 2007-06-26
thank you!

---

### Post by PriceChild on 2007-06-26
You might want to check out the package "aptoncd" which will let you make repository cds of content in your /var/cache/apt/archive

---

### Post by az on 2007-06-26
> **Dirk.R.Gently said:**
> Yeah, it's just an ftp, you can do it from your web browser there.

[ftp://ftp.ubuntu.com/ubuntu/dists/feisty](ftp://ftp.ubuntu.com/ubuntu/dists/feisty)

It's better to use the package manager since it will also fetch the dependencies.


sudo apt-get -d install *package*

---

