---
title: "External Hard drive permissions problems???"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by fishsa on 2006-11-21
I have just started using Ubuntu 6.06

and i have a 160gig external hard drive that it picks up yet it wont let me write any files to the hard drive 

when i go into the drives properties and select the permissions tab and then check the write box its brings up and error screen and tell me that: 

"Couldn't change the permissions of "External " because it is on a read-only disk"

How do i change the permissions so i can write things to my hard drive ????

---

### Post by derby007 on 2006-11-21
If your External hard drive is formatted to NTFS then u will have problems, however if it's FAT/FAT32 then u should be OK. I have a 250GB USB external hard drive, and only read from it...cause its formatted to NTFS as i store my multimedia on it, via windoze(on my way to converting, tho !).

---

### Post by fishsa on 2006-11-21
I cant remember what i formated it as 

is there any way to check??

and if it is NTFS is there no program that will allow you to write to it???

---

### Post by taurus on 2006-11-21
Actually, you can write to NTFS with ntfs-3g now...  There are a few threads around here explaining how to install and configure it.

---

### Post by taurus on 2006-11-21
> **fishsa said:**
> I cant remember what i formated it as 

is there any way to check??

and if it is NTFS is there no program that will allow you to write to it???
Run this command at the prompt to find out, Applications -> Accessories -> Terminal!

```
sudo fdisk -l
```

---

### Post by mbstrlbstr on 2006-11-21
I had this same problem 2 weeks ago.
I used GParted to format the drive to fat32. Just remember to back up any files if you do that.

---

### Post by derby007 on 2006-11-21
Thanks Taurus, by the way how could i install this (on a PC that doesnt ave Internet) ? ie. is there a .deb file, and is there many dependencies, i have 6.06 Dapper 2.6.15 kernel...

---

### Post by Ben Sprinkle on 2006-11-21
[Click here to learn how to write to NTFS partitions.](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by fishsa on 2006-11-21
Ok did that and it is NTFS 

reading up about ntfs-3g to try get that working are there any other programs
that i could use

---

### Post by Ben Sprinkle on 2006-11-21
Probably, but never heard of anymore.

---

### Post by derby007 on 2006-11-21
Cheers, didnt see ure post, i was googlin & found : 
[http://doc.gwos.org/index.php/Write_ntfs]("http://doc.gwos.org/index.php/Write_ntfs")

---

