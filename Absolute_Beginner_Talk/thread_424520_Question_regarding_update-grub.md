---
title: "Question regarding update-grub"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Drewski on 2007-04-26
The computer on which I installed Ubuntu has two 20-gig hard drives. Both of these hard drives had an installation of Linux each, so when I initially installed Ubuntu, I wiped the primary hard drive (hda) and installed Ubuntu there. After, I would get a bootup screen listing 6 options: 3 options for booting the Linux partition I just installed, and 3 for booting the Linux partition on the other hard drive (hdb).

So after I got Ubuntu installed and set up, I formatted and partitioned the second hard drive, and mounted it (all successfully.)

I heard about a program called update-grub, so I ran it (with sudo of course) expecting that it will scan my hard drives and update /boot/grub/menu.lst accordingly. It ran successfully, but for some reason still seemed to think there was a Linux partition on hdb1, even though it was empty, except for /lost+found and a directory I created, /data.
Of course to rectify the problem I just manually edited menu.lst and removed the invalid entry. Is this behaviour typical of update-grub? Shouldn't it have realized that hdb1 doesn't have a Linux partition on it?

---

### Post by speeddemon8803 on 2007-04-26
im not a bona fide expert..but i think it saw linux folders and thought hey woot theres a linux partition....might i ask what kind of file system they use?

---

### Post by Drewski on 2007-04-26
It's using ext3.
Thing is though, the menu.lst file would have to be edited in such a way as to point to the kernel file, vmlinuz-whatever.
Since that doesn't exist on hdb, that obviously means Linux doesn't exist either, right? :P

---

### Post by az on 2007-04-26
> **Drewski said:**
>  Shouldn't it have realized that hdb1 doesn't have a Linux partition on it?

No.  Update grub just adusts the /boot/grub/menu.lst file.  All the options lines are commented out and the update-grub script takes the setting from those lines and adds them to the appropriate stanzas.  The menu.list is seeded by the installer.   One of the installer scripts scans your other drives.

You need to edit the menu.lst file by hand.

---

