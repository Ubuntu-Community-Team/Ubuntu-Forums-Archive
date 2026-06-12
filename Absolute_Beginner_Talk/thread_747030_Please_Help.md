---
title: "Please Help"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by thayle on 2008-04-06
_**Don't tell me to look it up because thats all I've been doing!**_

I have "2" hard drives. Two 160gb hard-drives set up in RAID-0 (making one 300gb). And one 1TB hard-drive which I just got today. The one set up in RAID-0 has Windows on it, and I was dumb and have all my files and the windows on one hard-drive, I have no partitions. 

Alright so, I have tried to install Ubuntu on the 1TB hard drive, and I am able to install it, but then when I have the system reboot GRUB has Error 21. I'm pretty sure this is because of RAID or something, but continuing...

I switched the 1st Hard-Drive to the one with Ubuntu, but when I do that it hangs on a black screen with that little blinking white line thing...

Also I should tell you that when using the LiveCD I have to go into safe graphics mode or it doesn't work... 

Anyone able to help? If not I think I'm going to give up on Linux this is way to much...

_EDIT: Please be specific with your explanations on what to do. I had never used Linux in my life until the other day._
_EDIT (2): I have also done the exact same thing with Kubuntu and the exact same thing happened..._

---

### Post by thayle on 2008-04-06
Ok so heres what i think is the only way to get it to work. Reformat the hard-drives and get rid of the RAID. Then repeat everything I did before only this time it works... Unless it really is something with the video card...

My video card: NVIDIA GeForce 6800 XT

---

### Post by kaivalagi on 2008-04-06
> I switched the 1st Hard-Drive to the one with Ubuntu, but when I do that it hangs on a black screen with that little blinking white line thing...

Also I should tell you that when using the LiveCD I have to go into safe graphics mode or it doesn't work... 

Have you tried changing the "splash" option to "nosplash" in the /boot/grub/menu.lst file? I am not sure whether you will have a problem with the splash screens and a 6800 card...

You can do this temporarily by hitting F6 I think in the grub boot menu and editing the the option you want to boot, you can then change "splash" to "nosplash" for that one boot to see whether it will fix things.

Atleast after trying this you know whether you'll have to reformat and install again or not :)

---

### Post by ugm6hr on 2008-04-06
I don't have RAID, so I'm not 100% certain.

From [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)
> 21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

My suggestion:

With the new 1TB HD as 1st HD, reinstall Ubuntu on it.  Leave the RAID as it is.

I think what has happened is that GRUB has been installed on hd0 (default for Ubuntu), which was the RAID when you first installed.

For some reason, GRUB then couldn't find hd1 (the new 1TB device).

If you have swapped the 1TB to primary device, it should now be hd0, with GRUB and Ubuntu installing on the same device, it should hopefully be less problematic.

Make sure both drives are enabled in BIOS too.

---

