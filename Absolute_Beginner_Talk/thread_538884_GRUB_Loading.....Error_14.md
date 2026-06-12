---
title: "GRUB Loading.....Error 14"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by empiremonkey on 2007-08-30
Help, my Ubuntu pc will not boot anymore

getting this:-

GRUB Loading stage1.5

GRUB loading, please wait...
Error 14

pc then pauses, not key press will work except ctrl-atl-del.

any ideas ?

can it be fixed or do i need ot reinstall ?

Thanks

---

### Post by llamakc on 2007-08-30
What were you doing prior to this problem happening? Have you messed with the partitions? Installed another O/S alongside Ubuntu? Moved drives around physically in the box?

---

### Post by Magneticgravity on 2007-08-30
Have you a Xp disc?

---

### Post by empiremonkey on 2007-08-30
I just switch the pc on after being off for a few days.

it was working fine when i switched it off.

Yes, i do have an XP CD- Rom, why, can this help ?

---

### Post by dstew on 2007-08-30
This can be fixed, but we need more information. To fix the computer, you will need to be able to boot a working Linux system from a Live CD. That will allow us to look at the grub-related files and repair them, or even re-install grub.

Was your system working before? What did you do before it stopped working?

---

### Post by LowSky on 2007-08-30
I just had this error, my hard drive failed. had to replace it.

I hope your problem  isn't this case

---

### Post by empiremonkey on 2007-08-30
I have the live cd and it will boot form that and load ubuntu.

The last time i used the pc was a few days ago. it was working fine and i powered it off via "switch off" in ubuntu.

I come back a few days later and i'm getitng this error 14 message.

---

### Post by Magneticgravity on 2007-08-30
Have you XP installed on your harddrive?
This happened to me, dont worry, i was playing around with my partitions.
Put the Xp disc in, press 'R' for recovery mode, then press '1' which will ask you for your password, just press enter.
Then enter 'fixmbr' and press 'y' to confirm.
Now im sure this basically wipes linux because you can no longer boot up to it, but for me i didnt mind, because i was new to it completely. If you want to do this, then delete the partitions in while in your xp disc as well which has Linux on, then, making sure you have a LiveCD before hand, reinstall Ubuntu.

But thats only if you need to, there might be another way.

---

### Post by empiremonkey on 2007-08-30
would like to avoid having to reinstall ubuntu, if possible

There was no XP partition on the disc.

---

### Post by Magneticgravity on 2007-08-30
OK, so do you have XP installed, and did you do anything the last time you were on Ubuntu, like deleting partitions or anything at all.

Im not sure what other way there is, but have faith, someone might come along and know soon.

---

### Post by empiremonkey on 2007-08-30
XP was not installed on PC, no XP partition, only ubuntu on a single partition spanning the whole hard disk.

I only powered pc off, did not touch partitions or anything.

now it won't get passed this error 14. 

Is there a utility to fix ? 

Does the live CD have any utils on it ?

---

### Post by empiremonkey on 2007-08-30
just booted from live cd, and ran gnome partition editor

it says:-

unalbe to mount the volume

mount:wrong fs type, bad option, bad superplock on /dev/sda1, missing codepage or other error

it's not looking good......any ideas ?

---

### Post by Magneticgravity on 2007-08-30
At the moment i dont know what to suggest if you dont want to reinstall Ubuntu. Googled it?

---

### Post by atlien on 2007-08-31
I'm not an expert or even advanced but I have had booting probs before and I found a program called Super Grub.  Google it and download it since you obviously have access to another computer.  The program has repaired my bootloader several times, now.  The documentation talks a lot about having Windows on the hard disk as well but ignore all that.  It will fix your Grub whether or not a Windows issue is involved.  You will need a CD or USB to use the program in repairing your Ubuntu GRUB.

Super Grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I am not an expert by any means but this has worked for me.

Oh.  And it is free.

---

### Post by b0ng0 on 2007-08-31
I have had this problem before and same as you, it just happened out the blue.

I'm pretty sure it's fixable, if you boot using a LiveCD you should be able to check your partitions and grub files, maybe post some of the details up.

When I had this problem I formatted my harddrive and have not had that error since.

---

