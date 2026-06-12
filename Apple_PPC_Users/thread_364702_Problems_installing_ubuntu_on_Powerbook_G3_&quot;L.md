---
title: "Problems installing ubuntu on Powerbook G3 &quot;Lombard&quot;"
date: 2007-02-18
forum: Apple PPC Users
---

### Post by DisgruntledPostMan on 2007-02-18
I have a powerbook G3 that I am trying to put linux on, and I am running into quite a bit of problems.

Number one, after burning the proper .iso to a CD-RW disc I put it in my disc drive and OS 9 hangs. It unhangs eventually and says that I need to initialize the disc, which would wipe it.   I know the disc drive works so I have ruled that out, but none of the discs I burn work, the alternate install disc also wont load.

Number two, upon booting into the frimware I try to boot the CD and it says that it either cannot boot or that the disc boot size is zero.  I have verified data via MD5 hash on each disc too.

I'm desperate now to get OS 9 off of the mac and put ubuntu on. [-o<

Aslo, I have tried both 6.10 "Edgy Eft" and 6.06 "Dapper Drake."

It is a 6 gb hard drive, also I don't have the installer disc for OS 9 so I don't know how to reformat or partition it in any way.

Some one told me I may need to "partition a part of your drive to ext3 (I recommend at least 10 GB), and another part to Linux-Swap" :-s But I can't do that because of 6 gb hard drive, and the disc not even being read by the computer.  Currently my Mac is OS 9.1 would it work if it was OS 9.2.1 or 9.2.2? :-k

Thanks in advance for all the help.

---

### Post by Peter76 on 2007-02-18
What did you do to burn the iso to cd? It sounds to me like something went wrong there...

---

### Post by DisgruntledPostMan on 2007-02-18
I used a burning utility that came with my cd burner, its by nero.  Is taht bad? :(

---

### Post by alyoung on 2007-02-18
Did you download the PowerPC or i386 image?

---

### Post by DisgruntledPostMan on 2007-02-18
PowerPC

---

### Post by grazie on 2007-02-18
> It unhangs eventually and says that I need to initialize the disc, which would wipe it.
I'm not sure what you mean by this.

Also, I think it would be a good idea to keep OS9 for the time being by using the disk tools available once you've booted *Ubuntu. You can compress the OS9 partition to less than 1G if you don't have lots of data and applications installed.

A good test of whether you've done a successful burn is being able to view the many files and folders on the burnt CD. Can you see these from OS9? Can you see these from a Windows machine? Also, just because your machine can boot OS9 and/or OS X disks, it's no guarantee that it can boot Linux.

Your 6G disk is plenty big enough for Ubuntu. I'd recommend using Xubuntu to get the best performance. The only thing I'd be concerned about is keeping your OS 9 driver partitions as the installer may wipe these. If you then want to go back to OS9 for any reason (there are some benefits) re-installing all OS9 partitions may give you problems.  Why not let the installer set up the partitions automatically after you've compressed the main OS9 paritition, left the OS9 boot partitions untouched and left the rest of the disk unallocated?

---

### Post by DisgruntledPostMan on 2007-02-18
I CAN see the files burnt in windows, and when I put it in the laptop it gives me three choices which I belive are three different file formats for macs.  I really don't want to go back to OS 9 and I have a different laptop with all the same files on it and such that is on OS X so I just want this one for linux, also with Xubuntu do you have all of the same features as Ubuntu?

Should I update the OS to 9.2.2?  Would that help?

> **grazie said:**
> I'm not sure what you mean by this.

I hope that helps.  To answer the question of what I mean by it anyway.

---

### Post by grazie on 2007-02-18
> when I put it in the laptop it gives me three choices which I belive are three different file formats for macs Sorry I don't know what you mean by this either. Are you doing this from OS9?

Xubuntu doesn't have all the features of Ubuntu, but it does have a few that Ubuntu doesn't. It depends on what you want/need/prefer.

It looks like your burnt images may be fine. You could try booting the CD from Open Firmare using cmd+opt+O+F on booting the machine and then using the following command

```
0 > boot cd:,\\yaboot
```
There's many other things the can be done from Open Firmware, but there are too many options to go into here. If the boot fails you can shutdown the machine using

```
0 > shut-down
```

It would be worth trying to burn at the slowest possible speed. If you're using a CD-RW again make certain you do a complete wipe (not quick) first. I'd try a CD-R myself. Don't use the machine for anything else while burning. If you do have a good image burn, then the most likely cause for failing is your CD ROM. You may be able to boot from an externel CD ROM drive if you have access to one, but I don't know whether your machine supports it. I do know the B&W G3 PowerMac doesn't.

---

### Post by DisgruntledPostMan on 2007-02-18
I will try it with a CD-R because I have tried booting it from the firmware as you said but only with the cd-rw.

yes I am doing this from OS 9.



EDIT: It says Bad READ-1 Cant OPEN cd:,\\yaboot

Booting by pressing C to boot from disc just makes the cd drive go nuts and then it brings me to the firmware saying method <draw-rectangle> not found then a bunch of code that is ihandle and phandle stuff.

---

### Post by Peter76 on 2007-02-19
Just to get something cleared; you did burn the iso as you downloaded it; you didn't open/mount it or anything? You should burn the image, not the opened/mounted stuff. Otherwise, try using some other program for burning.... Something is going wrong there...

Good luck

---

### Post by DisgruntledPostMan on 2007-02-19
Whats a good program for burning images to discs that is free?

---

### Post by grazie on 2007-02-19
How long is a piece of string?

It depends on what platform it's for. On Linux K3B is probably the best, but it's best suited to KDE, so I use graveman which works just fine. On OS X, the DiskTool is good. On Windows and OS9 I've no idea, but I'm sure there must be some good free onea available now.

However, it's more likely that you've got a hardware problem. Can you not check whether you can boot the CDs you've burnt on another Mac?

---

