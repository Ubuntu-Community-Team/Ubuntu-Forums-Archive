---
title: "assistance please on removing vista,installing Xp (have dualboot with ubuntu)"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by 244f on 2008-04-02
hello :)

I have Ubuntu and Vista on dualboot, different partitions. 
Vista is terrible, so I want to install XP instead. but I don't know how since I have grub installed its messing up the XP installation. I tried booting with XP cd and it didn't find any partitions.

can someone please give assistance as to how to remove vista and install XP?

---

### Post by 244f on 2008-04-02
I attached a picture of what my file system looks like.
sda3 is where Vista is installed
the big ntfs sda2 drive is where I keep most my files and want to keep that

---

### Post by Duck2006 on 2008-04-02
Use the gparted live cd or the partition editor in the ubuntu live cd to format your vista partition to ntfs, then install win xp. after you will have to reinstall grub to your mbr.

---

### Post by TeoBigusGeekus on 2008-04-02
Do you have SATA disks?

---

### Post by 244f on 2008-04-02
thank you for your response.

i used the live cd to format sda3 to ntfs
i used the XP cd to boot up and try to install but it still says it can not find any hard disks


SATA? not sure. it's a laptop, one hard drive but partitioned

---

### Post by TeoBigusGeekus on 2008-04-02
If your hd is a SATA one, the original winxp cd will never recognise it. You need to have additional drivers on a floppy in order to proceed with the installation:
[http://cruftbox.com/blog/archives/000867.html]("http://cruftbox.com/blog/archives/000867.html") 
[http://www.alexnolan.net/articles/installxpsata.htm]("http://www.alexnolan.net/articles/installxpsata.htm")

---

### Post by 244f on 2008-04-02
aren't SATA old hard drives? i have a Dell Vostro laptop purchased less than a year ago.
is there a way to check if it is SATA?

---

### Post by 244f on 2008-04-02
apparently I do

[http://transgressive.com/dell-vostro-1400-and-xp-drivers/](http://transgressive.com/dell-vostro-1400-and-xp-drivers/)

---

### Post by TeoBigusGeekus on 2008-04-02
If your laptop has a floppy disk, then you are OK.
If it doesn't, then you can buy an external one for 20 euros or something...

---

