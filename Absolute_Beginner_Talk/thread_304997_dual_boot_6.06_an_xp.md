---
title: "dual boot 6.06 an xp"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by devils3cups on 2006-11-22
Currently i have ubuntu 6.06 as the only os on my system. the ubuntu partition takes up my entire drive. Unfortunately i do need xp for certain things an i need to repartion my drive. I just want to make sure i know what im doing. First i get my live cd. Boot it from there. Go into gparted and resize my drive to make room for oh say 20gb of space for xp. make it ntfs. format it and im done up until installation right?

---

### Post by bulldog on 2006-11-22
XP needs to be the first partition on your drive,make this happen,otherwise you can't boot it.

You can consider VMware server and install XP in ubuntu.[not for gaming]

---

### Post by Bigbluecat on 2006-11-22
Don't forget that installing XP after you have installed Ubunutu will wipe grub from the MBR (Windows will overwrite it) so you will need to re-install grub to the MBR to dual boot.

---

### Post by bulldog on 2006-11-22
That's easy with the live cd.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by devils3cups on 2006-11-22
crap. ok so i have an external hd. is there a way i can copy my partition to the external drive. then wipe my systems drive and put xp on it and then pop my ubuntu partition on it? how would i go about doing this?

---

### Post by Bigbluecat on 2006-11-22
Not sure why you would want to do this. Certainly make a backup of important data before any re-partitioning - there is always a risk.

Installing XP does not wipe Ubuntu - only the bootloader which can easily be re-installed as Bulldog has kindly and on many occasions clearly described how to do.

---

### Post by devils3cups on 2006-11-22
sorry im a bit of a noob. how do i re-install the bootloader? from what i said in my first post is that how i go about this though?

---

### Post by Neobuntu on 2006-11-22
A common mistake is when new users go try and do grub installs manually (instead of the distributions installer) and using the "setup" command they mistakenly tell it to write grub to the start of a partition (Bad, very bad, It takes out/writes-over the installed software), instead of the start of the drive (MBR.) It's the "root" GRUB command where you specify the partition (hdx,x) where GRUB files (like the menu) reside. NEVER do anything other than a "setup(hd0)" normally (That is, one drive number for it's MBR.) Anything else is for exotic and usually not needed configurations.

I don't know WHY GRUB doesn't give a warning (and y or n) when users put in something other than "Setup(hd0)" (and confusing it with the "root(hdx,x)" command).

Most peoples root is "root(hd0,1)" for the one and only hard drive (0) and the second partition after Windows (1). Of course, if you make a swap part the second and Linux on the third then it's root(hd0,2) etc. 

Please don't confuse GRUB's "root" with its "setup" commands.

---

### Post by Bigbluecat on 2006-11-23
The response from Bulldog earlier in this thread tells you how to re-install the bootloader after windows has overwritten it. 

You can use the Ubuntu LiveCD to do this.

Make sure you back up your data before starting this. There is always a risk of something wrong when you play around with partitions.

---

### Post by Bachstelze on 2006-11-23
> **bulldog said:**
> XP needs to be the first partition on your drive,make this happen,otherwise you can't boot it.

Wrong. XP is the third partition on my drive and boots just fine.

---

### Post by gn2 on 2006-11-23
> **HymnToLife said:**
> Wrong. XP is the third partition on my drive and boots just fine.

Guess you're not using the standard Windows bootloader then.....

Perhaps you could include a link to instructions for creating your set-up?

---

### Post by Bachstelze on 2006-11-23
Well, using the standard Windows bootloader is not exactly the easiest way to setup a dual-boot, is it ?

---

### Post by gn2 on 2006-11-23
> **HymnToLife said:**
> Well, using the standard Windows bootloader is not exactly the easiest way to setup a dual-boot, is it ?

I find it is: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by nickburns on 2006-11-23
you can always user vmware and then you don't have to dual boot


[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

---

### Post by gn2 on 2006-11-23
> **nickburns said:**
> you can always user vmware and then you don't have to dual boot


[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

Yes that's what I've found best, after dual-boot hassles it's VMWare from now on for me.

---

### Post by Neobuntu on 2006-11-27
Well, I hope my manual GRUB reinstall warning helps "Absolute Beginners" that learn enough about GRUB to make that mistake. That is, when they are looking for a quick way to reinstall GRUB (manually). After Windows (or whatever) writes over their MBR.

The thing is we are getting too far away from "Absolute Beginner".

If you have two computers. Use the older one for Windows and if you know anything about Windows you know that a "clean" install is best. Then you can devote your newer computer to Kubuntu and install from the live CD with everything done for you. See [http://www.getautomatix.com](http://www.getautomatix.com) afterwards.

If you have the one computer and don't want to do the better clean install of Windows in first position. Just click "qtparted" (Kubuntu live) and shrink it to half so that the Kubuntu live installer can then do the rest for you.

It is BEST to just leave Windows on the first partition because there is simply less to do, and remember. That is, until you never use Windows and then you can do a quick new install of Kubuntu after saving the files you can't live without (like to a cheap flash drive. It's click and drag.).

It's generally better to do a new install rather than an upgrade and Kubuntu (or ubuntu if you wish) installs fast and easy whereas Windows does not. Then Windows NEEDS a clean install and thus the pre-installed advantage is a myth.

Google all your devices for working ease with kubuntu and simply replace any rare device that doesn't play. This way, you have ZERO driver setup. Don't let some old $2 device that only works with Windows 98 keep you from the open software advantage. Don't fight them, replace them (about $20).

---

### Post by bulldog on 2006-11-27
> **HymnToLife said:**
> Wrong. XP is the third partition on my drive and boots just fine.

Well I'm very curious what your first partition is then.
In my understanding the first partition hold the windows boot files,this can be a small FAT32 or a Large NTFS partition.

But if I can learn something how it can be done otherwise I surely want to.

---

