---
title: "Repo's"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-10-17
Hey.. Been seeing this errormsg after running "sudo apt-get update"

Fetched 9646B in 1s (7149B/s)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems

Bad link in repo?
Should I change repo? This has been working since update from Breezy.. I'm using this repo:

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Appreciate any help..

---

### Post by skymt on 2006-10-17
That GPG error is basically harmless. Did you run these commands (from the guide you linked to)?```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
sudo apt-get update
```

---

### Post by deadgobby on 2006-10-17
read this link
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

---

