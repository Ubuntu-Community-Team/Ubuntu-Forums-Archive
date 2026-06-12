---
title: "Upgraded my MBP to OSX Yosemite which took over boot. Need tool update GRUB"
date: 2015-03-26
forum: Apple Hardware Users
---

### Post by swarup on 2015-03-26
I've got a dual boot set up on my MBP with OSX and Ubuntu. Upgraded to OSX Yosemite this morning, and the OSX OS took over the boot so that GRUB is no longer active. I found out that if I can get into Ubuntu once, then in a terminal window doing "sudo update-grub" should re-establish grub. And there is a bootable usb software Super Grub2 Disk which will boot my into Ubuntu. But I've been trying for hours to make a bootable CD. My other Ubuntu computer (Startup Disk Creator) gives an error when trying to do it. And in OSX the Disk Utility does not recognize the software and will not make the bootable USB. The same is happening with another software by same group, called Rescatux. Unable to make bootable USB.

Is there another tool for getting booted once into Ubuntu? Or any other guidance on how to get GRUB active again so I'll be able to boot into Ubuntu?

---

### Post by este.el.paz on 2015-03-27
> **swarup said:**
> I've got a dual boot set up on my MBP with OSX and Ubuntu. Upgraded to OSX Yosemite this morning, and the OSX OS took over the boot so that GRUB is no longer active. I found out that if I can get into Ubuntu once, then in a terminal window doing "sudo update-grub" should re-establish grub. And there is a bootable usb software Super Grub2 Disk which will boot my into Ubuntu. But I've been trying for hours to make a bootable CD. My other Ubuntu computer (Startup Disk Creator) gives an error when trying to do it. And in OSX the Disk Utility does not recognize the software and will not make the bootable USB. The same is happening with another software by same group, called Rescatux. Unable to make bootable USB.

Is there another tool for getting booted once into Ubuntu? Or any other guidance on how to get GRUB active again so I'll be able to boot into Ubuntu?

@swarup:

I had this same issue, upgrade from 10.9.2 to 10.9.3, that "wiped" the GRUB install and I couldn't boot Xubun 14 install.  And, I had the SG2 CD already burned so I thought I had it in the agbay . . . but, trying all of those "recovery" methods did not fix the problem.  So, that was my personal experience, not a top hand on the CLI, but, I just went for the "nuke n pave" and reinstalled into LM17.  It was just easier to do that than spend even more time trying to fix the situation.  I use "manual" and I create a small 10 MB partition in front of the ext4 partition, labeled as "bios_grub" . . . if I don't, the installer says "GRUB install successfully" but, no GRUB.  I'm also using rEFInd, and a recent "security update" in 10.9.3 broke the rEFInd "blessing."  Fortunately booting the option key still shows my 4 disks and will boot into any of the choices . . . linux shows as "windows."  Rodbooks site shows how to "rebless" but other things to do.

But, don't know why you are having problems burning a CD of SG2, I believe I used my '10 MBPro to burn the iso, drag n drop the iso into the left lower side of the DU window . . . a "line" appears as the iso image is dragged over the spot, then highlight the image, and click the Burn disk tab . . . should be "good to go"??????

e...

---

