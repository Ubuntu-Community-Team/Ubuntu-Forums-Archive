---
title: "How to come back to windows?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Albot on 2007-09-03
Hi, i installed Ubuntu on my dads old laptop (he said he didn't need it anymore) so i installed and anything worked well... but now my brother needs it for his school..

its a Acer and when i put in the Acer recovery disk in its not booting from it... its just starting Ubuntu normaly..

what is wrong what should i do to get windows back ? 

Thanks 
Albot

---

### Post by taurus on 2007-09-03
Go into the BIOS and make sure you have CD-ROM before harddrive in the boot option.

---

### Post by oilchangeguy on 2007-09-03
enter the bios, and make sure the computer is set to boot from the cd drive, first.

---

### Post by Zoiked on 2007-09-03
You have to reinstall Windows Xp from scratch from a real XP Disk, not a acer recovery.

There is no other way to get your xp back, cause you deleted everything(Including the acer recovery files it needs to use that disk) when you installed Ubuntu. Might I add that if you install XP from scratch, you don't get all your programs back.

---

### Post by meindian523 on 2007-09-03
A good way to allow your brother to use the lappy for his school AND preserve Ubuntu is to install Windows as a dual boot and boot into the OS you require at the particular time.Only 1 step would be added namely selecting the OS to boot for your brother.

What you will have to do is to install Windows using it's CD and then repair the bootloader(Grub) by following the HOW-TO given here......
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

But be sure to install Windows in a separate partition...one which has NOT been used to install Ubuntu.....

---

### Post by anewguy on 2007-09-03
If the Acer recovery CD works like my Gateway recovery CD, you will be able to reinstall Windows, but you have to do one step first:  you have to make room for it by either resizing or removing the Linux partitions.  My recovery CD will not install on top of active partitions, and I assume that is what you are running into.

I will assume you installed from the Ubuntu LiveCD, so put that disk in the drive and reboot your laptop so it is running from the LiveCD, not from the Ubuntu installed on your hard disk.

When the desktop comes up, go into terminal and type:

sudo qtparted

if that doesn't work, then type:

sudo parted

type   help  and press enter to get the commands available

The first thing you will need to do is delete your Ubuntu partitions - including swap.  This should bring you back to one large partition.  

Now you can restart your laptop on the recovery CD and it should run.:)

---

### Post by mb01915 on 2007-09-03
What does your brother need at school that he cannot get using Ubuntu?

---

