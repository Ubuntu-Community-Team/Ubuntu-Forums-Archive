---
title: "Single boot, leave the EFI partition for a faster one."
date: 2008-03-05
forum: Apple Intel Users
---

### Post by Tasu on 2008-03-05
Hi, some days ago I formatted my old MacBook White to turn it into a DAW using Ubuntu Gutsy and the packages from the Studio Version, having installed Ubuntu on some other MacBooks as th eonly one system, I noted, like a lot  of people here in the forum, that the boot time, in the pre grub phase, is reall long, about one minute, during the last installation, I thought not to erase the entire disk, but manually partitioned by myself, leaving the EFI partition you can see in place, the installation went smooth as always, and after the reboot I found that the Macbook wasn't waiting that minute before booting grub, it started linux in few seconds, just like booting Mac OS X, the white/grey screen shows for just one second a folder icon with a ? in it, and then grub starts from the Stage 2 and not the usual Stage 1.5...
In fstab the EFI partition is:

UUID=2860-11F4  /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1

Just to let you know...

Bye! ^_^

---

