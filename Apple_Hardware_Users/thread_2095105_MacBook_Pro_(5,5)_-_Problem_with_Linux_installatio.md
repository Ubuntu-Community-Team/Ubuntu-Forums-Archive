---
title: "MacBook Pro (5,5) - Problem with Linux installation"
date: 2012-12-15
forum: Apple Hardware Users
---

### Post by RandAlThor on 2012-12-15
Hey there

I've been trying my luck by searching through the net and trying a few different distributions.
So far i haven't had any luck - seems to me like i am nowhere near installing Linux successfully.

Since i cant remember how many different Versions i tried I'll describe the 3 that stuck the most to me.

I installed rEFIt and it works (as far as i can tell - i can see the refit menu and whatnot)
My partitions always looked like this (with some experimenting by giving boot an own little partition)
fat32 200 MiB EFI
hfs+ 233 GiB Macintosh HD
hfs+ 620 MiB Recovery HD
(that was the mac part, now for the new linux parts)
5 MiB bios_grub
ext4 228 GiB /
linux-swap 3.75 GiB
Selected root / to install the bootloader to
Also tried with own partition of 500 MiB mounted at /boot to install the bootloader to

Linux Mint 14:
With this version I couldn't get the Install-USB to work: "couldn't start x server (your graphical userinterface)"
after some not really successfull research i dismissed this one alltogether

Linux Mint 13:
The  installation went without any problem. After the installation i let  rEFIt update the Partition Table and tried to start Linux.
Well... I'm hanging at a black window with a white bar blinking in the top left corner.
I've  something about nomodeset and some other grub boot options but i wasnt  able to get there. (neither with tab, nor shift, nor e nor f6 nor f12)

Linux Ubuntu 10.04
Had the same problem as with Linux Mint 13

Sometimes i had 2 or even 3 Linux showing up in the rEFIt bootloader O.o


Guys I seriously need help.
I'm at my wits end.

PLEASE pity me

Sincerly, Shard

PS:  Im sorry if i missspelled anything or had a bad grammer. English is not  my native language and it's been a while since i wrote it / spoke it  the last time.


Edit: now it's showing a new trick: when i try  to start from the refit menu it goes to a screen with the linux pengium  in the middle and freezes up

---

### Post by RandAlThor on 2012-12-16
*bump*

---

### Post by mörgæs on 2012-12-16
Please don't bump a thread.

If you feel that you don't receive enough answers it could be because the question was not posted in the Mac forum. Moved it for you.

---

### Post by zaebo on 2012-12-18
I do pity you. :(

Did you worked accordingly to a tutorial?
Maybe you missed a step?

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

I do remember trying Mint 13, but experiencing a differnt problem
regarding grub and EFI.

---

