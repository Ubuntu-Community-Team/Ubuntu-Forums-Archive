---
title: "Grub menu not displayed... goes straight to XP"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by ector on 2007-05-19
For some reason when booting my PC the grub menu is skipped altogether and XP is started instead. I have made no changes at all to any of the partitions and the only thing that I did do recently was install IIS in XP. 

Any help in restoring Grub would be appreciated as I'm beginning to really miss my Ubuntu install.. It took quite a while to get it the way I like it :(

---

### Post by H.E. Pennypacker on 2007-05-19
To get the list, press ESCAPE when the computer is starting.  Keep pressing ESCAPE until you get the list, and then select the OS of choice.

---

### Post by ector on 2007-05-19
If I keep pressing ESC I get a list of devices (BIOS menu), namely two hard disks and two DVD drives. It doesn't seem to bring up the Grub menu though.?

---

### Post by macogw on 2007-05-19
You'll have to edit ntldr (the NT bootloader) so that it chainlinks to wherever GRUB is, I think.  I'm assuming GRUB is *there* but just not on the MBR and that Windows's bootloader is in the MBR

---

### Post by Bachstelze on 2007-05-19
Or install GRUB to the MBR.

---

### Post by ector on 2007-05-19
> **macogw said:**
> You'll have to edit ntldr (the NT bootloader) so that it chainlinks to wherever GRUB is, I think.  I'm assuming GRUB is *there* but just not on the MBR and that Windows's bootloader is in the MBR

Any help/advice from anyone who has experience in this area would be greatly appreciated :)

---

### Post by ector on 2007-05-19
> **HymnToLife said:**
> Or install GRUB to the MBR.

Is this an easy task? I'm still looking for a guide on how to do this..

---

### Post by Bachstelze on 2007-05-19
Yes, it's very easy :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

written by me, by the way ;)

---

### Post by mahiyar on 2007-05-19
HymnToLife's howto is very easy, I have done it myself and it works (thanks HymnToLife, now that I know whom to thank), just do not forget to look in to the details of your mounted directory as is instructed.

---

### Post by kh4nh on 2007-05-19
boot with your ubuntu live cd,
at the terminal prompt, type:
```
1. sudo grub
2. find /boot/grub/stage2
this will return something like (hd0,2). 0 if grub is on your first hard drive, 1 if it's on the second hard drive. 2 if grub is on the second partition of that hard drive, 3 if it's on third and so forth. Once you found that:
3. root (hd0,2)   # set (hd0,2) as the location of the boot directory
4. setup (hd0)   # write MBR of the selected hard drive
5. quit


```

---

### Post by kohl62 on 2007-05-19
I used "Super Grub Disk" to fix my grub problems.  Can't remember where I downloaded it from, but do a search for it.  You just burn it to a disk (as on ISO, i think) and boot it up.  Was the easiest way I found to restore Grub.

---

### Post by true_friend on 2007-05-20
[Super Grub]("http://supergrub.forjamari.linex.org/?section=download")

---

### Post by ector on 2007-05-20
Thanks all for the responses. 

I tried a few fixes but none of them seemed to work..? I then tried to restore the MBR through "Super grub disk" but that didn't work either. I'm sure I'm probably just missing some minor detail. At least for the time being I'm able to boot up Ubuntu through the super disk until I get more time to troubleshoot.

By the way HymnToLife great guide, it is written very well :)

---

