---
title: "Can I access my 6.06 files with 5.10 live CD"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-10-21
I have cannot revive my xserver after multi-attempts at updating drivers for an old ATI Rage 128.
Now I'm ready to get a new card but I wonder if there is a way i can use the live cd to get into my files and back thyem up first.
Any help?

---

### Post by wieman01 on 2006-10-21
Yes, you can to that. You need to boot from Live CD, mount your harddisk, and copy file to a USB driver or any other storage device. Should be no problem at all.

Boot from Live CD, open a terminal, and type:
> df
Which is the partition you are talking about? HDA1?

---

### Post by kindafunnylookin on 2006-10-21
> Which is the partition you are talking about? HDA1? Yes, I think that is it, so the thing is to just get to partition?

---

### Post by wieman01 on 2006-10-21
When you have booted, this is the command to mount HDA1:
> sudo mount /dev/hda1 /mnt
Then you can access your root file system:
> cd /mnt/
Or /home:
> cd /mnt/home/
Then simply copy whatever you need. Or simply use Gnome's file browser.

---

### Post by kindafunnylookin on 2006-10-21
I will try that. Thank you. I will post the results.

---

