---
title: "Dueal Booting Ubuntu &amp; Windows XP"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-23
I have a Fat32 partion and a Ext3 partition on my computer. I was wondering how I can install and dual boot Windows XP?

---

### Post by bulldog on 2006-10-23
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)


[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

This should help you a bit.

---

### Post by Kateikyoushi on 2006-10-23
If windows is not installed on your computer install it first, then install ubuntu by following this guide. [LINK]("http://www.psychocats.net/ubuntu/installing")
Ubuntu will find your exisiting windows installation and add it to your grub menu.

---

### Post by ciscosurfer on 2006-10-23
You may find this page useful: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by amitroy5 on 2006-10-23
I already have Ubuntu installed. I want to add Windows XP. Which guide should I follow for this?

---

### Post by Kateikyoushi on 2006-10-23
Just install windows in the fat partition or make an ntfs, windows will overwrite your mbr and have to install grub again.

Follow this guide to  reinstall grub. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by amitroy5 on 2006-10-23
But if I install Windows XP, I will loose access to Ubuntu. So I have no idea how to reinstall grub. Does anyone have a complete guide?

---

### Post by ciscosurfer on 2006-10-24
Dual-booting problems with Windows and Ubuntu can be solved at the links previosly mentioned as well as here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bulldog on 2006-10-24
> **amitroy5 said:**
> But if I install Windows XP, I will loose access to Ubuntu. So I have no idea how to reinstall grub. Does anyone have a complete guide?

Do it from the live cd.

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by ciscosurfer on 2006-10-24
This info is located in the link I provided in my last post...but I guess it's good to have hear as well!

---

### Post by bkd_life on 2006-10-24
First install Windows XP and then use the grub for dos to dual boot 
ubuntu with xp. And if you want to make ubuntu's grub the boot loader then reinstall grub when you gain access to ubuntu.

Simple, right? :)

---

### Post by amitroy5 on 2006-10-27
What about if I use a recovery CD for installing the Operating System from dell?

---

### Post by bulldog on 2006-10-27
> **amitroy5 said:**
> What about if I use a recovery CD for installing the Operating System from dell?

It depends on what it recovers.

If it whipe out your data and install from scratch you won't be pleased I think.
Better to use a windows cd,can't tell what recovery will do.:D

---

