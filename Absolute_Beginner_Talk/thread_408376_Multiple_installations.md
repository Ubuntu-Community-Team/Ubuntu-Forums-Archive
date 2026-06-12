---
title: "Multiple installations"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2007-04-13
Newbie here, so be gentle!

I recently installed 6.10 on a dual boot Fujitsu Amilo laptop (Win XP), which worked perfectly fine for a couple of days. Then I must have triggered something (I suspect downloading Gparted .iso live CD had something to do with it) and now at the boot window stage I have three(?) installations of Ubuntu and one XP in the following order:-
2 ubuntu
then under other OS:-
Windows
Ubuntu

Clearly this is not what is required/efficient and I would like to delete two duplicate installations (retaining XP and one Ubuntu), if for no other reason that Xsane will not now recognise my HP psc. Is there a way of identifying where the extra UB installations reside on my hard drive then safely deleting them without destroying XP? Any guidance gratefully received.

---

### Post by Inxsible on 2007-04-13
> **Hookheathen said:**
> Newbie here, so be gentle!

I recently installed 6.10 on a dual boot Fujitsu Amilo laptop (Win XP), which worked perfectly fine for a couple of days. Then I must have triggered something (I suspect downloading Gparted .iso live CD had something to do with it) and now at the boot window stage I have three(?) installations of Ubuntu and one XP in the following order:-
2 ubuntu
then under other OS:-
Windows
Ubuntu

Clearly this is not what is required/efficient and I would like to delete two duplicate installations (retaining XP and one Ubuntu), if for no other reason that Xsane will not now recognise my HP psc. Is there a way of identifying where the extra UB installations reside on my hard drive then safely deleting them without destroying XP? Any guidance gratefully received.

Does any one of the Ubuntu say [recovery mode]
That is same as Windows safe mode

---

### Post by Hookheathen on 2007-04-13
Yes, all three installations have recovery mode options in the boot list. What then?

---

### Post by zvacet on 2007-04-13
If I understand you it is about 3 versions of kernel.You can keep highest version and delete other with synaptic.Look for linux image and as I sed keep highest.

---

### Post by Hookheathen on 2007-04-13
Many thanks, using Synaptic I have removed one duplicate, however another - which is listed under other OS along with XP, remains. It is the same lower version as the one successfully removed. So how do I go about deleting that one?

---

### Post by indytim on 2007-04-13
Typically when you go through a kernel update, your grub boot menu is updated to include the new version of the kernel (along with the old versions).  To answer your question directly, edit /boot/grub/menu.lst and comment out the options that you do not want.  Of course, make a copy of the file before you edit it.

I'm on kde (Kubuntu) but I believe the protocol for Ubuntu is

```

$ cd /boot/grub
$ sudo cp menu.lst menu.lst-bu
$sudo gedit menu.lst

```

Hope this helps,

IndyTim

---

### Post by Hookheathen on 2007-04-16
Thank you IndyTim, cleaned up the dupes.
Now to get my printer/scanner to be recognised. Although it was working fine before I had the duplicated boots.

---

