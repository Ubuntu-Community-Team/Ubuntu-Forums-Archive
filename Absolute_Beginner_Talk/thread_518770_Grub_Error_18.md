---
title: "Grub Error 18"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-08-06
I had a perfectly functioning dual-boot system on my stepson's pc.  He was playing in Ubuntu for the first time, and messed up the installation.  We just decided to re-install it, as there wasn't really anything to lose.  

I've reinstalled it, and now get this error on reboot:
GRUB Loading stage1.5:

GRUB loading, please wait...
Error 18

I'm not sure what step to take.  As I said, it was working fine before the reinstall.  Any suggestions, please?  I haven't seen this before, and the searches I've done, aren't promising.

Thanks.

---

### Post by mike102282 on 2007-08-06
I have only seen this when I uninstall a Linux distro and windows is the only one there did Ubuntu write the MBR when you reinstalled?

---

### Post by thefoolisme on 2007-08-06
I don't know if Ubuntu wrote the MBR.  I would have thought so, as I didn't do anything different from my usual install.

---

### Post by thefoolisme on 2007-08-06
I tried reinstalling GRUB from the live CD using this:  [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but it didn't work.  Can anyone help?

---

### Post by philinux on 2007-08-06
Found what 18 means,
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

But in order to help what is yout machine spec and what version of windows was it running.

---

### Post by Jimcanoa on 2007-08-06
> **philinux said:**
> Found what 18 means,
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

But in order to help what is yout machine spec and what version of windows was it running.

Hmmm, I don't think the problem is the motherboard. If his computer was working fine and he hasn't upgraded the firmware or anything, I don't see why it would be that.
I ran across error 18 not too long ago. In the end it was because the hard drive had failed and there were bad blocks everywhere. We had to throw away the HD and buy a new one. I managed to recover the data using dd_rescue and dd_rhelp.

Just to make sure you HD is free of bad blocks, why don't you boot up with a Live CD! and check the filesystem for errors with fsck?

---

### Post by psusi on 2007-08-06
Try booting from the livecd and using gparted to remove the existing partition, THEN reinstall.  

If that still doesn't fix it, try installing with a separate /boot partition at the start of the disk.

---

### Post by thefoolisme on 2007-08-06
I'm sure it's not the motherboard, as the system hasn't changed since last weekend when it was working.  I would think the same would be true of the hard drive, but I am more than happy to run fsck.  All I get back from the run is:

fsck 1.39 (29 May-2006)

I don't know what that means.  I could try a reinstall, but I'm not sure what putting a /boot partition at the front will do when it was working last weekend as it's installed.  It seems as though it didn't like it when I deleted the old partitions and reinstalled it this time.  Everything else is the same.  Do I have to reinstall everything, meaning windows and Ubuntu?  

Trust me, my stepson has learned his lesson about leaping before doing research.  He can't use his system at all at the moment.  :-)

---

### Post by thefoolisme on 2007-08-07
So, can anyone help with this problem?  I'd like to get it fixed today, and I haven't had much success with searches.

---

### Post by psusi on 2007-08-07
If the error 18 is to be believed, your motherboard can not boot from further than the first few gigs of the hard disk.  When you reinstalled, the new copy of the kernel may have happened to land too high up for the bios to reach, which is why you are now getting the error 18.  Having a /boot partition at the start of the drive would resolve that.

As for fsck, try fsck -f to tell it to actually check the disk.  Always a good idea to man new commands you aren't familiar with.

---

### Post by thefoolisme on 2007-08-07
> **psusi said:**
> If the error 18 is to be believed, your motherboard can not boot from further than the first few gigs of the hard disk.  When you reinstalled, the new copy of the kernel may have happened to land too high up for the bios to reach, which is why you are now getting the error 18.  Having a /boot partition at the start of the drive would resolve that.

As for fsck, try fsck -f to tell it to actually check the disk.  Always a good idea to man new commands you aren't familiar with.


Why would the kernel have landed higher than the first few gigs?  That doesn't make any sense to me, especially since I'm reinstalling it on the same machine it was running a a week ago.  But ok, say it did.  Won't putting a /boot partition at the start of the drive mess up windows (not that I can get to it right now anyway)?  From my research, I always thought windows wanted to be first.  Plus, would that mean reinstalling everything? I was trying to avoid that by seeking help here.  

I was hoping someone had seen this error before, and could save me having to reinstall everything (windows and linux).  I'm pretty sure if I reinstall it just as it is now, it will work fine, without a boot / in the front or anything.  I think it's the reinstall that the system didn't like for some reason.  I figured there had to be someone out there who's done the same thing.  


BTW, I'm probably going to feel stupid, but what does "man new commands" mean?

---

### Post by psusi on 2007-08-07
man is the manual reader program.  Run man fsck to see the manual for the fsck command.

---

### Post by thefoolisme on 2007-08-07
I appreciate the explanation about the "man".  

Can anyone help me with my Error 18 problem?  Just as a brief recap, it is an error that is showing up after a reinstall on the same machine it was on previously, with the same dual-boot setup for Windows XP, etc.  The only thing that changed is that my step-son really messed up Ubuntu in his first blind run-though.  I know what the error 18 traditionally means, but it's not so in this case, or at least wasn't 2 days ago.  I really think it has to do with the reinstall, but I don't know what to do.  

I really thought someone out there would have seen this problem before.

---

### Post by Jimcanoa on 2007-08-07
Did you check your partition with fsck, then? It's important to know if the HD is damaged, because if it is there's nothing much we can do... 
Running fsck is pretty straight forward, bootup with a liveCD of your choice, Ubuntu LiveCD!, Knoppix, Gentoo, it doesn't really matter which one. Open a terminal execute:
```
fsck /dev/... 
```
where /dev/... means the name of your linux partition i.e. something like /dev/sda1 or /dev/hda1 
You can find out which one it is by running:
```
fdisk -l
``` 
If you need help finding out which one it is, post your "fdisk -l" and we'll tell you.
By the way, don't forget to execute all of the above with sudo, or in a root terminal (executing "su -" )

---

