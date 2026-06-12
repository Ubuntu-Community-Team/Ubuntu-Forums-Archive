---
title: "dist-upgrade questions"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by BKK on 2006-11-04
Hi, I am not sure whether to continue in this situation. I ran the dist-upgrade in console because I got an error "could not calculate upgrade" when I was asked to do a dist-upgrade graphically. So by the looks of this it wants to remove my video drivers? I don't know why...I am using the nvidia beta drivers. I am also running beryl. 
Are the packages that it wants to instal going to contain some new replacement for the video drivers?

Thanks

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-glx
The following packages will be upgraded:
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common
2 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 7702kB of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

### Post by MasterOfDisaster on 2006-11-05
I ended up with this option too...  I chose not to upgrade, as it would be a pain to install the nvidia driver again...  Anyways, everything is still working fine.

---

### Post by xyz on 2006-11-05
As seen in various places on the net
> If you want to upgrade using GUI use the following command

```
gksu “update-manager -c ”
```

“-c” switch tells it to look for upgrades at all.You should see the following screen here Now you can see 6.10 is available for upgrade click on upgrade

Has either of you tried doing it this way?

---

