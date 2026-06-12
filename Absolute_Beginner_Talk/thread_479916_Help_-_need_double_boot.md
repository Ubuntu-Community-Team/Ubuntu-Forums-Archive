---
title: "Help - need double boot"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Kuriozu on 2007-06-20
I installed Ubuntu and didn't do dual partition for Windows. Now I want to have dual boot and don't know how.  Someone please help.

---

### Post by Sushubh on 2007-06-20
gparted and [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) could be of some help?

---

### Post by amazingtaters on 2007-06-20
What I would do is delete the Ubuntu data off my HDD, and reinstall Ubuntu using the partitioner in the Ubuntu installer to create the partitions for ubuntu (don't forget the swap partition). Also, defrag windows at least once, really twice is better, before you go ahead with this.

---

### Post by Kuriozu on 2007-06-20
> **Sushubh said:**
> gparted and [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) could be of some help?



Thanks for your response

Is there a way to uninstall Ubuntu altogether and start over?

---

### Post by JebusWankel on 2007-06-20
Surely, just reformat the whole drive and install Windows. Knowing you'll have an Ubuntu dual boot, you may want to format the whole drive in FAT32 for Windows but NTFS may be fine to. FAT32 is more easily accessed by Linux but NTFS is otherwise better.

---

### Post by Kuriozu on 2007-06-20
> **JebusWankel said:**
> Surely, just reformat the whole drive and install Windows. Knowing you'll have an Ubuntu dual boot, you may want to format the whole drive in FAT32 for Windows but NTFS may be fine to. FAT32 is more easily accessed by Linux but NTFS is otherwise better.

I actually thought about doing that and I tried but my computer doesnt have floppy drive so I cant use a booting disk. I do have the windows xp cd but couldn't figure out how to reformat the HD.

Right now I only have ubuntu installed.

Thanks again

---

### Post by JebusWankel on 2007-06-20
If you want to repartition the drive from within Ubuntu just install gparted. I find it incredibly easy to use. You can install it by typing "sudo apt-get install gparted" in the terminal.

---

### Post by Sushubh on 2007-06-20
u can use the linux live CD or the Windows CD to format a disc i am sure. :)

---

### Post by Kuriozu on 2007-06-20
> **Sushubh said:**
> u can use the linux live CD or the Windows CD to format a disc i am sure. :)

Thanks to all of you, I'm going to try these sugestions.

---

### Post by Kuriozu on 2007-06-21
Hi guys,
How do I format using the live cd?

---

### Post by Kuriozu on 2007-06-21
I need help unistalling ubuntu using the live cd

---

