---
title: "Can't boot without a CD..."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by bambaman on 2008-01-01
Hi!
I've switched to ubuntu 7.04 few months ago (from XP). Everything was great, untill I've upgraded my whole computer except for the hard disk (which is pretty new too).
Since then, when I turn it on I get the message "No bootable device - insert boot disk and press and key".
The BIOS recognizes the hard disk (320 GB). I tried several live-cds:
_Ubuntu 7.10:_ doesn't recognize the hard disk (when I open gparted I get "no devices found")
_Ubuntu 7.04:_ same as ubuntu 7.10. But since the third time I tried it, in the middle of the booting process I get the message "/bin/sh: can't access tty; job control turned off" (I tried "safe graphics mode and still the same message)
_Ubuntu 6.06:_ recognized the hard disk, I can see how much space is available in every partition, but I can't mount. I can still the OS though, and did it a few times, but I still get the "press any key" message.
_Knoppix 5.10:_ I can only boot from it using the cheat-code "knoppix xmodule=vesa", but it mounts the hard drive and I can see my files :)

Few days ago I tried "super grub cd" and I was able to boot into my (re-installed and downgraded) linux! I tried the grub fixing option, and it says that everything is fixed but I still get the "press any key" message.
I tried many grub re-installation methods, to no avail. I actually messed it up and I need to use the ubuntu 6.06 CD, reinstall the OS and use the (awesome) "super grub cd" (running Knoppix right now).
I am really tired+frustrated of trying to fix this... what is the problem? can it be a hardware problem? Any help would be appreciated.

Ofir

P.S. : some last notes:
specs - 2.2 Ghz dual core intel processor E4500, 2 GB RAM, Geforce 7300... I don't really know where to check the rest in Knoppix.
All my data is on a partition other then the root partition, I don't care about formatting the other partitions (including erasing "/home").
I had some other problems in the past which may or may not be related:
- I couldn't boot into my XP installation after installing ubuntu (but I didn't care)
- I had problems upgrading from ubuntu 7.04 to 7.10 and I had to downgrade (some important packages couldn't be installed)
- When I first installed ubuntu, I had a grub error (can't remember the number), which I solved by creating a "/boot" partition in the beginning of the hard disk, probably because my old motherboard couldn't deal with a big partition as the first partition. But know, the "/boot" is inside the root partition "/" (that is the first partition).

---

### Post by arochester on 2008-01-01
Have you examined the boot order in the BIOS? It needs to boot from the Hard Drive first and not the CD-Rom.

---

### Post by bambaman on 2008-01-01
Thanks, but I think that it boots from the hard drive first. When I enter the boot options, I have a normal mode and an advanced mode. The normal mode is weird, but in the advanced mode I set the hard disk as the first device. I also tried to set the BIOS to deafult options a few times. And when it gives the "press any key", the CD-ROM light doesn't flash (and when I press a key, it takes about 20 seconds until it gives the message again).
And what about ubuntu 7.xx not recognizing the hard disk and the "can't access tty" error?

Is it possible that the problem may have something to do with IDE\SATA cables? (it's an IDE HD, with a motherboard with mostly sata cables) Is it worth opening the computer up?

---

### Post by LordTyrans on 2008-01-01
I have had hard drive problems before, so things to check.

Your hard drive + dvd rom might be in some sort of raid configuration look for raid settings in your bios and set them as normal drives.

Check to see if the switch position on your dvd-rom drive is set to slave not master( there is usually a diagram on the underneath of the drive stating witch position is which) I believe This does not apply is it is a sata drive.

If the only problem is just your disk drive and it does also not work under win-dose then i suggest you just buy a new one as they are only around £20 for a good r-w drive now anyway.

Hope that helped

---

### Post by bambaman on 2008-01-05
I found out what causes the problem - I unplugged the DVD and was able to boot from hard drive and everything was great :) when I plug it back, I can only but from the DVD drive and not from the hard drive. I put another old DVD instead of the new one and had the same problem... I also updated the BIOS and it didn't help.
So.. is the problem in the IDE cable? or is it possible that both DVD's are damaged? or something else?

---

