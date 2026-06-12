---
title: "[SOLVED] can't access hard drive"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by bjameswilliams on 2008-01-18
windows xp crashed on me & a friend suggested using ubuntu to access my hard drive, as i can't even boot up windows anymore. but when i try to access my hard drive through ubuntu i get a "cannot mount" error message with the suggestion to shut windows down properly first, which of course i can't do since i can't boot windows.

is there some way to reset or properly shut down windows through ubuntu? or some other way to get at my data? thanks for any help!!

---

### Post by mkwerner on 2008-01-18
You can override that error by issuing some commands from the shell:

Assuming your Windows partition is the first on the hard drive, do the following from a shell ->

sudo mkdir /mnt/windows
sudo mount -t ntfs-3g -o force,users /dev/hda1 /mnt/windows

(or use /dev/sda1 if you have a SATA hard drive)

Then you can access your windows drive via /mnt/windows

HTH,
M.

---

### Post by Het Irv on 2008-01-18
I think if you read this thread you should be able to solve your problem. [Link]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4153070")

Or just read the first response since it says about the same thing

---

### Post by bjameswilliams on 2008-01-19
thank you so much! you have no idea how much better you just made my life.

---

