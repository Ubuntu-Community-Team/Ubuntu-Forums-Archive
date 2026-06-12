---
title: "how do I use ubuntu liveCD to uninstall ubuntu?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by pearlygate on 2007-12-29
Hi, I just removed my ubuntu partition using norton partition magic. Anyway I encountered a problem with Grub because I forgot to deal with grub when I uninstall my ubuntu. 
I tried using fixmbr method from windows recovery mode but it still didnt fix the boot order. Every time I boot the computer, it will automatically restart back to the beginning. 

Anyway, I still have my ubuntu liveCD, how can I use this liveCD to fix the boot order to windows?

Thank you

---

### Post by Keen101 on 2007-12-29
You need to somehow fix your MBR bootloader.

You could try a number of things. You could look into the S**uper Grub Disk**, as it is supposed to help people fix the grub, so it can boot into Windows.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


or you could try the following

> **Sef said:**
> The code you need is ```
fdisk /mbr
```.


> **Gone fishing said:**
> Just boot from the XP recovery disk, start up the recovery console and type fixmbr. This will overwrite grub with the standard XP mbr.


[http://ubuntuforums.org/showthread.php?t=652716](http://ubuntuforums.org/showthread.php?t=652716)

---

### Post by ugm6hr on 2007-12-29
> **pearlygate said:**
> Hi, I just removed my ubuntu partition using norton partition magic. Anyway I encountered a problem with Grub because I forgot to deal with grub when I uninstall my ubuntu. 
I tried using fixmbr method from windows recovery mode but it still didnt fix the boot order. Every time I boot the computer, it will automatically restart back to the beginning. 

Anyway, I still have my ubuntu liveCD, how can I use this liveCD to fix the boot order to windows?

Thank you

Can you boot into Windows at all?  Is it Vista or XP?  fixmbr from the Windows CD didn't work - that's odd...

This has a list of solutions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you can still access XP - the fixmbr.exe method is probably easiest.
If it's Vista - EasyBCD.
If you can't access Windows - fixmbr from the XP disc should work (Windows Console Recovery Method).

---

### Post by meierfra on 2007-12-29
> how can I use this liveCD to fix the boot order to windows?

Click on FixMBR in my signature. It has three ways to fix the MBR. The third one can  be done from the Ubuntu LiveCD.

But I'm not sure it will  solve your problem. Because it does the same  thing  as "fixmbr" 

Did you do "fixboot" from the WindowsCD?

If none of this helps  post the output of 

```
sudo fdisk -l
```

Also see whether you can access your Windows partition from the LiveCD ( (Go to Places->Computer)

---

### Post by jordank on 2007-12-29
A disk format never hurt anyone :P

---

### Post by pearlygate on 2007-12-29
> **ugm6hr said:**
> Can you boot into Windows at all?  Is it Vista or XP?  fixmbr from the Windows CD didn't work - that's odd...

This has a list of solutions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you can still access XP - the fixmbr.exe method is probably easiest.
If it's Vista - EasyBCD.
If you can't access Windows - fixmbr from the XP disc should work (Windows Console Recovery Method).

I am using windows XP
I can go to windows XP  by inserting my windows installation cd and choose to boot from hard disk

but if I remove my windows CD, the screen just go blank after my Dell logo showed up and it will restart back to the beginning. ( I am assuming the boot loader is pointing to some random address and the default behaviour is to restart.. but I'm not certain. 

I tried using fixmbr but to no avail.
I just tried supergrub -> option fix boot to windows but still doesn't help
fdisk /mbr is basically the same as supergrub so I don't know...

Grub and ubuntu is gone from my system. the partition has already been joined with my windows partition.

Any ideas?

---

### Post by pearlygate on 2007-12-29
> **jordank said:**
> A disk format never hurt anyone :P

in fact the reason I got this problem was because I reformatted my windows xp... then I realized I can't get to XP if I remove my CD so I thought uh oh maybe there's something wrong with grub so I decided to wipe off my linux partition along with grub (erase the problem :P) but that doesnt solve anything so I tried fixmbr but still doesnt help and my last resort was to go to the forum...

anyway I'm trying to format my disk again. hopefully this time it will work...

---

### Post by pearlygate on 2007-12-29
> **meierfra said:**
> Click on FixMBR in my signature. It has three ways to fix the MBR. The third one gone be done from the Ubuntu LiveCD.

But I'm not sure it will  solve your problem. Because it does the same  thing  as "fixmbr" 

Did you do "fixboot" from the WindowsCD?

If none of this helps  post the output of 

```
sudo fdisk -l
```

Also see whether you can access your Windows partition from the LiveCD ( (Go to Places->Computer)

I didn't use fixboot I only used fixmbr. Imma trying fixboot now
edit:

fixboot saves the day!!! HURRAY! Thank you so much. how do I rep you?

---

