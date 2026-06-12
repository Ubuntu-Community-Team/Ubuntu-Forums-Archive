---
title: "Remove GRUB and just use rEFIt"
date: 2010-07-21
forum: Apple Hardware Users
---

### Post by metroidnemesis13 on 2010-07-21
I have OS X, Ubuntu 10 x64 and Windows 7 x64 installed on my Macbook Pro new unibody.  Right now when I choose Windows or Linux in the rEFIt boot menu both options take me to the GRUB menu, and I can boot everything but it's a bit redundant and annoying.  Anyone able to help me fix this?

---

### Post by hyper84 on 2010-07-22
BUMP...Looking for the same answer. I just have OSX and 10.04 32-bit though. I went through the rEFIt documentation on their website and I think that say to copy some files into the efi folder in OSX but they don't give specifics and talk more about LILO than GRUB and I don't want to screw something up.

---

### Post by conundrumx on 2010-07-23
rEFIt is not a boot loader, so no, you cannot "just use rEFIt."  Something has to boot Linux.

As far as the original poster, unfortunately the Mac has to put Linux and Windows in the same pretend legacy environment, so they share a MBR.  There is probably something you can do (perhaps try restricting the GRUB install to the Linux / partition?), but I can't give a definitive solution.

---

### Post by labaom on 2010-07-23
You can't get rid of Grub but you can make it "disappear" from the boot.

Go in terminal and write..

sudo gedit /boot/grub/grub.cfg

scroll down where it says 

timeout=10

and make it 0 instead of 10 that way it will automatically chose the first option of booting into Ubuntu.

---

### Post by conundrumx on 2010-07-23
Might want to make it 1 instead, so you have the option of mashing the down arrow should something go horribly awry.

---

### Post by labaom on 2010-07-23
> **conundrumx said:**
> Might want to make it 1 instead, so you have the option of mashing the down arrow should something go horribly awry.

That wouldn't do anything. Besides the other options are useless if you have refit. Besides reinstalling Ubuntu is fast.

---

### Post by conundrumx on 2010-07-23
> **labaom said:**
> That wouldn't do anything. Besides the other options are useless if you have refit. Besides reinstalling Ubuntu is fast.

Single user mode?  Memtest?  Booting an older kernel if one is borked?  Setting the timeout to 1 second instead of 0 means you can stop grub from autobooting if you're quick.  It's always nice to have recovery options without needing an install disk, and it costs nothing.

---

### Post by H264 on 2010-07-29
> **conundrumx said:**
> rEFIt is not a boot loader, so no, you cannot "just use rEFIt."  Something has to boot Linux.

As far as the original poster, unfortunately the Mac has to put Linux and Windows in the same pretend legacy environment, so they share a MBR.  There is probably something you can do (perhaps try restricting the GRUB install to the Linux / partition?), but I can't give a definitive solution.

This does not work, though in rEFIt you can select the linux partition to boot. Once control is handed over to GRUB, it fails. Donno why, it seemed to have worked before on an older release. 

I just got a shiny new 2tb hard drive and installed it in my iMac, been playing around with different boot configurations and it seems GRUB really does not want to work... if you uninstall rEFIt and just use GRUB you cant boot OSX unless you hold down the alt/function key (perhaps the X key too)

looking at the installer a bit more carefully, I noticed you can make an "EFI boot" partition - anybody know what this does and what its for? I cant seem to find anything about it online.

---

### Post by H264 on 2010-07-30
Alright, I got it, finally, though the process is a bit of a pain.

1.
resize OSX partition with bootcamp assistant to whatever size you want to keep OSX at.

2.
boot into Ubuntu live CD/DVD and use Gparted to delete everything but the first two partitions (which will be a 200MB or so EFI partition for OSX, and the OSX partition) then use the freespace to recreate one partition in fat32 for windows to be installed on (will be resized again later)

3.
install windows (I was using XP) to that drive space that was freed up

4.
boot into Ubuntu live CD and use gParted again to resize windows giving yourself some free space for Ubuntu.

5.
while technically still step 4, this part is very important...
define your linux partition right after the windows partition, then finally define your swap partition at the end of the drive

5.5 checkpoint
after applying the partitions in step 5 with gParted, your partitions should look something like...
/dev/sda1 EFI FAT32 | /dev/sda2 HFS+ OSX | /dev/sda3 NTFS windows | /dev/sda4 EXT4 (for linux) | /dev/sda5 SWAP
if you want a separate /boot partition, put it between SWAP and linux

6.
open up the Ubuntu installer and go through the steps only define the partitions manually... in the manual partition area of the installer program, just select the EXT4 /dev/sda4 partition as / and reformat it (why not?)

7.
on the final setup screen before you click on "install" ( step 8 of 8 ) click on advanced for GRUB to be installed to and select /dev/sda4 instead of the default /dev/sda from the pull down menu

8.
click install

9.
???

10.
profit

Notes:
GRUB must be installed on one of the first 4 /dev/sda partitions... obviously we dont want it on the first three, otherwise it would mess with the shiny rEFIt that I assumed was installed on OSX at some point. I dont know about anybody else, but I like shiny buttons to click on and look at.

I also assume that this is being installed on either a new drive, or a drive that has only OSX on it, or a drive that anything else on besides OSX (say an existing windows+linux install) does not have anything too important on it.

If there is stuff already installed that has important stuff on it, then boot up with the live CD and try to match checkpoint 5.5 as best as possible, figure out a way to remove GRUB from the MBR and use this method... [http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide) to install GRUB to /dev/sda4. I tried that, only at the time I was trying to install to /dev/sda5, which does not work

Another option would be to use GRUB-EFI [http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI) - I do recall coming across a way to have GRUB-EFI working with rEFIt as the front end, but as I also recall it was a bit more complicated than I wanted to deal with

/* *** *\

With the above 10 steps you still get the GRUB menu from which you can select OSX, windows, ubuntu, and related stuff, with a default 10 second or whatever time period. I suggest once its set up to edit the GRUB menu to remove OSX and shorten the delay duration to something like 2-3 seconds.

*Phew* longest post I've done so far on UbuntuForums... now that I have the three OSs installed its time to update, install software, and mirror my drive for a backup.

Enjoy

---

### Post by H264 on 2010-07-30
quick follow up to this post, as it does not quite work... when I booted into windows it sayed that it could not find hal.dll and that it was missing or corrupt, or some such nonsense. For some reason, it is just fine on partition 4

So for step 5 and 5.5 just switch linux and windows around, so the partitions look like...
EFI/FAT32 | OSX/HFS+ | linux root/EXT4 (see ***note) | windowsXP/NTFS | SWAP | [other linux installs]

***note
Really, this partition is where GRUB needs to be installed to, I'd imagine if you had a seperate /boot partition, put it in place of the linux root, and install GRUB there too; just make sure there is enough space.

Firguring this out was a week long battle of installing, formatting and reinstalling... lol

---

