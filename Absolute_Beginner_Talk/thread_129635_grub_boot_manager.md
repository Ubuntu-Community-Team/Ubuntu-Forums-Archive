---
title: "grub boot manager"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-02-14
Hello, I have the following situation.
I was using a Windows XP PC, and put in a new hdd, on which i installed ubuntu. Somewhere in the installation ubuntu asked, whether it should install the grub boot manager, so that i can select the operating system. This all works fine, but since i don't have a network on this computer, ubuntu cannot download the programs i need, and it doesn't make any sense to use ubuntu. Thus i wanted to uninstall ubuntu. But i don'T know how to do this. A bigger problem is, that i can't manipulate grub because i cannot locate it. it must be somewhere on the windows harddisc drive, but i don't have a clue, where. On the other hand,  if i remove the ubuntu harddisc physically, grub won't start, so it must be also on this hdd. The windows hdd is labelled master, but i cannot find the masterboot record, and fdisk/fdisc does not work.
Now the question is, how can i change grub such, that it automatically starts windows, and how can i uninstall it.

Thank you

---

### Post by Harleen on 2006-02-14
Grub is installed in the master boot record of your first hard disc, where probably Windows is located. To remove grub (or rather replace it by the Windows bootloader) run "fdisk /mbr" in Windows.
If that worked, you can remove the Linux partition using the Windows tools. Don't do that before you have removed grub from the MBR, because as you already pointed out grub reads its configuration from the Linux partition (it's located in /boot).

---

### Post by ajgreeny on 2006-02-14
just out of interest, how can you get onto the internet with what I assume is the windows OS of the computer but not with ubuntu.  If one works the other should also.  Ubuntu is great for more than surfing, however, so I'm surprised you say it is not worth using ubuntu at all!

---

### Post by gagatz on 2006-02-15
The Windows ubuntu computer is not connected to the internet. This is written from another computer (fedora core)

---

### Post by cotcot on 2006-02-15
Have you checked in ubuntu if your network card is activated ? (>system>administration>network)

It should be possible to have internet connection with XP on hhd 1 and ubuntu on hhd2. I have on my PC2 internet connection from Ubuntu 5.10 (breezy) , Kubuntu 5.10 (breezy) and Ubuntu 6.04 (Dapper)

---

