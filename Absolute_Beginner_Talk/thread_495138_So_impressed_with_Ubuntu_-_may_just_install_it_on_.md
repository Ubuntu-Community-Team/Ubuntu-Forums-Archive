---
title: "So impressed with Ubuntu - may just install it on another PC! (but before that...)"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-07-07
I have XP installed on another part.

How do I make a partition/wat does a partition do? will it mess up my xp part?

---

### Post by chuckyp on 2007-07-07
Okay if you image you hard drive as one big container.  partitions tell your computer where the container stars and begins.  You can have multiple partitions on the same drive.  ex:  you can install ubuntu and have it dual boot with xp.  You just have to resize the xp partition.  There are a plethora of options perhaps you should check out help.ubuntu.com and read the desktop guide.

---

### Post by wolfen69 on 2007-07-07
you need to defrag windows then create another partition with gparted or any other disk manager.

---

### Post by alienexplorers on 2007-07-07
When you dual boot you have to make partitions for Ubuntu and swap.  Once you have them install your live-cd and select install.   When you get to the part about selecting partitions make sure you select the ones you made for Ubuntu or you will over write windows.  When it is done just reboot and you should get a grub menu asking what you want ti boot,  The default is usually Ubuntu.
> [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by dansco on 2007-07-07
> **wolfen69 said:**
> you need to defrag windows then create another partition with gparted or any other disk manager.

defrag twice just to be sure. (past experience)

---

### Post by ajskhan on 2007-07-08
What is a swap? Can't I defrag a couple times, then make a partition usnig the live CD one of the current XP and another blank? (using gparted?)

---

### Post by Dyegov on 2007-07-08
Actually you don't need to do any of those. When you install from the live cd, one of the steps is the partitioning. You select "Resize actual partition" (Or something along those lines), select the new Windows' size with an easy to move bar, and you're done! The rest of the disk will be used for ubuntu. THe dual boot will work automatically too that way :)

---

### Post by ajskhan on 2007-07-08
do i still need 2 defrag 35+ times?!

---

### Post by Tomosaur on 2007-07-08
> **ajskhan said:**
> do i still need 2 defrag 35+ times?!

Well, you need to defrag until you can't improve the fragmentation of your hard drive any more, yes - otherwise you're just asking for trouble :P

---

### Post by ajskhan on 2007-07-09
AHAH - ok, and what about the 7.4 ubuntu?

---

### Post by az on 2007-07-09
> **ajskhan said:**
> do i still need 2 defrag 35+ times?!

If the Ubuntu installer does not give you the option of resizing your current windows partition, you should reboot and defragment again.

---

### Post by ajskhan on 2007-07-09
> **az said:**
> If the Ubuntu installer does not give you the option of resizing your current windows partition, you should reboot and defragment again.

OK - well Disk defrag in windows is crazy

and out of 24gb i have 8gb left

---

### Post by KIAaze on 2007-07-09
If the windows defragmenter does stupid things, you can use [O&O defrag]("http://www.oo-software.com/home/en/products/oodefrag/") for example.
What's important is not how many files are not fragmented but rather how much continuous free space there is. ;)

There are some problematic files when defragmenting a Windows partition:
[http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/]("http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/")
This link doesn't seem to work right now, but it helped me a lot.
If I remember correctly, one of the problematic files was the "system restore" file.
You'll have to disable "system restore" in order to delete it.

Some partitioning tips and explanations:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

