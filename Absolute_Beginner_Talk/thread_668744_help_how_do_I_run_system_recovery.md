---
title: "help how do I run system recovery"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-15
I tried to upgrade but my virtual pation took to long and my runscrape driver moron brother stoped it in the middle of an upgrade it says internal system error failed to inisalize HAL gnome isn't working thank the lord I installed xfce the day before helllp

---

### Post by marmaladeskies on 2008-01-15
> Try this:

Boot up a live cd

Open a terminal - Applications > Accessories > Terminal

Mount the location of your hard drive version somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc.)

If you're unsure of the drive name type:

Code:

sudo fdisk -l

Code:

      sudo mkdir /media/hd
      sudo mount /dev/**** /media/hd

chroot into your hd drive

Code:

      sudo chroot /media/hd su

Update your system via apt as normal (sudo not required)

Code:

      apt-get update
      apt-get install ubuntu-desktop

Ctrl+d or type "exit" to exit the chroot, then reboot the computer.

This is how bollix47 solved a similar problem of mine.  All credit goes to him.  Hope this helps.

---

