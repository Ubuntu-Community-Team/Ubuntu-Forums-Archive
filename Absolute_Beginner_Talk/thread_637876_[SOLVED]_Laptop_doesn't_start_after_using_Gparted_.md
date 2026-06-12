---
title: "[SOLVED] Laptop doesn't start after using Gparted -help!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Narv on 2007-12-11
Hi, when I was upgrading from feisty to gusty I accidentally ended up with both versions, which made the latop run slow.

Someone on the forums suggested I burn a live CD of gparted to delete one of the partitions (my laptop isn't connected to the net).  That worked fine, I deleted one and expanded another.  But when I restarted the machine it just said:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

And that's all it does.  I can't even type anything.  I've tried restarting it with the gparted CD in, and even a Live CD of ubuntu, but nothing works.

Can anyone help me please??!!!

Please don't say I've killed my laptop!!!!

---

### Post by Don1500 on 2007-12-11
Your GRUB is gone. you can use Super GRUB to fix GRUB. Load the live CD (ISO File) from the internet.

[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

---

### Post by logos34 on 2007-12-11
you don't need to download SGD (although it is a nice utility to have around).

Simply use your ubuntu live cd to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Don1500 on 2007-12-11
Logos,
I was trying to find that link, but I thought SGD would be something Narv should have anyway.

Also, it sounds like Narv may have to fix the original MBR of the disk first (fixmbr.exe in windows), The SGD will do this.

---

### Post by logos34 on 2007-12-11
> **Don1500 said:**
> ...but I thought SGD would be something Narv should have anyway.

Also, it sounds like Narv may have to fix the original MBR of the disk first (fixmbr.exe in windows), The SGD will do this.

yeah, agreed on first point...might be a good learning experience to use SGD.

I think overwriting the existing grub on the mbr should do the trick without having to fix anything, but I could be wrong

---

### Post by Don1500 on 2007-12-11
Agreed
(I always like to see my other system (windows) start again when I lose grub. Just for the warm and fuzzy that I didn't really screw it up):lolflag:

---

### Post by Narv on 2007-12-12
Hi, thanks for all your replies.

I burnt a Live cd of super grub, but it doesn't do anything.  I'm left with it just saying 

Grub loading, please wait...
Error 22

It's the same when I put in the ubuntu live cd, it just stays saying the same thing.  I can't type anything either.

Is there some way I can manually tell it to boot from the cd?

---

### Post by zabien1970 on 2007-12-12
It sounds like you may be booting off the hard drive first, on my dell laptop when I restart for a second when it first starts I can hit f12 toenter the boot menu (yours may be different, watch closely when it starts) once there I can change the settings to boot from cd first, let us know if that helps

---

### Post by schmildo on 2007-12-12
(Zabian beat me to it.)

It sounds like your BIOS isn't booting from the live CD at all, I'd go into the BIOS and double-check that it's booting from CD.

I a similar problem once, and I'd already ensured that the CD was the first boot device, but I (for some reason) was still unable to boot from the CD.

I ended up going back into the bios, and upon finding out that i wasn't allowed to remove the HDD from the boot sequece decided to teach it a lesson.

I reached down and pulled the IDE cable out of the HDD, and ripped out all my USB flashdrives.

I then rebooted, and 'THIS' time it worked. (as the only bootable drive left in my system was a CD)

(Yeah I've had my fair share of BIOS issues hehe)

---

### Post by Narv on 2007-12-12
Thanks everyone!!!

Yeah, when I told it to boot from the multibay first rather than the hard drive I could use the ubuntu live cd to add grub in a terminal (I actually thought I'd already told it to boot from the multibay, but apparently not).

I'm a complete newbie and I could never have done that without all your advice.

Thanks so much!

---

### Post by zabien1970 on 2007-12-12
Glad we could help, if you could go to thread tools at the top of this page and mark this solved, we'd appreciate it.

---

### Post by schmildo on 2007-12-12
So grub's going now? Good, here are some guides for fixing it just in case:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub)

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)


Good luck!

---

