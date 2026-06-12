---
title: "How do you use a live CD to edit a confg file (menu.lst)"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by louieb on 2006-07-13
I can't tell you how many time I have reinstalled Ubuntu just to fix my menu.lst file. The PC I'm using has two 30 gig hard drives. Windows XP is on hdb. On hda I have 4 partitions set up 1. /boot 2. /swap 3. / root for Ubuntu and 4. / root for whatever distro I'm currently looking at. I have used the [COLOR="Red"]Knoppix 4.0[/COLOR] live cd to view and edit the menu.lst file but I [COLOR="Red"]can't save it back to the /boot/grub directory.[/COLOR] I've been using PC's since the days DOS ruled and I am just to lazy to go back to the command line if I can help it. I feel I am missing something simple.

---

### Post by GuitarHero on 2006-07-13
you need to use the command line in the live cd to mount your ubuntu hdd.  Search the forums to find how to do it, i forget.  Then you can edit any file on there like normal.

---

### Post by Kilz on 2006-07-13
> **louieb said:**
> I can't tell you how many time I have reinstalled Ubuntu just to fix my menu.lst file. The PC I'm using has two 30 gig hard drives. Windows XP is on hdb. On hda I have 4 partitions set up 1. /boot 2. /swap 3. / root for Ubuntu and 4. / root for whatever distro I'm currently looking at. I have used the [COLOR="Red"]Knoppix 4.0[/COLOR] live cd to view and edit the menu.lst file but I [COLOR="Red"]can't save it back to the /boot/grub directory.[/COLOR] I've been using PC's since the days DOS ruled and I am just to lazy to go back to the command line if I can help it. I feel I am missing something simple.

Sometimes the command line can make your life a little easier. Like editing files as root while you are loged in as a user. That way you dont need a live cd. Open a terminal, copy and paste this in if you dont feel like typing.
```
gksudo gedit /boot/grub/menu.lst
```
The text editor will then open as root with the menu list. Edit to your hearts content, and save it.

---

### Post by aysiu on 2006-07-13
Yes, you're missing a few simple things.

1. Every time you modify a system file, you should make a backup copy beforehand ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
``` That way, if you ever screw it up again, you can just press Control-Alt-F1, log in, and type ```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
``` and you're back to your original menu.lst.

2. You can install this on Windows XP and modify the /boot/grub/menu.lst file from Windows:
[http://www.fs-driver.org](http://www.fs-driver.org)

3. Knoppix has a super-user mode or browse as root button on it somewhere. If it doesn't (or you can't find it), just go to a root terminal and type ```
konqueror
``` and you can browse as root and change the /boot/grub/menu.lst file on the mounted partition.

---

### Post by louieb on 2006-07-13
Thanks for the help. I will remember to back it up. I found the reason that I could not save changes was the Knoppix mounts the partition as read only. So I had to a little command line work to unmount the partition and remount it so that I could write to it. 
```
umount /dev/hda1
mount -orw /dev/hda1

```Then I could open it up in an editor make my changes and save it back.

---

