---
title: "Problems installing after wiping disk, iMac, RAM dead?"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by lemonbar on 2008-10-22
A friend of mine found a Blueberry iMac by a dumpster, and I decided to load Dapper on it.  I installed 640 MB RAM, burned some iso's, printed a ream of instructions from the forums (thanks guys:KS) and the installation (after several tries and much troubleshooting) went fine - got a desktop, an install icon, got to step three (keyboard layout) and got an error - no room on partition.  I had installed with the alternate for Heron (had trouble with xorg.conf - no section "Modules" and no refresh rates to change - the file was missing pretty much everything I needed to change - tried it a couple more times just in case), the desktop for Dapper, the original MacOS 9.04 was still on the disk, and everything was in a new partition. 

The drive was almost 8GB total and there must have been at least as many partitions.   After several tries I ran dban (Darik's Boot and Nuke) because it wasn't like there was anything on the computer I wanted to keep, right?  I wiped the disk clean.

Now everything is slo-o-o-ow.  I think I killed my RAM or something.  I can get the Dapper live cd started, but it takes forever and I can't get it to the install button.

I have no Mac software...

---

### Post by lemonbar on 2008-10-23
So I guess what I'm asking is, did I wipe whatever programming makes the RAM functional?  It seriously slowed down, and I'm not sure how to make everything go again.  The desktop loads to a point, and then it feels like nothing is happening.

I tried to do an alternate install so that it isn't so image heavy, and got an error that says my cdrom isn't recognized. I'm using the cd-rom to install the software.  There is so much I don't know about computers...

I can be more specific when I get home from work.  At this point is this more of a hardware issue, and should it be moved elsewhere?

---

### Post by Frak on 2008-10-23
IIRC, That's a Bondi Blue iMac with a 500-MHz PowerPC (Single) w/ 64MB initial RAM (you upgraded), ATi Rage 128 Pro, and a CD-RW drive.

I'd think it'd be a bit slow as it is, also considering the drive is a bit slow (24x). I'd recommend possibly upgrading the processor. That should help out a lot.


Question
When you boot, do you hear the bong/bell/sound?

---

### Post by oswaldkelso on 2008-10-24
opps wrong thread.

---

### Post by stream303 on 2008-10-27
> **lemonbar said:**
> got to step three (keyboard layout) and got an error - no room on partition.

With those early boxes, you are running into an 8gb partitioning limitation that root (and the special apple partitions) can't go beyond, and the Ubuntu partitioner doesn't know about that firmware limitation.

You may want to try manually partitioning it so that root is under 8gb, typically 7 to 7.5 gb to be safe, and dedicated the rest of the disk manually.

What I do is allow the system to calculate the partitions, then using the "go back" feature, delete what it thinks should be root and swap, and manually tell it to make root 7 to 7.5 gb, dedicate the rest as the /home partition, and allow for 2x ram for swap.

That 8gb firmware limitation (and 128gb limitation on some later machines), has reared it's ugly head on me more than once. :)

---

### Post by Frak on 2008-10-27
I use the ATA Hi-Cap driver. I have the 128GB limit (though it is possible to force higher through a firmware script.)

---

### Post by stream303 on 2008-10-28
I think I forgot to mention that on an old machine like that, be sure to burn the ppc release iso image as an iso, on CD-R, and at very low speeds like 1X or 2X.....

---

### Post by lemonbar on 2008-11-03
I hear the startup chimes.  It's newer than a Bondi - I got the specs, and it's a G3, Blueberry, 400Mhz - 1999, and I'm not sure, but I don't think the drive is RW.  

I was able to get the desktop icon the first several times I tried to install with the Live Dapper, but there was always one thing or another that made me try to re-install.  Instead of overwriting the old stuff (which I assumed was going on), it made new partitions (I think).  I figured that if I wiped the whole disk, I could start clean, but I think I might have screwed something up.  I used dBan (Darik's Boot and Nuke), and cleared it.  It slowed down horribly when I tried to re-install, and the alternate gave me a message that it couldn't identify my cd drive, even though it was the drive running the cd.  Again, so much I don't know about computers. 

I've been burning my iso's as slo-o-o-o-wly as allowed.

I'm trying again with the Dapper Live cd - I have a mouse pointer on a plain maroon background right now...waiting for an install button...waiting... 

Last time it shut off entirely after that screen.  I'm going to try the alternate again if this doesn't work.

Um...I salvage computers sometimes, but I'm sort of learning as I go - upgrade powerpc processor?  Tell me more:)

---

### Post by Frak on 2008-11-03
[This]("http://www.sonnettech.com/product/harmoni_g3.html") is the best I can find for the Blue/Flower G3 (you probably may have mistaken the blueberry for the Blue/Flower. The Blue/Flower version is technically superior.)

The manufactures instructions are the best to follow.

---

### Post by tiresia on 2008-11-03
I would definitely try to install with an alternate-CD.
You can have a look here for some information

[Where to download Ubuntu for PowerPC and other frequently asked questions]("http://ubuntuforums.org/showthread.php?t=427714")

You can download Hardy here
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
:::::::::::::

As said in the other posts, check the integrity of the image (md5sum), and burn it as slow as you can. 
If you have another Mac, use Apple Disk Utility, if you are burning it on Linux, run your burning-program as root.

Before starting the computer, remove extra PCI-cards, if any, and reset the PRAM (cmd+opt+P+R).
At the yaboot-prompt type video=ofonly, to avoid video problems.

:::::::::::::
**INTREPID**
You can even try to install the last Ubuntu version, Intrepid.
Here you can see, where you can download it
[http://ubuntuforums.org/showthread.php?t=963868](http://ubuntuforums.org/showthread.php?t=963868)

It is very probably, that you get a similar message, telling you that your CD-ROM was not detected. Here is a solution for this issue
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by lemonbar on 2008-11-04
Thank you - this was very helpful.  I used disk setup from a copy of OS9 to initialize the disk, reset the PRAM, and successfully installed Edgy with the alternate. Everything is back up to speed. 

I wanted to update from there, but software update was no go.  Firefox worked, so I had an internet connection, but I couldn't upgrade anything.  I tried to do an alternate install with Intrepid, got through the cd-rom problem, and the machine clicked off after the reboot.  I tried again, this time using cli-install, and this time I didn't have anything in the xorg.conf file.  

I'll try some other stuff, and if I have a "Eureka" moment, I'll share.  Thanks for all the help:)

---

### Post by tiresia on 2008-11-04
If it worked, you can try again to install Edgy, and then make an upgrade (maybe to Hardy)
Here you can see how to do it
[http://ubuntuforums.org/showthread.php?t=964208](http://ubuntuforums.org/showthread.php?t=964208)

Before upgrading, if you xorg.conf file works, make a backup```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If you have problems after the upgrade, you can restore the file that worked for you

---

