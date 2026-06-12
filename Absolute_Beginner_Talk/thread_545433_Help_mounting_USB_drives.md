---
title: "Help mounting USB drives"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by praneeth on 2007-09-07
Hi,

I have installed edubuntu server and configured the thin clients successfully and working fine..

When i connect the USB Device on my thin clients and server the drive do not mount and also it do not recognize the device.


how can i fix this problem..

Thanks,
Praneeth.

---

### Post by vanadium on 2007-09-07
I have no experience with servers a nd thin clients, but on a regular Ubuntu/Edubuntu/Kubuntu/Xubuntu install, USB drives are mounted automatically and appear on the desktop.

Try this first: System - Preferences - Removable Drives and Media, Storage tab: make sure "Mount removable drives ..." and "Mount removable media when inserted" are checked.

If that was not the issue, then I can only suggest for now the following diagnostic. Run

sudo fdisk -l

to check wether or not the USB is "recognised". It could be recognized, but not mounted. The command

mount

lists all that is mounted. You might want to post the output of both commands here so we can comment on it.

---

### Post by praneeth on 2007-09-10
Hi 

Thanks,

I have done what you have suggested and it worked however

I have configured the Server and it worked well 


I have 3 ThinClients and I can access usd drives only on my third client but the rest 1&2 i cannot access the external drives.

I have given the permission to access the external drives.

How can i solve this problem.


Thanks,
Praneeth

---

