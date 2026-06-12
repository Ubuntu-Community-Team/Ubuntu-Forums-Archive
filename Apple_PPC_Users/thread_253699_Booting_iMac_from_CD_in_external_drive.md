---
title: "Booting iMac from CD in external drive"
date: 2006-09-08
forum: Apple PPC Users
---

### Post by k49 on 2006-09-08
I tried to boot up my iMac DV+ (a G3 from 2000 that usually runs Mac OS 10.3.9) from the Ubuntu 6.06.1 CD in an external Iomega CD drive via FireWire (the internal drive is broken). This didn't work; holding down the 'c' key has no effect, and the computer starts Mac OS X from the hard drive. I know the Ubuntu CD is okay because it works on other computers (e.g. a PowerBook G4 boots from it with no problem), and I know there's nothing intrinsically wrong with booting from a CD in the external drive, since a Mac OS X install disk works fine. 

If I hold down the option key while starting up, the Ubuntu CD shows up on the list of available startup disks (as a CD icon with a penguin and a FireWire symbol), but I still can't boot from it that way: if I select it, the CD drive makes noise and a white screen shows up for about a second; then I'm back to the same startup disk menu, except for slight weirdness with the colors. If I then try to select the hard drive from this menu to start up in Mac OS X, the white screen returns and nothing happens.

I did try the various tips offered to people with similar questions, but they didn't work for me. When I type "boot cd" in Open Firmware, I get the response "can't OPEN: cd", and resetting the PRAM with command-option-P-R has no effect either.

I think the problem must be with the external CD drive, but it seems to work fine for all other purposes. Any suggestions?

---

### Post by linear on 2006-09-09
It takes a bit of work to boot Linux from an external Firewire drive. See this post for some info: [http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5](http://www.ubuntuforums.org/showpost.php?p=498516&postcount=5)

---

### Post by k49 on 2006-09-10
Thanks for the link, but I can't even get to the point where I'd be able to follow those instructions. I don't have Ubuntu installed anywhere; I would need to boot from the CD, or at least get to the screen with boot options, before I can do anything at all.

I am assuming the problem is the lack of a Linux driver for the CD drive (Iomega says they don't support it on Linux), so there's no way I can boot from the drive, or even use it if I managed to install Ubuntu on the hard drive by other means. I need a CD drive, so I assume I can't install any sort of Linux--correct me if I'm wrong.

---

### Post by linear on 2006-09-10
Looked at this again and realized I pointed you to info about booting from installed Linux on external firewire HD.

Still, booting from a firewire CD is also a problem, and I haven't seen a solution.

Installing over a network might be an alternative. (Don't have any information about this, though.)

---

