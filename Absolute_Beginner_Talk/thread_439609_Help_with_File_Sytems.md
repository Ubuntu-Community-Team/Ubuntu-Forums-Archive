---
title: "Help with File Sytems"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Billy_1900 on 2007-05-10
First of all, I know just enough about Linux to be dangerous.

My issue is that I have 2 Hard Drives in my PC, my main one is where ubuntu is installed, the OS I use. Next, I have a secondary HD (identical to main) that I did not Format during installation.  It is still on an NTFS format so I am limited in what I can do with it... as far as I can tell, I can just view it.

My problem is how do I 'Format' this HD to a Linux style filesystem so I can use it?

/dev/sda1  is my HD that has ubuntu on it.  /dev/sdb1 is the NTFS HD.

-Billy

---

### Post by mikewhatever on 2007-05-10
You can format it from the live CD using Gparted in Systems>Administration, exactly the same way you formatted partitions for Ubuntu. Before you do that, did you know about ntfs-3g? It is in the repositories and can be useful if you use any MS OS. If you only use Ubuntu, then it's a good idea, but obviously, you'll loose all data on that HDD while formatting.

---

### Post by spur on 2007-05-10
You will a program like qtparted installed first. Then start it and highlight the drive you want to reformat.
Sorry I'm not more specific but I haven't done it just looked into how to. It should work, so is worth a try.

---

### Post by Billy_1900 on 2007-05-10
Thanks Guys,

I'm gonna look into the ntfs-3g, but I really have no intention of using any windows applications on this PC ( I have my laptop for that). This is my desktop, and it will force me to learn this OS!

Mainly, I believe just reformatting it is the best way for my purposes. 

I'll let ya know how it goes!

-Billy

---

### Post by Billy_1900 on 2007-05-10
Well,  I installed Gnome Partition Editor, but it says I don't have permission to anything (read-only).  It also says Owner unknown.  How can I get around this? 

-Billy

---

### Post by spur on 2007-05-10
I believe this is because windows partitions don't come with permissions built in like Linux. If I want to repartition any hard drives I use third party software that boots from a cd. If you do this make sure you are repartitioning the right partition! 
You might be able to find a trial edition of something like Partition Magic that will enable you to burn a cd of it and use it a couple of times. This would cleanly solve your probs. Apart from that if you can run your Partition Editor as root you might have some success.
You will need to know where it is and then run "sudo path to program/program" or "sudo nautilus" then find the program and click on it.

---

### Post by jbro on 2007-05-10
Hello,

It's possible that you had permissions problems because that disk was still mounted. Try the following.

[LIST=1]
[*]At a shell prompt type ```
mount | grep /dev/sdb1
``` If you get a line like ```
/dev/sdb1 on /windows type ntfs (rw,nls=utf8,umask=007,gid=46)
``` then the drive is mounted (note that the important bit is the /dev/sdb1 the beginning of the line, the other output may vary.) In this case type ```
umount /dev/sdb1
```
[*]You now need to use a partition editor to change the partition type on your second disk to "Linux". To do this, type ```
fdisk /dev/sdb
``` and then hit 't', answer "1" to select the partition to modify and then enter "83" for the partition type. This indicates a Linux partition.
[*]In fdisk type "w" to save the partition changes. You will end up back at a shell prompt. 
[*]At this point your partition needs to be formatted. Use one of the following commands, depending on whether you want to have an ext2, ext3 or reiser file system: ```
mke2fs /dev/sdb1
mke2fs -j /dev/sdb1
mkreiserfs /dev/sdb1
```
[*]If you want your new partition to always be automatically mounted, you need to add a line to /etc/fstab. This line will specify the partition, the mount point, the file system type and some other options. Typing "man fstab" at a prompt and reading the docs and checking out your existing /etc/fstab file is a good start to knowing what to put in this file.
[/LIST]

Regards,
jbro

---

