---
title: "Preseed blues"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by paul.clayton on 2007-05-04
Hi there. My first post, and only becasue I am totally desperate.

I am trying to set up an automted install of 7.04 server using preseed, and cannot get passed two areas.

Namely

1) Always get requested to detect my keyboard regardless of whether I have set it up in the preseed or not.

2) Always get asked to do Guided install of my hard disk.

I don't have this nonsense with kickstart.

Any ideas. I can post my cfg file later if required.

ciao

---

### Post by paljas on 2007-05-07
I am also struggling with your step 2. Problem one, I solved with:

LABEL staff
kernel ubuntu-installer/i386/linux
append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw debian-installer/locale=en_US console-setup/layoutcode=us netcfg/get_hostname=unassigned-hostname preseed/url=http://etc.etc. --

(assuming you also use pxe booting)

---

### Post by rizza on 2007-05-13
All your problems have been answer in my previous post on the same problems. Just search for preseed and you should see my post for preseed problems. I've corrected these issues and now can to fully automatic install without any interaction except hostname by choice. Good luck.

---

