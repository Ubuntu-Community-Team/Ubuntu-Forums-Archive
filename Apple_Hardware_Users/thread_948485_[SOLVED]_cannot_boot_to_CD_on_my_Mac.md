---
title: "[SOLVED] cannot boot to CD on my Mac"
date: 2008-10-15
forum: Apple Hardware Users
---

### Post by spkrck on 2008-10-15
As the title suggests, I cannot get my Mac booted to the ubuntu cd.
I have tried with 6.10, 7.04, and 7.10. None of them will boot.
I have a Quicksilver, G4 dual 1gig unit with 1 gig of ram. I can get the cd to list when I hold the option key down during boot, but when I choose it, it acts like it will boot, but return to the drive choice menu, but in a lower resolution. Does this over and over until I choose the OSX drive, then the computer has to be booted into safe mode once, in order to be able to boot back up normally. This is very frustrating. I used toast titanium to burn all 3 cd's from the ISO files. All disks were verified 100%.
if you think you have a solution for me, send me an email, or just leave a post.
Thanks,
Den

---

### Post by cyberdork33 on 2008-10-15
Try to burn the disk a slow as you possibly can.

---

### Post by Slowspeed on 2008-10-15
> **spkrck said:**
> As the title suggests, I cannot get my Mac booted to the ubuntu cd.
I have tried with 6.10, 7.04, and 7.10. None of them will boot.
I have a Quicksilver, G4 dual 1gig unit with 1 gig of ram. I can get the cd to list when I hold the option key down during boot, but when I choose it, it acts like it will boot, but return to the drive choice menu, but in a lower resolution. Does this over and over until I choose the OSX drive, then the computer has to be booted into safe mode once, in order to be able to boot back up normally. This is very frustrating. I used toast titanium to burn all 3 cd's from the ISO files. All disks were verified 100%.
if you think you have a solution for me, send me an email, or just leave a post.
Thanks,
Den

It might sound silly but did you verify that you downloaded the proper ISO file for a PowerPC? and not the X86 architecture?
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
Slowspeed

---

### Post by spkrck on 2008-10-15
Yes, I know it does sound silly, but that was a good suggestion. Yes, all three ISO's are for power PC. I am going to try to burn the disk as slow as I can, and see if that helps. What the heck eh? :-) I will post if that works.

---

### Post by tiresia on 2008-10-15
Have you got any extra hardware (USB-Card, Grafik - Card&#8230;)?
Remove it before start your Mac and reset the PRAM (P+R+Opt+Cmd)

---

### Post by spkrck on 2008-10-15
ok, I downloaded this- ubuntu-8.04.1-desktop-powerpc.iso
I wanted to be SURE I had the right version- PPC. I burned the disk at 3x, and it still does not boot. I had replaced teh superdrive with a nice sony dual layer burner, and had thought that might be the problem, but I can boot from any OSX disk, or OS9 disk. That leave that out. I have a SCSI card, and a USB 2.0 card that I had added to my computer. I will take them out and try again later this afternoon. Thanks to all that have posted, trying to help me. I am a network admin (out of work at the moment) and just want to get into something that will help keep my tech skills sharp. I am only a Mac user, and not a mac tech, so it gets even more fun at this point. :-)

---

### Post by Slowspeed on 2008-10-15
> **spkrck said:**
> ok, I downloaded this- ubuntu-8.04.1-desktop-powerpc.iso
I wanted to be SURE I had the right version- PPC. I burned the disk at 3x, and it still does not boot. I had replaced teh superdrive with a nice sony dual layer burner, and had thought that might be the problem, but I can boot from any OSX disk, or OS9 disk. That leave that out. I have a SCSI card, and a USB 2.0 card that I had added to my computer. I will take them out and try again later this afternoon. Thanks to all that have posted, trying to help me. I am a network admin (out of work at the moment) and just want to get into something that will help keep my tech skills sharp. I am only a Mac user, and not a mac tech, so it gets even more fun at this point. :-)

I configured g3 Imac a while back and I remember that there was a problem with the install routine which required some additional commands. I don't know if this was just limited to g3's and Feisty or all powerPC's. I do remember some outstanding people helped out on the forum and got me going. You could try another flavor of linux like Fedora or Suse as you are aware PowerPC's are only supported by the community now not Ubuntu.
Good luck.

---

### Post by jaw1959 on 2008-10-15
I have a G4 eMac that I use as a MythTV frontend, and I was unable to make any flavor of Ubuntu work on the machine (I tried 6.10, 7.04, and 7.10; 8.04 wasn't available at the time).  I tried various other distro's, including yellow dog and Fedora, until I found one that worked well, which oddly enough was Debian Etch (which of course, is what Ubuntu is based on).  I can't speak to just how well *everything* is supported, but I have network, sound, and video support.  I'm not sure if the CD-burner works, but I know it works as a reader.  I'm not sure if I have any hardware video acceleration of any kind working, but I can watch any SD content that I've tried on the 800mhz G4, with 256mb of ram.  It runs video better using VLC and MythTV on Debian than the same machine did running OS X 10.4. 

So I guess the moral of the story is that if you can't make Ubuntu work, keep shopping.  And I recommend Debian as a good distro to try next, especially if you like Ubuntu.

---

### Post by spkrck on 2008-10-17
hey, it's me, I'm back.
No seriously, I downloaded Debian Etch, burned the disk, and again, nothing. I downloaded the x386 version of Ubuntu for my laptop, burned it from the image with my Mac and the laptop booted into it just fine. I can get an OSX disk to boot on my Mac, just can't seem to get any Linux disks to cooperate. ANY help?
Thanks Folks!
Den :-)

---

### Post by tiresia on 2008-10-17
> **spkrck said:**
>  I have a SCSI card, and a USB 2.0 card that I had added to my computer. I will take them out and try again later this afternoon.

Have you removed those cards and reset PRAM / NVRAM [Command-Option-P-R keys]?

---

### Post by spkrck on 2008-10-17
> **tiresia said:**
> Have you removed those cards and reset PRAM / NVRAM [Command-Option-P-R keys]?

Yep, I did that to no avail. It's kind of frustrating, but I am sure that there is a way to get Linux on this box. When I got done resetting with the cmd-opt-p-r I held the C key down, and could see that cdrom light flashing, but it still wouldn't boot. Once I let teh C key go, it booted right into OSX. I even reset the pram, and then held the option key so that I could choose the disk I wanted to boot from, but all it did was return to the option menu in a crappy low res image. Had to reboot back into OSX so the system wouldn't get all crappy on me.
 I am still open to suggestions.
Thanks,
Den

---

### Post by spkrck on 2008-10-17
Another thing to add to this issue is, when hold down the O+F+CMD+OPT keys, and get into the firmware, I cannot list the directory of the cd. when I type dir cd:,\, or dir cd:\ I get the journal directory. This is telling me that the Mac's BIOS or what ever it's called in MAC land is not able to read the cdrom. I even took the SONY dvd burner out, and installed the original superdrive, just in case that was the problem.
Are we scratching our heads yet? I sure know that I am. LOL

---

### Post by MikeTheC on 2008-10-18
Make sure you're using Toast to burn an image based on the ISO disk image, not a disk of the ISO image.

FWIW, I ordinarily use Disk Utility to burn ISOs, not Toast. I've never had the least little trouble with it.

---

### Post by tiresia on 2008-10-18
> **spkrck said:**
> I even reset the pram, and then held the option key so that I could choose the disk I wanted to boot from, but all it did was return to the option menu in a crappy low res image.
If you see an icon with Linux, when you hold the option key, it means that Open Firmware detected the CD and tries to start from it. But most probably the CD was not correctly burned. How did you burn it? As you were suggested, burn it at very slow speed (with Apple Disk Utility)

As last resource, you can start and install also from a USB stick. Here you find more information
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html)

---

### Post by spkrck on 2008-10-18
> **tiresia said:**
> If you see an icon with Linux, when you hold the option key, it means that Open Firmware detected the CD and tries to start from it. But most probably the CD was not correctly burned. How did you burn it? As you were suggested, burn it at very slow speed (with Apple Disk Utility)

As last resource, you can start and install also from a USB stick. Here you find more information
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html)

Well, I had burned it at 1x with toast before. This time I tried it with the disk utility, at 4 x. The only difference is that when I held the C key down I did get the file folder image for a sec, and then it went right back to the OSX normal boot. I will read the url that you sent and see what that has to say.
Thanks,
Den

---

### Post by tiresia on 2008-10-18
Since you added a new drive to your computer, you could check your CDs with another PPC Mac.
Which of both is your Mac? Quick silver or Mirrored Drive Doors 
[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1ghz_dp_qs.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1ghz_dp_qs.html)
[http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1.0_dp_mdd.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_1.0_dp_mdd.html)
Support the new Drive CD-R and CD+R?

---

### Post by spkrck on 2008-10-18
For those of you who have been helping me struggle through this, I say THANK YOU! I have now been working in the open firmware. I can get Ubuntu to yaboot, but it still wont install. However, I was able to get the Debian Etch Disk to run the install. I got as far as setting up the partition when I decided to back out, and free up a whole HD, just so I don't loose anything.
The big thing in the open firmware was that I couldn't get it to read the cd. Well, just for the heck of it I started to run the dir command on all the ide drives, and there it was, the cd was being accessed as ide1. Once I discovered this it didn't take long to get things going. I will keep this thread up to date until I am successful.
Thanks again!
Den

---

### Post by spkrck on 2008-10-22
As my earlier post said, I was able to find the CD contents in the Open Firmware. I was finally able to boot from the newest Ubuntu release. However, instead of running install, I ran Live. I was then able to run the install from the live session. I am typing this from my new Ubuntu install while I am doing my updates!
Thanks to all who helped!
Den

---

