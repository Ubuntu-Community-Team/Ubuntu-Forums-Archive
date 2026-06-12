---
title: "&quot;Succesful&quot; Boot-Repair still not booting properly"
date: 2018-08-23
forum: Apple Hardware Users
---

### Post by almartire on 2018-08-23
I recently installed Ubuntu Budgie 18.04 on an old 2007 MacBook (white plastic model A1181).-- 64 bit CPU w/ 32 bit EFI
I went through many forum posts about how to install Ubuntu 64 bit on these machines but seems way to complicated to jump through so many hoops for the intended purpose of this machine.  The laptop is to be used by my 11 yr old daughter in her homeschool curriculum.  So I feel like a simple 32-bit install should work just fine.

Computer specs: MacBook A1181, 4 GB RAM (installed), 3GB recognized, Intel Core 2 CPU T7400 @ 2.16GHzx2, Intel 945GM x86/MMX/SSE2 graphics.
OS: fresh install of Ubuntu (Budgie) 18.04.1 LTS.  I completely erased the 64GB SSD and installed Ubuntu as the ONLY OS (no macOS or Windows).

The install seems to be working very well.  Everything seems to work: graphics at native resolution, wi-fi, CD-rom drive, etc, etc.  Pristine!  Except, I notice a pattern that only EVERY OTHER boot sequence is successful. This is either a shutdown and power boot sequence or a restart.  Typically it hangs at a grey screen and sits for long periods before I manually have to hold down the power button and shut it off.  Then on the very next power up it will boot to the GRUB menu where I have the choice to select *Ubuntu, Advanced options, etc.

At least I know I can boot into Ubuntu every other time.  But it has to go through the GRUB menu, then the next time I KNOW I'm going to have to force power off before I can boot into the OS again.  Weird!

So I searched online and found the "boot-repair" utility which I ran and installed from the same live CD that I used to install the OS from.
It ran and said that the "boot was successfully repaired", but I did not notice any difference.  The same issue still persists.

If someone can help me get this boot issue resolved, my daughter and I would absolutely appreciate it!

The boot-repair report is attached.

---

### Post by oldfred on 2018-08-24
Moved to Apple sub-forum.

I do not know Mac.
But many with Mac use the rEFInd boot manager which seems to work better for some of those types of issues. Not sure if it works with your older Mac or not. Also do not think it works with BIOS type boot only UEFI.
       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 
    
From what little I have seen, it seems each version of the Mac needs somewhat different configuration. Old info, but newer Ubuntu should work better.
 [URL="https://help.ubuntu.com/community/MacBookPro"]https://help.ubuntu.com/community/MacBookPro

[/URL][https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)
       MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[URL="http://ubuntuforums.org/showthread.php?t=2157775"]http://ubuntuforums.org/showthread.php?t=2157775
[/URL]
 Boot Ubuntu from efi with Mac - post by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257) 
[URL="https://help.ubuntu.com/community/MacBookPro"]
[/URL]

---

### Post by francoisdelabre on 2018-10-08
I had an issue with a Macbook (late 2006) and Ubuntu 16.04, where boot was OK one every two starts.
On the second boot, the Grub menu had a 30 seconds timeout to choose an entry whereas the default is 10 seconds.


It seems Grub has a different configuration when it detects a previous boot did not succeed.
I had a look at the grub.cfg configuration file and it does different things when the "recordfail" attribute is set.
On my configuration, the difference was mainly on the GFXmode setting.


So I added the following line to the Grub configuration in /etc/default/grub to force the text mode :
GRUB_GFXPAYLOAD_LINUX=text


The grub configuration then needs to be regenerated with sudo update-grub


Hope this helps!

---

