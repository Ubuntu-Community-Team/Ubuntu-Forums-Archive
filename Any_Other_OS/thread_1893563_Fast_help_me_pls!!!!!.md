---
title: "Fast help me pls!!!!!"
date: 2011-12-10
forum: Any Other OS
---

### Post by alfamuzjak on 2011-12-10
i had dual boot win7 and ubuntu 11.04... i wont to install xp insted of win7, because i have 1GB ram, nvm.

So i insert installation of xp and after i was asked to "press any key to boot.." it started and say "setup is detecting hardware confi... or smth like that" but there wasnt next step with formating and installing, just black screen.

So i tryed to format that drive(*i have 2 disk: local c: and local d:,win7 was on C: *) -drive c: with ubuntu disk utility with NTFS option, then i update grub *sudo update-grub*.

And still i didnt get further than "setup is detecting hardware conf...."

HOW CAN I NOW INSTALL XP?
PLEASE HELP ME AS FAST U CAN

---

### Post by N00b-un-2 on 2011-12-10
I would recommend that you boot up a Live CD and use GParted for your partitioning, even if it's just wiping an already existing NTFS partition.  I've run into instances where partitions created using linux tools though do not play nice with Windows, in which case you may want to try formatting the partition you intend to use as FAT32 or FAT16 in order to get it recognized by the XP install disc.  If all else fails, I've had 100% success rate installing Windows on NTFS partitions created by the Windows 98 SE install disc, provided your BIOS can emulate IDE on SATA (assuming your computer is new within the last few years).
I realize this solution doesn't help unless you have a copy of Win98SE but any good hacker should if for no other reason than formatting drives.
Once you format the drive as FAT32 or NTFS using whichever method you choose, try booting up the XP disc again and see if it detects your hard drive.
If XP doesn't recognize that your computer has a hard drive at all, chances are your install CD lacks SATA drivers.  Sata Drivers were included with SP3, but if you have a XP install disc with SP2, you will need to slipstream the drivers into the ISO using an application called [Nlite]("http://www.nliteos.com/").  You will also need an application to rip the CD as an ISO and then burn the modded one.  I would recommend IMG Burn if you're on Windows.  If you are using Linux, Nlite will work using Wine.
Hope that helps

---

### Post by alfamuzjak on 2011-12-10
Thanks for helping but I didnt understand anything...i only have now installation of win sp2,sp3 and win7...Only thing i care for now is data on that local disk d:...do you know any way which will disable/delete ubuntu and let me install fresh xp..(i can install ubuntu later)

Or what do you think about inserting win7 at running ubuntu...and start instalation...do you think win7 will kill ubuntu grub...
What are consequences?

---

### Post by N00b-un-2 on 2011-12-10
If you are trying to recover data from the hard drive before partitioning, just boot up an Ubuntu Live CD and follow the instructions I wrote in this post [http://ubuntuforums.org/showpost.php?p=11091991&postcount=16]("http://ubuntuforums.org/showpost.php?p=11091991&postcount=16")

I think that should cover it.

---

### Post by N00b-un-2 on 2011-12-10
if you are asking whether it's possible to install windows 7 while booted in Ubuntu, no.  That's a silly question.  You can't even install Windows 7 while booted into Windows, you have to reboot and start from the CD.

If you are asking whether installing Windows will overwrite GRUB, the answer is yes.  Always.  You must reinstall grub after installing Windows, period.  These instructions work fine. [http://www.lancelhoff.com/restore-grub2-after-installing-windows/]("http://www.lancelhoff.com/restore-grub2-after-installing-windows/")

---

### Post by deonis on 2011-12-10
You have to add SATA drivers for your HDD to the XP installation CD. In another words you have to prepare your own respin of XP to install it on your PC. Here is some info: 
[http://www.londatiga.net/it/installing-windows-xp-on-acer-travelmate-6291-laptop/](http://www.londatiga.net/it/installing-windows-xp-on-acer-travelmate-6291-laptop/)

---

### Post by darkod on 2011-12-10
Also, did you ever have XP installed on this computer before? Depending how old it is, and if it came with win7, it might have sata mode set to AHCI in bios. Not sure if XP plays nice with AHCI even with drivers, or you have to set it to IDE.

There might be a problem with your XP CDs too. Usually even if the HDD is not discovered because of missing sata drivers, at least the installer is shown and it says no disk found. You say that the screen goes black during hardware detection.

In any case this is related only to XP, not ubuntu. And if you have ubuntu running on that computer still, I wouldn't remove it yet because it might be the only way to access your data (and the option to run the ubuntu cd in live mode).
You can't run windows in live mode to get the data.

---

### Post by alfamuzjak on 2011-12-10
I have bunch of times xp and win7 installed on this computer. i have athlon dual core 4400+,1GB ram...as i sayed i have several installation cd's and all cd's work fine trust me. i buyed my computer few years ago (5 i think) and he comes with xp...

I hope this will negate some of the proposition. (sorry for my english, it is not my native)


P.S. I think that there isn't problem with sata drivers, because it is not first time that i installed any system, my computer is same...didnt change any component except keyboard or mouse. but it is first time i have ubuntu on real system. (dont get me wrong but it is just my opinion, which dont mean that im right)

*Last edit: [http://ubuntuforums.org/showthread.php?t=1873200](http://ubuntuforums.org/showthread.php?t=1873200) * - this is my post few weeks before i tryed to install

---

### Post by nothingspecial on 2011-12-10
Moved to Other OS/Distro talk.

---

### Post by alfamuzjak on 2011-12-11
I succeded!...Thank you guys for help!

---

### Post by N00b-un-2 on 2011-12-12
congratulations.  what did you end up doing in the end?

---

