---
title: "Noob install of Ubuntu, can't boot Windows XP"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by daou on 2006-06-27
Hi everyone.
I finally got the linux bug (after almost getting it for about 3 years) and decided to install Ubuntu. After using it for an hour, I've already fallen in love with it.
As good as it is, I'm not ready to give up Windows yet. The problem is the GRUB loader won't boot my XP properly. I get the following (and not surprisingly familiar) error from windows:

"NTLDR file is missing."

What I think happened was that GRUB recognized my old installs of windows xp and probably windows 2000 that haven't existed on my hd for a couple years. The hd is in bad shape anyway and had to install Ubuntu twice because of corrupted filesystems.

Another option is that GRUB isn't recognizing my Raid 0 setup where my Windows XP is installed. At least the Ubuntu installer recognized them as two separate hds and not as one continuous block.

Is there anyway of editing the boot options from GRUB to direct it to the correct location for Windows or do I need some raid drivers?
(My raid, however, is hardware based and loads from BIOS right after powerup so I'm not sure if drivers will help)

Thanks in advance.

---

### Post by woedend on 2006-06-27
[http://www.computing.net/windows2000/wwwboard/forum/60792.html#](http://www.computing.net/windows2000/wwwboard/forum/60792.html#)

check out that page.  Its old and for win2000, but if you see, one responder points to a website that has a winxp pro boot disk with the file.. You can try booting from it at least.

---

### Post by Breezy Badger on 2006-06-27
you want to make sure windows is installed first and that ubuntu is on a seperate HDD or partition

---

### Post by shoot2kill on 2006-06-27
i had a similar problem, when looking through a forum for advie on how to read other HDD's, i was told to write

```

hdd1, hdd0
hdd0, hdd1
```

in a certain file (sorry cant remember wich file)

and i got the error,,, if u have done this, remove it...

---

### Post by woedend on 2006-06-27
/boot/grub/menu.lst?

---

### Post by daou on 2006-06-27
I already had an existing Windows XP install on a separate hdd.

This is my hdd layout:

2 Samsung 80 GB (RAID 0, NF4 controller) -> existing Windows XP install
1 Maxtor 160 GB -> new install of Ubuntu

> and i got the error,,, if u have done this, remove it...
i haven't done that.
but if this is similar to (or the same thing) as GRUB's map command, I've seen the advice around and probably will try it.

Is there a command that lists all installed OS's on hdds with their locations, types, etc. so I could check if GRUB is trying to load WinXP from the right location?

---

### Post by Chandu on 2006-06-27
If you have altered the partitions there is a probability that you need to change the boot.ini file of your XP installation to reflect those changes.

You need to change the partition number in the following

multi(0)disk(0)rdisk(0)partition(1)

if you know the exact number put it in place of partition(1). i.e, 

multi(0)disk(0)rdisk(0)partition(xx)

otherwise try to put 1....9 once at a time and reboot everytime to test your luck....

---

### Post by shoot2kill on 2006-06-27
[QUOTE=woedend]/boot/grub/menu.lst?[/QUOTE]
yes, that was the file... it took me ages to find it and remove the code.. :(

but i got the NTLDR message when i modified this file, so check that file, see if all ok.. ^ ^ ^

---

### Post by daou on 2006-06-27
> If you have altered the partitions there is a probability that you need to change the boot.ini file of your XP installation to reflect those changes.

I haven't touched the partitions of the hd where WinXP is located. I installed Ubuntu on a new hd to (ironically) isolate it from any linux related stuff.

---

### Post by daou on 2006-06-27
Does Ubuntu rewrite the MBR of Ubuntu root hd to point to GRUB? Because I've configured my BIOS to boot first from the RAID array where WinXP is, but it loads GRUB nevertheless. If I disconnect the hd where Ubuntu is, I get an error 17 from GRUB:

> Error 17 : Cannot mount selected partition 
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

But why would the comp still try to boot with GRUB, unless Ubuntu rewrote the MBR of my separate WinXP RAID array as well?

---

### Post by shoot2kill on 2006-06-27
[QUOTE=daou]Does Ubuntu rewrite the MBR of Ubuntu root hd to point to GRUB? Because I've configured my BIOS to boot first from the RAID array where WinXP is, but it loads GRUB nevertheless. If I disconnect the hd where Ubuntu is, I get an error 17 from GRUB:



But why would the comp still try to boot with GRUB, unless Ubuntu rewrote the MBR of my separate WinXP RAID array as well?[/QUOTE]

the Grub information file is stored on your main HDD that your computer boots from, not on your seperate HDD that ubuntu is installed to

---

### Post by daou on 2006-06-27
Ok,

I decided that before any damage is done, that I should restore the Windows boot into the MBR and backup important stuff. Easy as typing fixmbr into the WinXP CD recovery console. Or should have been. Despite this, Grub still loads at boot.

How hard can it be to get rid of Grub?

---

### Post by Breezy Badger on 2006-06-27
wait...did you say you changed around some partitions or moved the drive order around?

---

### Post by daou on 2006-07-07
Everything works now. Had some delays because I had to backup everything and return a damaged hdd (after 4 days of HDD Regenerator ~30,000 bad sectors, and at 45/160 gigs checked). Installed WinXP and Ubuntu again a couple of times. Turns out that the Ubuntu install incorrectly wrote the boot options for Windows in Grub ](*,) and then I furthered the damage by trying to salvage WinXP with the recovery console. All I had to do was manually change some of the root and map options in Grub and got Windows to dual boot off Raid0 with Ubuntu.

At least I got a great head start at learning Ubuntu and Grub. 

The Ubuntu install might have detected an old install of Windows in the MBR of one of my extra hdds.

---

