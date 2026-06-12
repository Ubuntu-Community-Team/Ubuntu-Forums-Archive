---
title: "where is my hard drive"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by chimchim on 2008-02-02
I am running 7.10 and have two internal hard drives on my system. They are both recognised by the BIOS and by Ubuntu. Unfortunately Ubuntu chooses to ignore the second drive. After spending several weeks reading almost every tutorial on how to mount this drive I have finally had a small measure of  success. I have laboured through Gparted and fstab and now have confirmation that the drive is mounted as /dev/sdb1 - yippee!

My problems now are, where is it and how do I get it on my desktop so that I can use it?

One other thing, the entries in Gparted show a locked padlock on each line. What does this mean?

My thanks for any help.

---

### Post by Nythain on 2008-02-02
what does your fstab look like???

whats the output of sudo fdisk -l

---

### Post by jan quark on 2008-02-02
check the media or the mnt in the filesystem

---

### Post by wolfen69 on 2008-02-02
> One other thing, the entries in Gparted show a locked padlock on each line. What does this mean?

you need to open gparted as root.(superuser)
```
sudo gparted
```
this will unlock the drives.

---

### Post by chimchim on 2008-02-02
First, I thank you for your responses.

Nythain.   I am currently running two computers with Windows on this computer so cannot easily paste the whole file details but I can tell you that fdisk shows similar details for both drives and the relevant entry in fstab reads

/dev/sdb1   /datadisk   ext3   defaults   0   0

Does this help?

jan quark.  How?   I am new to this stuff.:confused:

wolfen69.   Did that, whats the next step?:)

---

### Post by jan quark on 2008-02-02
see pics

I just wanted that you navigate in the filesystem to the folders
sorry next time I will answer more in detail

computer > filesystem > media

---

### Post by chimchim on 2008-02-02
Thank you jan quark.

I have now found two entries for this drive, one listed in **File System **and the other in **media**. I am the owner of the first one and root is the owner of the other. I am beginning to wish I hadn't asked this question.

Thanks again.

---

### Post by jan quark on 2008-02-02
hey 

ask, we are here to  answer no matter how simple it might be, we are all learning everyday, every second,,,

---

