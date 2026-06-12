---
title: "[SOLVED] Mbr"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by scrimple101 on 2008-04-13
I have Ubuntu 7.10  and Windows XP installed on a partitioned disk. i decided to install Mandriva and split the Ubuntu partition. This worked well but now when i boot it comes up with the mandriva splash screen with only windows and mandriva options for boot. I want the Ubuntu option as well and i aslo wanted the ubuntu grub splash sceen. What do i need to do? do i have to edit the Master Boot Record? If so what is the Ubuntu entry the i need to type in? best regards, Rob

---

### Post by Oldsoldier2003 on 2008-04-13
> **scrimple101 said:**
> I have Ubuntu 7.10  and Windows XP installed on a partitioned disk. i decided to install Mandriva and split the Ubuntu partition. This worked well but now when i boot it comes up with the mandriva splash screen with only windows and mandriva options for boot. I want the Ubuntu option as well and i aslo wanted the ubuntu grub splash sceen. What do i need to do? do i have to edit the Master Boot Record? If so what is the Ubuntu entry the i need to type in? best regards, Rob
What you will need to do is edit the grub menu. here is a good tutorial on multibooting.
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by scrimple101 on 2008-04-13
thanks for your reply but i was after the Ubuntu 7.10 entry for the master boot record. I think if i edit the MBR it will be the easiest and quickest way of being able to boot Ubuntu also. Regards, Rob.

---

### Post by Oldsoldier2003 on 2008-04-13
> **scrimple101 said:**
> thanks for your reply but i was after the Ubuntu 7.10 entry for the master boot record. I think if i edit the MBR it will be the easiest and quickest way of being able to boot Ubuntu also. Regards, Rob.
you wont be editing the MBR. what you need to do is copy the data from /boot/grub/menu.lst of the Ubuntu partition and insert it in the /boot/grub/menu.lst of the mandriva partition or chain load.

When you installed Mandriva it installed grub and activated it on your Mandriva partition.

---

### Post by Jason2gs on 2008-04-13
This might help you:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dcstar on 2008-04-13
> **Oldsoldier2003 said:**
> you wont be editing the MBR. what you need to do is copy the data from /boot/grub/menu.lst of the Ubuntu partition and insert it in the /boot/grub/menu.lst of the mandriva partition or chain load.


Or re-install Grub on the Ubuntu partition and copy the Mandriva info to that (if the Mandriva may someday be removed).

I find it a lot simpler to install VMware server and then install all these other OSs as VMs - no more multi-booting the base OS.

---

### Post by scrimple101 on 2008-04-13
Thanks David, how do you install grub to the ubuntu partition?\
regards, Rob

---

### Post by scrimple101 on 2008-04-13
Hello, thanks to everyone who replied to this thread. I found what i was tryinh to do in this thread on the Mandriva forum. 
[http://mandrivausers.org/lofiversion/index.php/t42743.html](http://mandrivausers.org/lofiversion/index.php/t42743.html)

Basically it's editing the boot/grub/menu.1st file so that ubuntu sows on the boot screen. 
regards, Rob

---

