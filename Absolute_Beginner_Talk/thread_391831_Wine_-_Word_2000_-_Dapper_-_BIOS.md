---
title: "Wine - Word 2000 - Dapper - BIOS"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-23
1. Using Wine, do I install Word 2000 directly onto my Linux HDD in order to use Word 2000 from Dapper? 
2. If I can't get my computer to recognize a HDD which has WinXP, do I need to check my BIOS to see if the drive is set to be booted onto? I hope this makes sense. (I lost the ability to go into my WinXP HDD when I installed Feisty, which I am no longer using. I am back to using Dapper.)
kh

---

### Post by 1/0 on 2007-03-23
1. Why would you ever want to install M$ Word when there's OOO??? If you would install a wine program, that would be done in a fake drive in .wine.

2. Which drive that boots is set by grub. The config file is in /boot/grub/menu.lst

---

### Post by kittyhawk63 on 2007-03-23
> **1/0 said:**
> 1. Why would you ever want to install M$ Word when there's OOO??? If you would install a wine program, that would be done in a fake drive in .wine.
2. Which drive that boots is set by grub. The config file is in /boot/grub/menu.lst

!. I do editing for over 30 authors that only use MS Word. Word 2000 is able to do all the editing properly for their needs. 

2. I have GRUB installed onto my Master hard drive (Linux - Dapper) by default. However, it messed up my other drive somehow when I installed Feisty and now I am completely unable to boot up to it. I can remove the Linux drive and only attach the winXP drive and my computer will no longer recognize it. I can't even get BIOS to recognize it. I did not have any problem before I installed Feisty. I am now back to Dapper, and there is no GRUB recognizing my WinXP hard drive.

---

### Post by 1/0 on 2007-03-23
1. Frank's corner might give a clue on how to install office under wine: [http://frankscorner.org/index.php?p=office2000](http://frankscorner.org/index.php?p=office2000)

2. Is grub configured for a dual boot with Windows XP. If not check the end of this document where it is discussing grub: [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by kittyhawk63 on 2007-03-24
> **1/0 said:**
> 1. Frank's corner might give a clue on how to install office under wine: [http://frankscorner.org/index.php?p=office2000](http://frankscorner.org/index.php?p=office2000)

2. Is grub configured for a dual boot with Windows XP. If not check the end of this document where it is discussing grub: [http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp](http://apcstart.com/5459/dualboot_ubuntu_and_windows_xp)

1. Maybe I am missing something here. If I only attach my WinXP HDD to the computer, and it is not recognized, what does that have to do with GRUB? I was always able to boot to it when it was the only HDD. 

Note: I am fairly certain that GRUB is only installed to my Linux HDD. 

2. Yes, I had GRUB showing both HDDs before I installed Feisty. I think that is what you mean by dual boot. Even though I have now installed Dapper again, GRUB still does not recognize my WinXP drive nor does the BIOS.

---

### Post by seshomaru samma on 2007-03-24
> GRUB still does not recognize my WinXP drive nor does the BIOS.
if your bios doesn't recognise the drive then ubuntu will not see as well

do you have gparted installed?
does it show both your HDD?

---

### Post by 1/0 on 2007-03-24
What kind of hard drive is this? If its a second IDE hard drive you should see it as /dev/hdb*, where the asterisk stands for a number. The b is for second drive. You can mount it on any unused directory by:

```
mount /dev/hdb* unused/directory
```

If you, on the other hand, use an IDE-to-USB cable, the drive will be found under /dev/sda*. 

If there's no drive found in /dev/ at all, you got a problem but it all depends on what kind of drive it is.

---

### Post by kittyhawk63 on 2007-03-24
> **seshomaru samma said:**
> if your bios doesn't recognise the drive then ubuntu will not see as well

do you have gparted installed?
does it show both your HDD?

I have just now installed GParted. I have _never_ used it. Not sure if I know how. I will check it out though.
Thanks for your suggestions.
kh

---

### Post by kittyhawk63 on 2007-03-24
> **1/0 said:**
> What kind of hard drive is this? If its a second IDE hard drive you should see it as /dev/hdb*, where the asterisk stands for a number. The b is for second drive. You can mount it on any unused directory by:

```
mount /dev/hdb* unused/directory
```If you, on the other hand, use an IDE-to-USB cable, the drive will be found under /dev/sda*. 

If there's no drive found in /dev/ at all, you got a problem but it all depends on what kind of drive it is.

It is a 40GB Maxtor Ultra ATA/100 HDD.
Maxtor 536DX  5400 RPM
I am not sure, but I think it is an IDE HDD.  Does the ATA say otherwise?
kh

---

### Post by kittyhawk63 on 2007-03-24
It is a 40GB Maxtor Ultra ATA/100 HDD.
Maxtor 536DX  5400 RPM
I am not sure, but I think it is an IDE HDD.  Does the ATA say otherwise?
kh

---

### Post by macogw on 2007-03-24
Crossover Office

---

### Post by kittyhawk63 on 2007-03-24
> **macogw said:**
> Crossover Office

What?

Note: I just googled Crossover Office and see what I can do with it. Thanks alot.
kh

---

### Post by 1/0 on 2007-03-26
Its an IDE drive, you can see it also at the cable. This means that your drive should be /dev/hdb*, as I said before. What's the result of (with the drive plugged in (both cables)):
```
ls /dev/hdb*
```

---

