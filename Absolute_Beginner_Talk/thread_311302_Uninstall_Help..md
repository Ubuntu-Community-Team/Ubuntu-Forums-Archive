---
title: "Uninstall Help."
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by compaq_xp on 2006-12-02
I need to know how i can uninstall Ubuntu So i can reinstall Windows 3.1

---

### Post by Shatrat on 2006-12-02
You can just format the disk.  I dont know much about the windows installer but surely it has the ability to do that.
Keep in mind, installing windows over a linux installation qualifies you for the 4th circle of hell, its worse than having impure thoughts about your cousin.

---

### Post by compaq_xp on 2006-12-02
Anyone?

---

### Post by compaq_xp on 2006-12-02
ok Shatrat , I'm goingto try but it's a very old windows system

---

### Post by eriefisher on 2006-12-02
Insert the windows installer disc and reboot.

---

### Post by Frak on 2006-12-02
I don't think age has anything to do with it? An HDD is and HDD all the way through, and an installer might change the way it works, but the harddisk *has* to be formatted.

---

### Post by halitech on 2006-12-02
boot from a windows boot disk (cd or floppy) and it should format for you. if that doesn't work, check out [http://www.bootdisk.com/bootdisk.htm]("http://www.bootdisk.com/bootdisk.htm")

or

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by smile_sunshine on 2006-12-02
Boot into the ubuntu live cd  (any linxu live cd would do if your computer is too slow for the ubuntu one try puppy linux or dsl)


From the terminal: 
> sudo mkdosfs -F 32 /dev/hdx

(replace x with the relevant partition) 

NOTE: I dont know if windows 3.1 uses fat 32?  possibly fat 16 or something as its older ?? (you would have to look it up and replace the 32 with the relevent number).

By the way did you know its possible to dual boot linux and windows so you have both on your system if you wanted ? 

hope that helps :)

---

### Post by halitech on 2006-12-02
smile_sunshine, I would say with almost 100% certainty that win 3.1 uses fat 16 seeing as how it runs on top of DOS and technically isn't an OS.

compaq_xp
Which has me thinking, how are you going to run Win 3.1 on your computer? do you still have a copy of DOS to install first?

---

### Post by compaq_xp on 2006-12-03
Yes I still Have the Old DOS Disks.

Is there Anything I can do in the termanal That Can erase and format the HD?

(The HD is A IBM 3.9GB)

---

### Post by smoker on 2006-12-03
going from memory here, but i think you can use the 'format' command on your dos disk to reformat your harddrive, something like 'format c:' without the quotes

---

### Post by bulldog on 2006-12-03
If you have the old DOS disk you should have one with format.com on it.
Use this disk to format the partitions.
If you want to repartition your hdd,just find fdisk on your floppy.

---

### Post by CatKiller on 2006-12-03
You're going to have to partition that disk as well. Old-skool FAT can't make a partition bigger than 2GiB.

---

