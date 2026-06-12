---
title: "Xubuntu won't boot if my hard drive is in"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-04-07
Right now, I have Windows XP on my hard drive and Xubuntu on my flash drive. When I have the flash drive out and the hard drive in, it boots Windows XP like it should. When I have the flash drive in and the hard drive out, it boots Xubuntu. However, when both are in the screen goes black, except for the word GRUB and a blinking cursor. It stays frozen like this, and any attempt to press a key just makes the computer beep.

---

### Post by mac.ryan on 2007-04-07
Is the HD external? If so, what do you have on your internal drive (if any?). Also, what did you install first (win or xubuntu)? If you installed xubuntu second, did you install when the XP drive was in? Did you configure the system for dual booting?

---

### Post by Sporkmaster on 2007-04-08
> **mac.ryan said:**
> Is the HD external? If so, what do you have on your internal drive (if any?). Also, what did you install first (win or xubuntu)? If you installed xubuntu second, did you install when the XP drive was in? Did you configure the system for dual booting?

1) The HD is internal.
2) N/A
3) I had Windows first
4) No
5) Huh?

---

### Post by mac.ryan on 2007-04-08
GRUB is the **GR**and **U**nified **B**ootloader, it is the program that - just after you switch on your computer - gives you the choice about which of the various installed operating system you want to use for your session.

Grub has to be installed in order to work: normally it writes an instruction on the master boot record (MBR) of the first HD, telling where to find the actual GRUB program, that has a "table" of the various available systems.

A system that is configured for dual (or triple, or quad...) booting normally has GRUB installed.

From my understanding of your symptoms, it seems like you have no Grub installed (or you have a broken installation), so that the boot simply happens when the bios find a "bootable devices" connected to the bus, rather than opening a grub menu. While some kind of conflict seems to happen when the two bootable devices are both inline.

OTOH, Grub typically install the command "run grub" on the first (in your case XP internal) HD's MBR, while the grub itself is in the /boot/grub directory of your GNU/Linux media (in your case the flash drive), thus a typical grub installation would require both your media to be all the time plugged in when you boot.... but is this a possibility for you?

A possibility that I would also try would be - when both devices are plugged - to exclude from the bios setting one of the two from the boot list... if it works that way, you might avoid to install GRUB.

A third possibility (but this is an opinion, I never tried to do it myself!) might be to force the GRUB software installation on the same HD than windows, so that you could have the MBR and GRUB on the same (internal, all the time plugged in) media, and you could then select to boot ubuntu only when the flash drive is plugged in... However again: I never tried to do it myself, so I am not sure it would work.

Related links:[LIST=1]
[*][Installing grub]("http://ubuntuforums.org/showthread.php?t=224351") from liveCD
[*][Repairing the MBR]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true") from XP recovery CD (in case a grub installation gets broken)[/LIST]**Please note that playing around with grub can make your system non-bootable at all.** This doesn't delete your data or system installations from the HDs and _can be reversed_, yet it might be frustrating... so be sure to have all the needed tools described in the link #2, before to get into experimenting...

Final note: there is also a way to fix the MBR from ubuntu LiveCD, but at the moment I couldn't find the link for you.

Best luck!

---

