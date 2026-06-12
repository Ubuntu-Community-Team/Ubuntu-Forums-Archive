---
title: "Dapper has Disks Manager??? What does it do?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Unterseeboot_234 on 2007-02-02
Drake comes packaged with (from the top bar menu) --> System --> Administration --> Disks. Click on that, the Administrator Password dialog box comes up to give in your password, the program fires up, and the Gnome Title Bar at the top of the resulting window says **Disks Manager**. 

WHAT does that software do????? Every time I've ever tried it, the "time out" cursor spins and spins and spins and spins whenever the mouse pointer is over the Disks Manager window. No help menu. Nothing to search for because the program name is "Disks" "Manager" and that brings up too many hits.

Should I just delete the program? Is it good for anything?

---

### Post by steve.horsley on 2007-02-02
There's something wrong with it then. What it does is to let you choose the mount points of the disk partitions, and whether they're mounted at boot. It's a very simple GUI for editing /etc/fstab. It's not included in Edgy.

---

### Post by Unterseeboot_234 on 2007-02-02
Hmmm, thanks. Makes sense. I seem to remember it did work at first. I've reinstalled too many times with partitions making up partitions. Last crash was I tried to install XP 64-bit on top of a stable ubuntu Drake. Mind you, XP install is all or nothing. I thought I was fine. This was a sealed CD that has been laying around because no one at our organization had 64-bit hardware. When I tried to put in the key number for XP, that's when the install wouldn't proceed. MS says maybe my disc is defective. MBR is totally locked. GRUB or nobody won't let me have my ubuntu install back. If I do XP again, it goes on first and then I know ubuntu won't have any problems.

Thanks, I'll look for anything that will fstab and find my mounts. Right now, I just finished getting Drake back to where I want it. Mostly, some java code I lost.

---

### Post by steve.horsley on 2007-02-03
To replace GRUB, you can boot the "alternate" installer, go into rescue mode, choose to open a prompt on your install partition, and enter the command **grub-install /dev/hda**, I seem to remember. 

Here is a useful looking page:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

