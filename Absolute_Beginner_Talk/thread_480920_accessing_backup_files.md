---
title: "accessing backup files"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by prow on 2007-06-21
I recently backed up the files on my windows xp machine (music mp3's, videos, pictures, text documents) onto a maxtor onetouch 200 GB external hdd (USB).  I would like to get those files onto my new ubuntu installation.

The reason is.....i have a windows laptop on my network that uses the desktop that i just revamped with ubuntu as a file server.

Please walk me through the process.

---

### Post by Hobo Joe on 2007-06-21
It should be able to access the Windows network computer without any changing of settings, as long as the files are being shared on the Windows machine.

---

### Post by prow on 2007-06-21
no, your not understanding

Desktop computer used to be windows xp box.  Documents from that computer are now on an external usb hdd.  The desktop computer now has ubuntu linux on it.  I want to mount the ntfs external hdd to my now ubuntu desktop so i can put my files back onto it. (as a server) so my windows laptop can access my ubuntu computer as a server for files and such

all in all i want to be able to use my external hdd as a backup for files on my desktop while my windows laptop accesses my desktop for the files.

i know im confusing but please help

---

### Post by atria on 2007-06-21
Just plug the usb disk into your ubuntu computer. It should be detected automatically and mounted in /media and will promptly show up on your ubuntu desktop.

---

### Post by prow on 2007-06-21
the drive is plugged in and i turned it on and off.......nothing

---

### Post by prow on 2007-06-22
bump

---

### Post by prow on 2007-06-22
can someone who actually knows what im talking about please help me!

And before you answer would you please think about what i want to do before you blert out a dumb answer that doesn't help me one bit.

I dont mean to be rude but i need some serious solutions....not basic answers like "just plug it in" or "it should work"

---

### Post by molly_001 on 2007-06-23
External hard drives which usually have their own boot system (which does the one touch copying for ya) are tricky on Ubuntu at your beginner level.

Just create a Windows domain network on your laptop (leave the USB external drive out of the picture for now).  I think the default name for MS networks is MSHOME or something like that.

Turn off laptop (main machine), restart it.  Then go to Ubuntu machine and you'll probably find the MS network ready for you to connect to.  If not,

then boot into Windows on your Ubuntu machine (if dual boot), and using Windows connect to that network, then go back to the Ubuntu side and you will find the MS network waiting for you.

It seems more logical to just tap straight into the USB external drive for your data, I know, but it might be more trouble than it is worth at this point.

---

### Post by prow on 2007-06-23
well thats not what i wanna do but thanks for letting me know in basically screwed on mounting my maxtor in ubuntu.

---

