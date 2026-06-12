---
title: "Rollback an alsa sound update?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by broisaac on 2008-03-06
I recently ran a bunch of updates when i logged into my ubuntu 7.10 gutsy system, including some for the alsa drivers i am using. No more sound. 
Is it possible to rollback the drivers? I can see the updates in the var/log/dpkg.log , but i'm not sure how to remove them without screwing up and having to reinstall the whole OS - i've done that before.
Any ideas would be appreciated...

Toshiba A105 - S2001 w/ ATI SB450 HDA Audio

---

### Post by kuja on 2008-03-06
If you know which packages were upgraded (probably linux-sound-base, alsa-base, alsa-utils, and/or libasound2 related), you could download the version from the gutsy release here: [http://archive.ubuntu.com/ubuntu/pool/main/a/](http://archive.ubuntu.com/ubuntu/pool/main/a/) (probably the alsa-driver folder), the modified date should be sometime in october (or close to) of 2007. (seeing as multiple versions of the packages will be there). After downloading them, open a terminal (ie: gnome-terminal, xterm, konsole, etc), and enter the following command: ```
sudo dpkg -i --force-downgrade *.deb
```

Afterwards, reboot.

---

