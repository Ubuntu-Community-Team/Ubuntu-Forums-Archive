---
title: "/dev/sda3 missing"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Naruto on 2006-03-22
When  i try to boot it gives me an error saying that /dev/sda3 (my Linux partition) )is missing and get's me in console. Then  when I get into /dev/ and type "ls" it says NULL. I have no patrtitions in /dev/. HeLp.

---

### Post by taurus on 2006-03-22
At the GRUB screen, try to boot it into single user mode (or recovery mode).  Then, have a look at your /etc/fstab to make sure an entry for your / is correct!  By the way, do you have a SATA harddrive and what is the output of this command?
```

fdisk -l /dev/sda

```

---

### Post by Naruto on 2006-03-22
Yes I have tried recovery mode and it give's the same error :
> ALERT! /dev/sda3 does not exist dropping to shell!

The shell itself goes like:
> /bin/sh: can't access tty ; job control turned off

I don't know much about shells but obviously the one I am droped in won't do any good.
There is no fdisk in /sbin. Actually there are lot's of directories and files missing so I figured it is some kind of virtual shell. I booted Gentoo live cd and tried fdisk.
It said that /dev/sda3 can not be opened. (don't know if this is related to my current problem or it was bacause of Gentoo)

All started when I upgraded to dapper through apt-get. All went well until i restarted the computer, then it started the above "complaining".
And the sda3 partition is perfectly fine. I am using explore2fs.exe in windows to have access to it's files. Everything is in order.

Any insights?

---

### Post by A-star on 2006-12-21
Same problem here, a while ago I installed an update for ubuntu and on first boot it doesn't detect my sda disk.
When i reboot it detects it just fine and starts up without a problem.

does anyone has a clue?

---

### Post by macogw on 2006-12-21
Distro upgrades rewrite your /boot/grub/menu.lst .  I had an updated kernel and started getting "no OS found" errors because for *some reason* my computer sees hd0 as what Grub calls hd1 and hd1 as what Grub calls hd0.  That means Ubuntu edits my Grub to point at the wrong hard drive for all the boot options.  When I upgraded Dapper > Edgy I sat there watching the terminal and right after it said it changed Grub, I editted it to change everywhere that it put hd1 to say hd0 so it'd be able to boot.

---

### Post by A-star on 2006-12-21
It's not a complete ugrade that it did, it just upgraded some packages.

Oh well, time to reinstall and install edgy.

---

