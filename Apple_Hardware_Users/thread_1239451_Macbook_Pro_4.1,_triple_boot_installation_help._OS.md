---
title: "Macbook Pro 4.1, triple boot installation help. OS X, 7, and Jaunty"
date: 2009-08-13
forum: Apple Hardware Users
---

### Post by XanderVincent on 2009-08-13
I've been struggling with this for the past few days now. I have a Macbook Pro 4.1 with Leopard and Windows 7 on it, and can't figure out for the life of me how to have 7 and Ubuntu both installed on it. 

I tried following the OS X, Vista, Ubuntu and OS X, XP, Ubuntu guides but neither of those worked.

The problem I'm having is that if I follow the directions layed out here [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) it just doesn't work. 

It says to partition Windows as large as you want both Ubuntu and Windows to be, I do that... partitioning 170GB for Windows, with refit already installed and working properly. Then when I am going through the installation if I try to partition the drive windows is on it removes windows and installs Linux in its place. That was from following this step.. "Install Ubuntu by partitioning the boot camp drive that Windows is located on, and install both Ubuntu and GRUB bootloader onto the new partition."

Maybe I'm partitioning that part Windows is on to the wrong type? The directions don't really say how to format it, even though there are a ton of options. 

I'm thinking maybe the problem lies in Windows 7? Because when going through the 7 installation it won't let me install it on the partition labeled "Boot Camp" because it's the wrong type. Then I have to delete it and just create a new one for 7. 

Sorry, I'm just looking for a way to run all three of these and it's getting very difficult for me because I can't find directions anywhere that include 7.

Help?

---

### Post by hajk on 2009-08-13
You may want to invest some effort in trying to understand what you're doing instead of just following some recipe in a wiki... 

The problem with any multiple OS installation on an Mac involving Windows is that it (Windows) assumes to be the only OS in the world, so a trick is needed to let it work with other OS-es that use the same old MBR partition table. That trick is to first install Windows in a BootCamp partition that is large enough to hold both Windows and GNU/Linux; second, the Windows partition must be whittled down to create room for GNU/Linux; third, GNU/Linux is installed in the space thus created. Steps two and three cannot/should not be reversed.

The above works fine with XP (see the wikis), but I don't know if that whittling down can be done in Windows 7, and if so how to do that.

You may wish to look into grub-efi, which gives a means of booting GNU/Linux from any GUID partition, internal or external, so bypassing the whole BootCamp/Windows/legacy MBR problems. This will require some fortitude on your part. Start with that most active thread in this forum...

---

### Post by XanderVincent on 2009-08-13
Yeah. I managed to previously do this in XP and Vista. I just can't figure out for the life of me how to shrink down my 7 installation at the partition menu when installing Ubuntu.

---

### Post by hajk on 2009-08-13
No, don't do it when installing Ubuntu, but do it from within Windows using some tool like PartitionMagic. This may have to wait until such a tool becomes available that can handle this for Windows 7 (assuming that Windows 7 allows this). That's why the grub-efi route may be the better one, but this will require a bit of effort on your part... but isn't that part of the fun of running a SOTA OS?

---

### Post by Anorexic Leader on 2009-08-22
I have the same model MBP as Xander does, and Refit worked for me, but I can't seem to find the guide I used. I know a guy who helped me do it too, so I'll have him look for the link as well, but it really wasn't as complicated as it seems that you are making it out to be.

Good luck man. Just remember that it is possible.

---

### Post by XanderVincent on 2009-08-22
I finally got it to work for me. I don't know why Ubuntu kept not seeing 7 even though it worked, and 7 kept removing Refit from OS X... somehow. Had to reinstall Refit a bunch of times until I got it all working out.

I shrunk OS X down to 20GB (I never use it), and created a partition in the OS X Boot Camp like all the wiki's I've seen for Vista or XP. But, it never would work. If at the 7 install screen I even broke it up to use only part of it, or if I used all of it.. installing Ubuntu would see 7 as not an operating system and would just see it as a huge storage partition of all the remaining space, no matter what size I made it.

What I had to do was shrink OS X down in Boot Camp and then run a live version of Ubuntu and use the partition manager in that. Then if I created the 7 partition there it would think I created a Vista one. Then I installed 7 on that and during the Ubuntu install it finally saw 7 as the correct size and an operating system (saw it as Vista, haha), so I finally had a partition to install Ubuntu on.

That's how I had to do it.

Shrink OS X
Create partitions with Ubuntu in live mode
Install 7
Then install Ubuntu. 

=) So yeah. Solved.:)

---

### Post by leaded on 2009-09-10
I don't know if this has been documented yet, but as someone who recently set up Snow Leopard, Windows 7, and Ubuntu 9.04, here's what I did:

0. 1 Partition with Leopard
1. Upgraded to Snow Leopard over top of Leopard (no clean install)
2. Run Boot Camp Assistant to allow 45 GB for Windows
3. Rebooted to a GParted Live CD
4. Resized 45 GB to 30 GB for Windows 7
5. In the newly freed up 15 GB, created an ext4 partition for Ubuntu
6. Installed Windows 7 on 30 GB.** During the early stages of the install, I ran advanced and formatted the 30 GB partition which made it NTFS
7. Installed Ubuntu 9.04 64-bit, chose Advanced disk partitioning, chose the 15 GB partition and specified the / mount point
8. rEFIt working great!

** - I initially tried Windows 7 64-bit on a MBP3,1 but after having to reburn the iso image a different way (extracting the boot image, using ImgBurn to create new ISO, Google it :)), I only discovered that Apple's 64-bit drivers are not supported on my machine. Tonight I found an Apple support article stating the exact models that support Vista 64 and mine is not one of them. So I went back and installed Windows 7 32-bit. (For those wondering, I have legitimate licenses for both through uni).

---

