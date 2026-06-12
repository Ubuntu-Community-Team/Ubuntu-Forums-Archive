---
title: "Not booting.... :-("
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Atra_Phasma on 2007-09-30
Hello all,
I recently (15 minutes ago) decided I wanted to install Ubuntu on my Windows XP computer. I used G-:)parted to reallocate 30gb of unallocated space on my HDD. I made a 20GB ext3 drive, a 2gb swap drive, and a 7gb FAT32 drive for transfer between OS's. I put in the LiveCD for 7.04, and I manually edited partitions for install. Before the install was complete, I canceled it, because I decided I didnt want to install Linux right then. (bad choice). I tried booting, but got my mobo's boot agent.. I thought that was odd, so I put back in G-parted, and checked the Partitions. My Windows one was still there. I deleted all the partitions I was going to use for Linux and turned them back into unallocated space. I then tried booting into XP again, but yet again, got the boot agent. I tried manually booting from the partition in G-parted, but I got a message stating "Error when accessing disk" . I tried this again, and the "booting from partition 1" screen just froze there. I tried making a new NFTS partition to re-intall windows on, and then transfer the files from the other windows partition was on, but that plot was foiled once I got the the Product Key screen, it said my key was invalid, even though i took it directly off the back of my case and checked it twice. I also tried using the "repair drive" function on the WindowsXP CD, but hit yet another brick wall when it asked for an admin password. I typed in my password, but it said it was invalid. I tried this a couple of times, until the CD booted my from the repair function. Is there any way to get Windows to boot again without a total reinstall? Is there something like GRUB on the MBR that isn't allowing it to load? Did I make the HDD corrupt? will i have to get another Windows Product Key to reinstall if I need to do that?
Thanks so much to those who help!
Matt

---

### Post by Pumalite on 2007-09-30
Use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If there is still a windows system, maybe you can repair the MBR.

---

### Post by Atra_Phasma on 2007-09-30
Ok, Ill try that, but when I have downloaded and burned the ISO before, the CD hasn't booted.

---

### Post by Pumalite on 2007-09-30
make sure to do md5sum on the iso, burn as 'Image', and burn at 4x.

---

### Post by Atra_Phasma on 2007-09-30
Ok, burned at 4x, and am getting ready to go try it out! hope it works! (fingers crossed)

---

### Post by Atra_Phasma on 2007-09-30
using the Cd and the "Boot Windows" option, the CD just loops my back through my BIOS screen, and I end up back at the CD again. :-(

---

### Post by Pumalite on 2007-09-30
Get a Knoppix and take a look at your system: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it, it will mount all your drives/partitions automatically and you will have access to all your files. See what is left.

---

### Post by Atra_Phasma on 2007-09-30
could I do the same with U or Xubuntu?

---

### Post by Atra_Phasma on 2007-09-30
aww.... it will take forever todl this iamge with DSL.. :-( *begins*

---

### Post by Pumalite on 2007-09-30
Knoppix IS the best Live CD around. It's good to have around, period.

---

### Post by Atra_Phasma on 2007-09-30
aww.... it will take forever to dl this image with DSL.. :-( *begins*

---

### Post by Atra_Phasma on 2007-09-30
mmk.... starts DL. will you be here tomorrow?this could take a couple of hours.

---

### Post by Pumalite on 2007-09-30
Sure thing. I won't forget you.

---

### Post by Atra_Phasma on 2007-09-30
thank you! most people on other forums do just that!:)

---

### Post by Atra_Phasma on 2007-09-30
ok, just posting this for the sake of progress..... I used the Uninstall GRUB option on the SuperGrub CD, and also, after it did not boot then, installed a windows XP MBR. Still no boot

---

### Post by Atra_Phasma on 2007-09-30
so once i get the CD, (I will have it by tomorrow, what should I do, exactly?

---

### Post by Pumalite on 2007-09-30
Once you boot from it, see what you have and report back. You use the terminal. But also check /media and /mnt

---

### Post by Atra_Phasma on 2007-10-01
I have the Knoppix disk. checking some things out as I type.

---

### Post by Atra_Phasma on 2007-10-01
> **Atra_Phasma said:**
> using the Cd and the "Boot Windows" option, the CD just loops my back through my BIOS screen, and I end up back at the CD again. :-(
I have my Windows partition, according to GParted, and it is still intact.... i think. I'll wait until the LiveCD boots up to make for sure!

---

### Post by Pumalite on 2007-10-01
Let's see.

---

### Post by coolen on 2007-10-01
If you're not against reinstalling Windows, I'd create a fat32 partititon to copy personal data across. I wouldn't vouch for any Linux LiveCD being able to write to NTFS at this point.
The Super GRUB Disc has a FixMBR equivalent, which tries to restore Windows' bootloader. You Windows CD has this option in the Recovery Console, too.
Just wondering: did you shrink your Windows partition during this? If so, did you defrag first? You may have accidentally deleted some important files. In that case, I'm afraid their recovery is well beyond anything I know.

Personally, I'd pop in a Live CD, create a fat32 partition, and save whatever I can, then reinstall Windows. Well, I'd wipe Windows and install Ubuntu, but that's just me :)

---

### Post by Atra_Phasma on 2007-10-01
> **coolen said:**
> If you're not against reinstalling Windows, I'd create a fat32 partititon to copy personal data across. I wouldn't vouch for any Linux LiveCD being able to write to NTFS at this point.
The Super GRUB Disc has a FixMBR equivalent, which tries to restore Windows' bootloader. You Windows CD has this option in the Recovery Console, too.
Just wondering: did you shrink your Windows partition during this? If so, did you defrag first? You may have accidentally deleted some important files. In that case, I'm afraid their recovery is well beyond anything I know.

Personally, I'd pop in a Live CD, create a fat32 partition, and save whatever I can, then reinstall Windows. Well, I'd wipe Windows and install Ubuntu, but that's just me :)
I owuld have Ubuntu, and did for awhile, but I need windows for gaming, WINE just can't cut it. I did not resize the partition with windows on it at all, just merely created and deleted partitions in the unallocated space around the partition. I tried the MBR options in supergrub, but to no avail. Reinstalling Windows is also a no go, because when I tried that, my product key was invalid, as I had already registered with windows. If i really wanted to, i could wipe the HDD, or return it if it was corrupted, and then call Microsoft up, De-activate my Product Key, and start from anew. I just thought there might be a quicker fix to this, since that data is still there.

---

### Post by Atra_Phasma on 2007-10-01
My Monitor is "Out of Scan Range" for the Knoppix GUI. >.<. I'm guessing this means more hard work. I,Unfortunately,must depart once again. This problem must be quite annoying to those kind enough to help me as I have no time to dedicate to fixing it, or to talk, and I am pretty new to Ubuntu. But I would like to hope that they will still hold on as I try to get through this.... eh.... problem.

---

### Post by coolen on 2007-10-01
You can get the data off. That's the easy part. If you didn't resize your Windows partition, then everything should still be there.
I'm assuming you've tried reinstalling Grub, but I think that it's a bunch of Debian scripts that detect other OSes and set it up accordingly. Luckily, Knoppiz is Debian-based.
To get Knoppix working, you can probably boot in a safe graphics mode. Last time I used it (ling time ago) you got a nice little menu to help you with boot options. Check it, and try VESA mode or something similarly safe-sounding.

---

### Post by Atra_Phasma on 2007-10-04
ok, i can try that. Sorry for the rash inactivity, my schedule has been so busy, and conviniently planned around not getting on the computer... >.< . Once I get into knoppix, what am I supposed to do?I know it mounts my drives for me, but what next?(i havent tried getting on knoppix yet,asit is 5:56am, and I need to leave for class at 6.

---

### Post by coolen on 2007-10-04
I'm no expert on the specifics of installing Grub, but the following command might work:
```
grub-install (hd0)
```
If I understand it correctly, that should install Grub to the MBR of your first hard drive...and hopefully detect all your other OSes in the process.
You may want to double-check that, though.

---

### Post by Atra_Phasma on 2007-10-04
no... last time i had GRUB, it messed up my Windows... It "Forgot" Where Windows was..... I still am clueless as to why the HDD doesnt boot... i dont know if i should resize the Window sPArtition to fill the whole HDD or what..... Quite Frustrated at this point.

---

### Post by Atra_Phasma on 2007-10-04
Finally managed to reset XP Password with a bootdisk. Unfortunately for me... the recovery console is no help. It says none of my Windows Files are corrupted, I made a new MBR, I made a new Boot Secotr, but its still wont boot!

---

### Post by Pumalite on 2007-10-04
See if you can boot with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Atra_Phasma on 2007-10-04
ok, Ill try.

---

### Post by Atra_Phasma on 2007-10-04
Unfortunately, it loops me back to SuperGrub. I tried booting from Windows, and then the Partition, but it just loops back to the disk, like its completely ignoring the HDD. I checked the boot sequence, and my HDD is 1..... followed by floppy, followed by CD.

---

### Post by Pumalite on 2007-10-04
If you want to boot any CD, the CD has to be 1rst in the boot sequence in BIOS.

---

### Post by Atra_Phasma on 2007-10-04
no, in my BIOS, when it boots I can hit F11 to choose boot device. I choose CD so supergrub boots, and then tell it to boot windows. it reboots, and has the HDD as the main boot device, and then it loops me back to the CD.

---

### Post by Pumalite on 2007-10-04
Looks like your MBR is screwed up. Fix your Windows MBR with Super Grub, then boot Windows.

---

### Post by Atra_Phasma on 2007-10-04
looks like.... but I've"repaired" it so many times.. with SuperGRUB and the Windows Recovery Console! meh. I'll try it again.

---

### Post by Atra_Phasma on 2007-10-04
hmmmm Super grub seems to think there is an additional partition called NATRUAL that seems to have GRUB on it..... that might just be something that the program adds at the top...but I think not.... when i try to fix the boot of it it says there is nothing to do...

---

### Post by Atra_Phasma on 2007-10-04
and also when i try booting the partition (not windows) it goes straight to my Boot agent. :-(

---

### Post by Pumalite on 2007-10-04
This is very weird. You might have an 'extra' partition at the front of the drive or a corrupted one. If you can boot from Knoppix, post: sudo fdisk -lu from the Terminal

---

### Post by Atra_Phasma on 2007-10-04
oh wait... the thing at the top is part of the GUI of SuperGrub. When I try to activate the partitions of Windows, I get an error message, which i assume means its already activated....

---

### Post by Atra_Phasma on 2007-10-04
and if it must come to re-formatting.... will my CD key for Windows work on the same computer?

---

### Post by Pumalite on 2007-10-04
I'm not a Windows user, but from what I heard, it should. I would never trust Micro$%& for anything though.

---

### Post by Atra_Phasma on 2007-10-04
Amen Brotha!

---

### Post by Atra_Phasma on 2007-10-04
does U or Xubuntu have an option that lets me acess NTFS HDDs? or is knoppix the only one? I cant boot into knoppix, at least not in full graphics mode.

---

### Post by Pumalite on 2007-10-04
Ubuntu Live CD will also give you the option to access the drive or partition.
Check /media and /mnt, if not there, at the Terminal:
sudo mkdir /media/ntfs
sudo mount -t ntfs /dev/? /media/ntfs
Then go to /media and open ntfs
(? in /dev/? has to be replaced by your with appropriate dev)

---

### Post by Atra_Phasma on 2007-10-04
ok

---

### Post by Atra_Phasma on 2007-10-04
i do beleive i might back up to a flash drive, and then perhaps reformat... or i might stick it out for the weekend.... I'm sure there is a solution to this problem.

---

### Post by Atra_Phasma on 2007-10-04
hmmm... i might stick it out.... I can access and open all the files in Ubuntu... so all the data is fine.... just HOW do i get to it... *ponders*

---

### Post by Atra_Phasma on 2007-10-04
I backed up using ubuntu (i didnt know it could access NFTS File systems...) and am currently using Windows incredibly long, inferior formatting tool to format and install windows. one can only wait now.

---

### Post by Atra_Phasma on 2007-10-06
Woo! the Recovery console did not help at all, but thanks to ubuntu, i backed up, reformatted, reinstalled, un backupped..... (is that a word?) and now all's well.... i might try Ubuntu on an external drive, but no more partitioning for me!

---

