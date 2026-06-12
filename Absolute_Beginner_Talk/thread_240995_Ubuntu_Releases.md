---
title: "Ubuntu Releases"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Icon41 on 2006-08-21
I got a couple questions on ubuntu releases.
Can you download a new release say edgy eft through the update manager or would I have to burn a iso and reinstall it.

and If I do have to burn the iso would I have to do a wipe of the drive or is there a upgrade feature in the live cd. thanks

---

### Post by tribaal on 2006-08-21
Pretty easy really: you don't need to burn a new CD at all.

To upgrade from a distribution version to another, just edit your "/etc/apt/sources.list" file, replacing the codename of your actual distro ("dapper" for example) to the new codename ("edgy") anywhere they appear in the file (usually in about 10 lines).

After that a simple "sudo apt-get update" and a "sudo apt-get dist-upgrade" will do the trick.

Upgrading this way might not be the recommendent way, though. The most fool-proof way is still to download the CD and burn it.

Worked perfecly for me from Hoary to Dapper, but... who knows? :)

- trib'

---

### Post by taurus on 2006-08-21
You can modify your /etc/apt/sources.list if you want to test out edgy.  Replace the dapper with edgy and run

```

sudo aptitude update
sudo aptitude dist-upgrade

```

---

### Post by ironfistchamp on 2006-08-21
Ok to get edgy right now you would need to go to you sources list (/etc/apt/sources.list), edit it as root and change all references to dapper (or whatever codename your version is) to edgy. Then type in a terminal

```


sudo apt-get update
sudo apt-get dist-upgrade

```

This is not recommended though as this will changes your dapper install (or whatever version you have) to the current version of edgy which is by no means stable. If you did this I don't think you would be able to go back to dapper or whatever you use.

There is currently no Edgy iso to my knowledge.

Hope this helps

Ironfistchamp

EDIT: Dammnit two ppl beat me to it  :p

---

