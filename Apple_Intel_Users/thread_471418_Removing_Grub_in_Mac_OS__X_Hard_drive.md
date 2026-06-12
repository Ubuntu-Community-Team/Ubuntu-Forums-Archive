---
title: "Removing Grub in Mac OS  X Hard drive"
date: 2007-06-12
forum: Apple Intel Users
---

### Post by kitki83 on 2007-06-12
Trying to get myself confused as I write it down basically I installed Ubuntu in partition on a hard drive that has Windows XP.


I erased it because I somehow had two Ubuntu hard drives and Windows XP boots only to Ubuntu. So basically Grub is in the Mac OS X MBR so how can I clean that out? (do not know if this helps but I did install rEFIT)

---

### Post by ronocdh on 2007-06-12
> **kitki83 said:**
> Trying to get myself confused as I write it down basically I installed Ubuntu in partition on a hard drive that has Windows XP.


I erased it because I somehow had two Ubuntu hard drives and Windows XP boots only to Ubuntu. So basically Grub is in the Mac OS X MBR so how can I clean that out? (do not know if this helps but I did install rEFIT)
Well I believe that OS X uses GPT instead of MBR, as it's an EFI configuration, not BIOS. So OS X pretty much ignores any content on the MBR. Have you seen anything that indicates otherwise? If you want to get your MBR back in order for that WinXP installation, boot from the WinXP installation disc and try the **fixmbr** command.

---

### Post by kitki83 on 2007-06-12
Thats the thing, Windows XP (Hard drive 2) is cleaned. What I did is remove hard drives from Mac Pro that don't relate to my problem to avoid a mistake. Having only Windows XP Hard drive, the computer Booted showing only Windows and loaded Windows not giving me GRUB text spam. Second reboot, I put Windows XP(Hard Drive 2) and Back UP (Hard Drive 3). No Extra Windows Boot Icon. Then I took those two out and left Mac OS X (Hard Drive 1) and it shows Mac os X and Windows. The Windows takes me to the GRUB text spam(Just repeats GRUB across the screen). So really my problem is with Mac OS X. How can I clean that out so I can start fresh again.


Thank you


PS. Did fix MBR with Windows XP SP2 Disc.
Boot Screen I am referring to this [img]http://www.applelinks.com/images/uploads/charles/bootcamp_bootscreen.jpg[/img]

---

### Post by ronocdh on 2007-06-12
> **kitki83 said:**
> Thats the thing, Windows XP (Hard drive 2) is cleaned. What I did is remove hard drives from Mac Pro that don't relate to my problem to avoid a mistake. Having only Windows XP Hard drive, the computer Booted showing only Windows and loaded Windows not giving me GRUB text spam. Second reboot, I put Windows XP(Hard Drive 2) and Back UP (Hard Drive 3). No Extra Windows Boot Icon. Then I took those two out and left Mac OS X (Hard Drive 1) and it shows Mac os X and Windows. The Windows takes me to the GRUB text spam(Just repeats GRUB across the screen). So really my problem is with Mac OS X. How can I clean that out so I can start fresh again.


Thank you


PS. Did fix MBR with Windows XP SP2 Disc.
It surprises me that fixmbr didn't solve your problems, but let's keep trying. If you are OK with really "starting fresh again," perhaps it would be best to just insert the OS X DVD and reinstall everything. Before you proceed with the installation, you may want to load Disk Utility and reformat the drive; OS X should in this process adequately prepare the drive for installation of OS X, which I believe would entail wiping even the MBR of the drive.

Good luck, and please post back with your results.

---

### Post by kitki83 on 2007-06-12
Is there similar option to reset MBR for Apple. Since its not Windows with GRUB but the Mac OS hard drive.

I really do not want to reformat my Mac OS X because of the software settings and what not.

I been reading on Windows XP theres two options for fixing MBR

Fix /mbr

fix /boot
whats the difference?

---

