---
title: "Installation Issues"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by TomRiley on 2007-04-17
I am trying to run desktop 6.10 on an older Dell PowerEdge 1300 with PIII 550 and 256MB of memory. The hard drives are 9GB SCSI set in RAID 1. This was a server we used for our office running NetWare. I want to try Ubuntu without using any of my production machines. I formatted both drives with the SCSI utility, dowloaded, validated and burned the image. The install hangs with a Buffer I/O error hdc. I've tried F6 at the opening screen and adding acpi=off, as well as Boot_Debug=2|3 from another post. Using that it now hangs at mounting the drive and then goes into the Buffer I/O errors. I'm not sure where to go and wonder if my problem is attempting to use a server as a desktop. Thanks for your advice.

---

### Post by nudnik on 2007-04-17
> **TomRiley said:**
> I am trying to run desktop 6.10 on an older Dell PowerEdge 1300 with PIII 550 and 256MB of memory. The hard drives are 9GB SCSI set in RAID 1. This was a server we used for our office running NetWare. I want to try Ubuntu without using any of my production machines. I formatted both drives with the SCSI utility, dowloaded, validated and burned the image. The install hangs with a Buffer I/O error hdc. I've tried F6 at the opening screen and adding acpi=off, as well as Boot_Debug=2|3 from another post. Using that it now hangs at mounting the drive and then goes into the Buffer I/O errors. I'm not sure where to go and wonder if my problem is attempting to use a server as a desktop. Thanks for your advice.

It could very well be that the nature of your hardware is causing the problem. Ubuntu does some interesting things on an old Compaq Presario with similar specs to your server that I use as a jukebox , although it does install and run.

Fedora Core 6 comes to mind. I might give that a try.

---

### Post by dstew on 2007-04-17
When you say the install hangs, do you mean that you can run the Live CD fine, but when you go to install it hangs, or that the Live CD doesn't run? If the Live Cd does not run, you can also try the boot options **noapic** and **nolapic**.

With an older system like that, you might do better with the Alternate Install CD. It installs the same Ubuntu system, but in text mode. Another thing to think about is using Xubuntu. The slow speed of your processor might give you some problems with the Ubuntu desktop.

You can find the alternate install .iso [here]("http://releases.ubuntu.com/6.10/").

---

### Post by juantovarm on 2007-04-17
Due to the specs of your computer, you should try Ubuntu server edition or Xubuntu or Fluxbuntu. They are more lightweight.

---

### Post by tstockma on 2007-04-17
I'm not sure yuor hardware is the problem.  I'm still struggling with my own first attempt to install, but I'm finding out some verrrry interesting things...

The "default" installs on the LiveCDs, including the alternate, simply don't work for some machines. 

The "f6" option brings up a generic load command, not one tailored for your machine.  In my case, it's been bringing up "._size=1048576" as a parameter...but up until late yesterday, I only (like you) had 256MB RAM, and I'm bettin' that ._size= calls for a GB...

And I just got off a post somewhere offsite that criticized Ubuntu's install CDs for inadequate documentation.  Once you hit "f6", hit "f6" again to _really_ enter the custom-load-parms area.  Now _that's_ perhaps a suprisingly useful tidbit of information...

Personally, I'm now on a quest to find adequate documentation of the various load parameters, so maybe I can gain control over this damn thing...I have yet to get the LiveCD load of the linux kernal to come up in anything other than command line mode, and I don't yet have knowledge to use that to execute GRUB or install any version of Ubuntu from there...

Good luck!

PS  I think that once properly configured, your hardware will do fine.  Here's that offsite article I mentioned, he has a fairly comparable system:  [http://www.serverwatch.com/stypes/servers/article.php/17181_3619676](http://www.serverwatch.com/stypes/servers/article.php/17181_3619676)

---

### Post by TomRiley on 2007-04-17
Thanks for the help. I downloaded the Server Image yesterday, and attempted to install it as suggested above. It shows the Linux Kernal is 100% loaded and stops. I think I may forget this and try another version. Thanks again.

---

