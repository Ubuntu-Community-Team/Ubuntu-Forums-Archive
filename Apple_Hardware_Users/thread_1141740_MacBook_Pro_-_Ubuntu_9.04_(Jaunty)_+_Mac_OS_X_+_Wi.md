---
title: "MacBook Pro - Ubuntu 9.04 (Jaunty) + Mac OS X + Windows : Triple boot HOWTO"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by phico on 2009-04-28
Hello,

I have just reinstalled my MacBook Pro with triple boot including
Ubuntu 9.04 and give you the HowTo ..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111575&stc=1&d=1240952059[/IMG]


**Install Mac OS X**
[LIST=1]
[*]Put Mac OS X Leopard CD 
[*]Rebot and hold "C" key to launch installer
[*]Open Disk Utility, erase partitions and create a new one for Mac OS X (I put 10G)
[*]Install Mac OS X
[*]Launch Mas OS X
[*]Download refit from [http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[*]Install refit : double click "rEFIt.mkg" and follow instructions
[*]reboot 
[/LIST]

**Install Ubuntu 9.04**
[LIST=1]
[*]Put Ubuntu 9.04 CD 
[*]Reboot and choose linux CD in refit menu
[*]Launch Ubuntu install
[*]Select Advanced partition
[*]Create one partition for linux (format ext3, / as boot)
[*]Create one partition for windows (unformated)
[*]Do NOT create swap partition as partitions are limited to 4 ..
[*]At confirmation screen, click Advanced button 
[*]Choose to install Grub boot loader on the linux partition 
(NOT on the MBR because Windows can only do so ...)
[*]Continue installation 
[*]Reboot
[*]Start Partion Tool in refit and sync
[/LIST]

**Install Windows**
[LIST=1]
[*]Put Windows XP in CD
[*]Reboot and choose Windows CD in refit menu
[*]Launch Windows install
[*]Choose the Windows partion defined before
[*]Reboot and finish windows install
[*]Put Mac OS X cd
[*]Go to bootcamp directory and launch setup.exe this will install all windows drivers
[/LIST]

**Configure Ubuntu 9.04**

This is for MacBook Pro 4.1

_Graphic card : _
[LIST=1]
[*]Go to : System>Administration>Hardware Driver 
[*]Activate latest NVIDIA driver
[/LIST]

_Wireless :_
Should work out of the box
If not : 
[LIST=1]
[*]System>Administration>Hardware Driver 
[*]Activate Broadcom driver
[/LIST]

_WebCam :_
Work out of the box

_Sound:_
[LIST=1]
[*]sudo gedit /etc/modprobe.d/options
[*]add :
[/LIST]
```
options snd_hda_intel model=mbp3
```
reboot

_Keyboard fn keys:_
Work out of the box, screen brightness, sound ..
Keyboard light does not work automatically
Manual solution by maffix in [http://ubuntuforums.org/showthread.php?t=1141029](http://ubuntuforums.org/showthread.php?t=1141029)
set on  : 
```
echo 255 | sudo tee -a /sys/class/leds/smc::kbd_backlight/brightness
``` (max = 255, min =0)

_Bluetooth_
Seems to work also .. at least I paired my phone

That's it!

---

### Post by cyberdork33 on 2009-04-28
If you haven't already, please add info to the docs:
[https://help.ubuntu.com/community/MacBookPro4-1/Jaunty](https://help.ubuntu.com/community/MacBookPro4-1/Jaunty)
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by toxik_ca on 2009-05-31
Thanks phico for your guide. With it I was able to install Jaunty on my 3.1 Macbook Pro. Note that I did not install Windows.

I had a 16GB partition created previously in Mac OS X using bootcamp utility. I updated ubuntu just after the installation with no problem.

Here are the modifications of phico's guide for Macbook Pro 3.1: 

> **phico said:**
> 
**Install Ubuntu 9.04**
[LIST=1]
[*]Put Ubuntu 9.04 CD 
[*]Reboot and choose linux CD in refit menu
[*]Launch Ubuntu install
[*]Select Advanced partition
[*]Create one partition for linux (format ext3, / as boot)
[*]Create one partition for windows (unformated)
[*]Do NOT create swap partition as partitions are limited to 4 ..
[*]At confirmation screen, click Advanced button 
[*]Choose to install Grub boot loader on the linux partition 
(NOT on the MBR because Windows can only do so ...)
[*]Continue installation 
[*]Reboot
**Note I did not use the partition tools since I used Bootcamp utility.**
[/LIST]

**Configure Ubuntu 9.04**
...


Use the config posted by phico except for the sound. Use the following configs for the Macbook Pro 3.1:

_Sound:_
[LIST=1]
[*]sudo gedit **/etc/modprobe.d/alsa-base.conf**
[*]add :
```
options snd_hda_intel model=mbp3
```
[*]reboot
[/LIST]

Remove mouseemu to have F11 and F12 keys behave as normal. This makes the Capslock LED works.

```
sudo apt-get remove mouseemu

```

Finally, use 3 fingers + click for right click.

Hope this help!

---

### Post by 311005901 on 2009-05-31
I did all of these steps exactly on my iMac. All installations went fine, except XP asked to set itself as the primary partition. I didn't see what the big deal was so I continued with the installation.

When I was done with the XP installation, my rEFIt only listed OSX and XP, forgetting the Ubuntu partition.

I tried to sync the MBP to get Ubuntu to show up, but rEFIt said it was already updated.

How do I get all three to appear on the rEFIt menu?

Edit: Also, my XP Home (SP1) partition seems to think it has less than 4 megabytes of free space on it (actually, it has ~98 gigs free). I tried to install the XP SP2 update from my iPod and it said that I can't install it because it doesn't have enough space. Why does it do this?

---

### Post by 311005901 on 2009-06-01
I hate to do this, but bump? :(

---

### Post by cyberdork33 on 2009-06-01
> **311005901 said:**
> I did all of these steps exactly on my iMac. All installations went fine, except XP asked to set itself as the primary partition. I didn't see what the big deal was so I continued with the installation.

When I was done with the XP installation, my rEFIt only listed OSX and XP, forgetting the Ubuntu partition.
It sounds like you had grub installed to the MBR (the default location) and then Windows overwrote it (as it does... without asking...). You need to reinstall grub to the root partition of your ubuntu install.
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by travamiel on 2009-06-01
Will this work for the 2,1 MacBook Pro if I use the Ubuntu Community Documentation that cyberdork linked for setting up Ubuntu 9.04?

---

### Post by 311005901 on 2009-06-01
Thanks for the help, cyber!

I seem to have run into another problem: my screen goes black when I try to live boot using my Ubuntu Jaunty AMD 64 cd. The menu comes up and I select "Try without installing" and it sits there.

How do I reinstall grub without booting into Ubuntu?

---

### Post by touann on 2009-06-01
Anyone have tried to triple boot with windows 7?

Thank for the step by step with xp!

---

### Post by cyberdork33 on 2009-06-02
> **311005901 said:**
> Thanks for the help, cyber!

I seem to have run into another problem: my screen goes black when I try to live boot using my Ubuntu Jaunty AMD 64 cd. The menu comes up and I select "Try without installing" and it sits there.

How do I reinstall grub without booting into Ubuntu?
you can change the video options using the correct Fx key listed in the boot menu. Try changing that.

---

### Post by 311005901 on 2009-06-06
Cyber, thank you so much! :popcorn:

All of my partitions and rEFIt are working correctly!

---

### Post by _mario_ on 2009-06-09
i hate to say that: but please do not repeat common mistakes, which will most likely confuse other less experienced users.

> **phico said:**
> 
**Install Ubuntu 9.04**
[LIST=1]
[*]Do NOT create swap partition as partitions are limited to 4 ..
[/LIST]

in fact, the linux kernel is able to read the GPT. grub (standard grub, not grub EFI) is the only part of the boot process that needs the MBR partition table to load the linux kernel from. hence, a separate boot partition (or alternatively the root partition if one doesn't set up /boot separately) has to be among the first 4. the rest of linux might be everywhere on the disk, including more advanced setups with LVM, encrypted partitions, encrypted LVM containers with root, swap, and home logical volumes ...

> **phico said:**
> 
[LIST=1]
[*]At confirmation screen, click Advanced button 
[*]Choose to install Grub boot loader on the linux partition 
(NOT on the MBR because Windows can only do so ...)
[/LIST]

windows always installs its boot loader onto its (boot-)partition and sets this partition to active. to successfully boot on PCs, it also needs the standard MBR boot code that loads and executes to boot loader from the active partition. that's why windows destroys grub if it is there. on macs it is even safe to erase the first 440 bytes of your harddisk (the MBR boot code), after installing all operating systems' boot loaders on their respective partitions.

ciao,
Mario

---

### Post by swarup on 2009-07-28
re: rEFit does not seem properly installed.

I want to do the triple install on my MBP 17" laptop, as given in the HowTo, and have installed and shrunk Leopard, leaving a large chunk of blank space on the HDD for the other two OS's. I then downloaded and installed rEFIt to the OSX partition according to the instructions-- but when I reboot my laptop, I do not get the rEFIt boot menu, which as I understand, means that rEFIt is not installed properly. And I tried putting the Ubuntu 9.04 cd in the DVD drive and rebooting to see if there have to be at least two available boot options for the rEFIt boot menu to appear, but it still does not appear. What do I do to get rEFIt installed properly?

---

### Post by 311005901 on 2009-07-29
Swarup: I had this problem on first run. Now, every time I update in OSX, I lose the rEFIt menu. :(

It's a really easy fix, though. :D
To get the rEFIt menu to appear when you boot, you have to boot into OSX. Then, find and open up the rEFIt disc image or the rEFIt folder or whatever OSX calls programs you download from the internet. Then, in Spotlight (CMD + Space), open up the OSX Terminal.

Then, click and drag the file from the rEFIt folder called "enable-always.sh" to the Terminal window. Press enter and enter your password. 

When you reboot, it should automatically boot to rEFIt. :D

---

### Post by bmb6agb on 2009-07-29
I have OSX and a 32 gig Windows partition installed with Boot Camp. Is there a way in which I can add Ubuntu without disturbing the existing two installations?

---

### Post by swarup on 2009-07-29
311005901: Thanks for the tip! Actually, before trying anything else I shut down this morning and booted it back up, and mysteriously the rEFIt multiboot screen is now appearing at every bootup.

bmb6agb: hey bro, we're in this together. I'm just in the same process now of trying to set up my triple boot, so don't have any answers for you yet. Perhaps someone else may.

I want to set up a triple boot with OSX/Jaunty/Vista. I've got OSX installed, along with rEFIt, and was going to install Vista next and have a large empty space on the hdd for it and Jaunty. But everytime I boot up to the Vista install cd, it complains that it needs an NTFS partition to install onto. I tried booting up parted magic so as to convert the empty space to NTFS, but every time I boot parted magic, it gives me a frozen cursor when it finishes its bootup-- so I had to abandon it.

So I thought, I'll install Jaunty first and during the advanced install, will create an extended partition in which to put Ubuntu (type ext3) and swap. And at the same advanced partitioning screen, I'll create what will be the fourth partition, and will set it to be of type NTFS-- and then I'll be all set. But what I found is, that at the advanced partition screen under partition types, there is no option for creating an extended partition, and nor is there an option for type NTFS. 

If I create an ext3 for Ubuntu without the extended partition, then I won't have any partitions left for swap if I want to add Vista. Isn't there an option for extended partition creation in the Jaunty installer? And can't the installer create an NTFS partition?

---

### Post by buntuLo on 2009-07-29
i'd simply run the Jaunty livecd, install GParted from repositories, use it to set partitions as i like them to be, then proceed with the win$ and linux installations. am i missing something?..

---

### Post by swarup on 2009-07-29
> **buntuLo said:**
> i'd simply run the Jaunty livecd, install GParted from repositories, use it to set partitions as i like them to be, then proceed with the win$ and linux installations. am i missing something?..

I also got the same idea-- to try using gparted instead of the installer partitioner. I went into gparted, set up an extended partition with Ubuntu ext3 and swap, and then set up a 4th partition as NTFS. But when I click on "apply", it is giving an error that it can't do the operation. And when I try creating just an ext3 partition as a test, it does it fine. I found by experimentation, that it is just the extended partition which gparted refuses to create. It will create anything else, besides that. It seems that gparted cannot create an extended partition in an apple computer. I do not know why.

---

### Post by swarup on 2009-07-29
I have OSX and Jaunty installed, and a third partition set up as NTFS. It is 25 GB size. I went to install Vista on it, and for some reason Vista says it is not large enough (Vista business only requires a 23 GB partition for installation). So I dropped the idea for now of using Vista, and am installing Win XP professional. I booted to the XP livecd, selected the NTFS partition, and hit "enter" for it to install. It said it had to check the disk, apparently made some sort of revision to it, and then told me to reboot the computer in order to do the install. I rebooted and opted for boot to the XP cd. Then I got a screen that says "BOOTMGR is missing. Press ctrl-alt-del to restart." I tried that, but it just comes back to the same screen. (Just in case anyone asks, I did install grub to sda3 (ubuntu). And rEFIt is working fine.)

What do I need to do to install XP?

---

### Post by _mario_ on 2009-07-29
> **swarup said:**
> 
So I thought, I'll install Jaunty first and during the advanced install, will create an extended partition in which to put Ubuntu (type ext3) and swap. And at the same advanced partitioning screen, I'll create what will be the fourth partition, and will set it to be of type NTFS-- and then I'll be all set. But what I found is, that at the advanced partition screen under partition types, there is no option for creating an extended partition, and nor is there an option for type NTFS. 

If I create an ext3 for Ubuntu without the extended partition, then I won't have any partitions left for swap if I want to add Vista. Isn't there an option for extended partition creation in the Jaunty installer? And can't the installer create an NTFS partition?

the GPT partitioning scheme doesn't support nesting of partitions. you simply cannot create an extended partition. if using the MBR partitioning scheme, extended partitions are necessary to overcome this stupid 4 partition limit imposed by the MBR format.

but you can do as follows to still use several partitions for ubuntu:
[LIST=1]
[*]i assume your disk contains a partition for OSX, which ought to be /dev/sda2, since /dev/sda1 is the EFI system partition not visible in OSX's disk utility.
[*]use the alternate installer to create a small partition (e.g. 512MB ext4) for /boot (/dev/sda3).
[*]create another partition for windows (/dev/sda4). filesystem type doesn't matter. windows can format it during installation.
[*]create a third partition (/dev/sda5) and initialize it as a LVM physical volume, initialize a LVM volume group and create LVM logical volumes. these are the partitions for /, /home, and swap. you may also fully encrypt this container by initialize it as a dm-crypt volume which in turn becomes the LVM physical volume.
[*]re-sync your MBR with rEFIt before trying to install windows. there, select the 4th partition. the 5th partition might not be visible in versions up to vista. the windows 7 installer shows all 5 partitions but you cannot install onto partitions beyond 4, because its boot loader still only recognizes the MBR partition table (limited to 4 partitions). a booted windows 7 fully recognizes a GPT partitioning scheme. showing all partitions in the volume manager.
[/LIST]

doing so results (more or less) in the following setup (taken from my machine):

```
   
   device       start -          end   filesystem  size
------------------------------------------------------------
/dev/sda1          40 -       409639  FAT32 (EFI)  200 MiB
/dev/sda2      409640 -     42352680         HFS+  20 GiB
/dev/sda3    42352681 -     43401257         EXT3  512 MiB
/dev/sda4    43401258 -    106315818         NTFS  30 GiB
/dev/sda5   106315819 -    976773134         EXT3  415 GiB

```
/dev/sda5 is decrypted to /dev/mapper/system, which in turn is the only LVM physical volume of an LVM volume group 'system', which contains 3 LVM logical volumes /dev/mapper/system-root, /dev/mapper/system-home, /dev/mapper/system-swap.

ciao,
Mario

---

### Post by swarup on 2009-07-29
Wow, very interesting. I'll try it.
A few questions:
1. Will your method solve the problem I mentioned above in my last post, that XP will not install because of that the "BOOTMGR is missing"?
2. When I have 4GB of RAM, then is a swap partition still needed for proper function of the computer? Several others have told me that when you have that much RAM, no swap is needed unless you want to use the hibernated function. Will it suspend (not hibernate) without swap? And does yours suspend/hibernate?
3. How do you feel about the general functionality of Ubuntu on your mac? Is yours a laptop/MBP? If so, does the trackpad work properly? Does the machine run hotter than it should? I've purchased this 17" MBP mainly for use with Ubuntu-- because I really like the MBP keyboard and I do alot of typing.

---

### Post by _mario_ on 2009-07-30
> **swarup said:**
> 
A few questions:
1. Will your method solve the problem I mentioned above in my last post, that XP will not install because of that the "BOOTMGR is missing"?

i don't know, because i don't know what that message shall mean.
> **swarup said:**
> 
2. When I have 4GB of RAM, then is a swap partition still needed for proper function of the computer? Several others have told me that when you have that much RAM, no swap is needed unless you want to use the hibernated function. Will it suspend (not hibernate) without swap? And does yours suspend/hibernate?

in general, Linux will run fine without swap. however, if your system runs out of memory, it will not be possible to swap some currently unused portions to disk to free up memory. instead Linux will kill tasks to get free memory. (the same will happen if swap is also full, which is just more unlikely.) anyway, 4GB should suffice for a desktop system.

of course, as hibernate uses the swap partition/file to store the system image, hibernate in general will not work anymore if setting up without swap. suspend (to ram) should still work. with my setup, both suspend and hibernate do work.
> **swarup said:**
> 
3. How do you feel about the general functionality of Ubuntu on your mac? Is yours a laptop/MBP? If so, does the trackpad work properly? Does the machine run hotter than it should? I've purchased this 17" MBP mainly for use with Ubuntu-- because I really like the MBP keyboard and I do a lot of typing.

my machine (MBP4,1) runs fine with Ubuntu after installing the Mactel packages. everything works. but newer machines (5th generation) are known to cause some more trouble, in particular with respect to power consumption.

btw: after writing my previous post i realized, i installed like this due to encryption. if you don't need encryption, there's an even simpler approach - i also did before - that allows to use the regular installer rather than the alternate one. however, you'll have to keep some facts/restrictions in mind:

partitioning:
[LIST=1]
[*] the MBR partitioning scheme allows to describe up to 4 (primary) partitions (the slots) in its primary partition table in the first disk sector. to overcome this restriction, extended partitions were invented, that contain another partition table with the same format to describe logical partitions. this effectively nests those partition tables.
[*] the GPT partitioning scheme doesn't support nesting, as it natively supports more than 4 partitions.
[*] the GPT partitioning scheme requires an EFI system partition, although not yet used by Apple. this must be the first partition on disk. deleting this partition doesn't free an MBR slot (see below), so just keep it. also note, that Apple's graphical disk utility doesn't show this partition. the command line utility, however, does.
[*] the GPT partitioning scheme requires an MBR in the first disk sector, called protective MBR (PMBR), that uses exactly one slot to protect the whole disk from being accidentally overwritten by legacy tools. this is what the EFI specification mandates, this is what gparted does, and this is why we have to run rEFIt's partitioning tool after modifying partitions (see below).
[*] rEFIt's partitioning tool allows to write an MBR to the first sector that protects the GPT and the EFI system partition using one slot (instead of the whole disk), leaving 3 free slots to describe the following 3 partitions (in order), e.g. OSX, Linux, and Windows. this is why most tutorials suggest to install Linux using only 1 partition, effectively requiring a swap file, but this is not the whole truth. although, this approach is not standard compliant, it seems to be safe. and this is what Apple's boot camp and disk utility do as well.
[/LIST]

operating systems:
[LIST=1]
[*] a running OSX fully supports either partitioning scheme. however, OSX's installer refuses to install on a non-GPT disk. installing on a temporary disk and then cloning OSX to a MBR partitioned disk, is known to overcome this restriction.
[*] a running Linux fully supports either partitioning scheme. however, its boot loader GRUB (not GRUB-EFI) doesn't recognize the GPT. hence, Linux's boot partition (mounted to /boot) must be visible through the MBR, and hence must be among the first four. if one chooses to not set up a separate boot partition, this applies to the root partition, which contains /boot.
[*] a running Windows up to Vista doesn't recognize the GPT. Windows Vista with a recent service pack might recognize the GPT. i don't know. Windows 7 does. in any case Windows's boot loader (including Windows 7) doesn't support the GPT, and hence, Windows's system partition must be among the first four.
[/LIST]

this all means it is perfectly legal to have a partitioning like this:
[LIST=1]
[*] EFI system partition (covered by protective slot 1)
[*] OSX partition (slot 2)
[*] Linux boot/root partition (slot 3)
[*] Windows partition (slot 4)
[/LIST]
still allowing to boot all operating systems. additional partitions might come thereafter, e.g.:
[LIST=1]
[*] Linux root partition, if a separate boot partition is used
[*] Linux home partition
[*] Linux swap partition
[*] Linux LVM/crypto container(s) for the above types of partitions
[*] partitions for data exchange. however, only recent versions of Windows can really access it.
[/LIST]

ciao,
Mario

---

### Post by voltage22 on 2009-08-03
I already have OS X and Windows XP SP3 installed on my Macbook 2,1. Is there anyway to install Ubuntu without having to remove and re-install XP? Does it necessarily have to be in the Mac-Linux-Windows install order?

---

### Post by _mario_ on 2009-08-06
> **voltage22 said:**
> I already have OS X and Windows XP SP3 installed on my Macbook 2,1. Is there anyway to install Ubuntu without having to remove and re-install XP? Does it necessarily have to be in the Mac-Linux-Windows install order?

the order of partitions on disk doesn't really matter, as long as you keep the above restrictions in mind. neither does the installation order. however, it should be clear, that the Windows installer is not really able to shrink/move Linux/OSX partitions in order to get free space. hence, someone who likes/needs to install Windows last should use gparted booted off a Linux live-cd to repartition. with respect to your question, the same approach can be used to install Linux last: just repartition using gparted (shrink and/or move the Windows partition), and then proceed with the Ubuntu installation. don't forget to install grub to your Linux root/boot partition and to re-sync GPT and MBR after installation.

i merely chose this order, because rEFIt only offers the possibility to boot the first OS in its list after a certain timeout. this is usually partition order, with OSX being always first, unless the option legacyfirst is set which moves OSX at the end of the list. and i'd like to boot Linux by default. hence, Linux (only the boot partition) must be in front of Windows.

ciao,
Mario

---

### Post by swarup on 2009-08-11
Mario,
Thanks for the great tips on how to manage multiple partitions on a MBP. I've been busy, and couldn't get back to you right away. But now I am ready to set up my triple boot OSX/Jaunty/Vista, and have a few follow-up questions for you.

1. You mention that if encryption is not needed (it is not), then I can use the standard (rather than alternate) Ubuntu install. And the sense I got from your posting was that even with a standard install, I'll be able to add more partitions at the end of the standard four, for things like swap and /home. It sounds from your write-up like an LVM is still going to be needed for this. Is that something that can be set up in the standard Ubuntu install livecd? I never saw anything there about options for "LVM". I'm quite familiar with the use of extended logical partitions, but as you noted, that cannot be used on the MBP. So how do I set up the "LVM", if that is what I would need for swap?

2. As regards my need for swap, I don't think I'll ever need it for memory use, but I want to make sure the computer can suspend-to-RAM (I've heard swap is not needed for that, but I tried setting up the MBP as a triple with no swap, and Jaunty would not wake up from suspend. Once I removed Vista and reinstalled Jaunty with swap, the suspend-to-RAM worked fine.) And if the hibernate is also made to work with the swap, then that is a plus too.

3. I'd like to set up rEFIt so that it will default boot to Jaunty instead of OSX. What would I have to do to make this happen? (I couldn't completely follow what you described about this in the post just above.)

4. I guess I could just avoid the LVM and extra partitions matter, and instead create a swap file. It says on the [MacBook 2,1 wiki]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Using%20a%20Swap%20File%20instead%20of%20a%20Swap%20Partition") that "you can also hibernate (suspend to disk) your MacBook using a swap file"-- which is really great. If it works like that for the MBP 5,2 as well, then it almost seems easiest to just do the standard setup using just the four partitions (EFI/OSX/Linux/Windows), and then add the swap file once everything is installed. Although in the [Ubuntu swap documentation]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swap%20for?"), it is written that "The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system." No matter what, I definitely need to ensure that I can suspend-to-RAM; if in addition I can hibernate-to-disk, that would be nice to have as well.

What do you think will be the best approach for me, on the basis of the above points?

Many thanks for your kind help,
Regards,
Swarup


> **_mario_ said:**
> this all means it is perfectly legal to have a partitioning like this:
[LIST=1]
[*] EFI system partition (covered by protective slot 1)
[*] OSX partition (slot 2)
[*] Linux boot/root partition (slot 3)
[*] Windows partition (slot 4)
[/LIST]
still allowing to boot all operating systems. additional partitions might come thereafter, e.g.:
[LIST=1]
[*] Linux root partition, if a separate boot partition is used
[*] Linux home partition
[*] Linux swap partition
[*] Linux LVM/crypto container(s) for the above types of partitions
[*] partitions for data exchange. however, only recent versions of Windows can really access it.
[/LIST]

It isn't really clear yet for me how the extra partitions beyond the first four get created using a standard Ubuntu install. Does the LVM for swap, home, root get created in the standard install?

---

### Post by _mario_ on 2009-08-17
> **swarup said:**
> Mario,
Thanks for the great tips on how to manage multiple partitions on a MBP. I've been busy, and couldn't get back to you right away. But now I am ready to set up my triple boot OSX/Jaunty/Vista, and have a few follow-up questions for you.


so i've been. sorry for replying late. i had to prepare for an exam, i had today... but now it's time to talk about partitioning disks.

> **swarup said:**
> 
1. You mention that if encryption is not needed (it is not), then I can use the standard (rather than alternate) Ubuntu install. And the sense I got from your posting was that even with a standard install, I'll be able to add more partitions at the end of the standard four, for things like swap and /home.


yes.

> **swarup said:**
> 
It sounds from your write-up like an LVM is still going to be needed for this.


no.

> **swarup said:**
> 
Is that something that can be set up in the standard Ubuntu install livecd?


additional partitions: yes. LVM: no.

> **swarup said:**
> 
I never saw anything there about options for "LVM".


this option is currently missing. but might be added in a future release.

> **swarup said:**
> 
I'm quite familiar with the use of extended logical partitions, but as you noted, that cannot be used on the MBP. So how do I set up the "LVM", if that is what I would need for swap?


the bottom line is: LVM can be used to get something similar to extended partitions (but much more flexible). but it is **not required at all**, since you simply can create more than 4 primary partitions on a GPT disk. just ignore, that i mentioned LVM.

(as a side note: someone should fix gparted/libparted to not allow the user to create extended partitions on a GPT disk.)

> **swarup said:**
> 
2. As regards my need for swap, I don't think I'll ever need it for memory use, but I want to make sure the computer can suspend-to-RAM (I've heard swap is not needed for that, but I tried setting up the MBP as a triple with no swap, and Jaunty would not wake up from suspend.


you definitely **don't need** swap for suspend-to-RAM. i disabled my swap partition and suspended and it worked just fine. maybe there's something else not working on your machine.

> **swarup said:**
> 
Once I removed Vista and reinstalled Jaunty with swap, the suspend-to-RAM worked fine. And if the hibernate is also made to work with the swap, then that is a plus too.


but you'll **definitely need** swap for hibernation. and that's the only possibility to temporary switch to another OS (e.g. for updates), without rebooting.

> **swarup said:**
> 
3. I'd like to set up rEFIt so that it will default boot to Jaunty instead of OSX. What would I have to do to make this happen? (I couldn't completely follow what you described about this in the post just above.)


rEFIt is able to boot the first OS in the list after an amount of time. this is either the first OS on disk, as the OSes seem to be displayed in disk order, or always OSX (i cannot tell the difference, because OSX is my first OS on disk.) however, there's an option called **legacyfirst** in efi/refit/refit.conf on the OSX partition, that moves OSX to the end of the list.

if you create a setup like the one described in my previous posts, with OSX being the first OS, then Linux and Windows, you'll be able to boot Linux by default after enabling this option. otherwise it's OSX.

> **swarup said:**
> 
4. I guess I could just avoid the LVM and extra partitions matter, and instead create a swap file. It says on the [MacBook 2,1 wiki]("https://help.ubuntu.com/community/MacBook2-1/Jaunty#Using%20a%20Swap%20File%20instead%20of%20a%20Swap%20Partition") that "you can also hibernate (suspend to disk) your MacBook using a swap file"-- which is really great. If it works like that for the MBP 5,2 as well, then it almost seems easiest to just do the standard setup using just the four partitions (EFI/OSX/Linux/Windows), and then add the swap file once everything is installed. Although in the [Ubuntu swap documentation]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swap%20for?"), it is written that "The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition. It cannot use a swap file on an active file system." No matter what, I definitely need to ensure that I can suspend-to-RAM; if in addition I can hibernate-to-disk, that would be nice to have as well.


using a swap file instead of a partition is not MacBook but Linux kernel specific. hence, the first link will also apply to your machine. however, i never ran Linux using a swap file. i cannot tell whether it is possible to hibernate with such a setup. as mentioned above, swap (neither file nor partition) isn't required for suspend-to-RAM. if the Ubuntu documentation says that hibernation does not work with a swap file, i'd suggest to use a swap partition if you need it.

> **swarup said:**
> 
What do you think will be the best approach for me, on the basis of the above points?


at least 5 (primary) partitions:
[LIST=1]
[*] EFI system (mandatory)
[*] OSX partition
[*] Linux boot partition or root partition containing /boot.
[*] Windows partition
[*] Linux swap partition
[*] Linux /home partition. it's always good to separate OS and user data. (optional)
[*] data exchange partition using FAT32 or NTFS. (optional)
[/LIST]

the order of the last 3 partitions (5-7) doesn't matter. the first four are fixed to get what you what.

> **swarup said:**
> 
It isn't really clear yet for me how the extra partitions beyond the first four get created using a standard Ubuntu install. Does the LVM for swap, home, root get created in the standard install?


i never tried to use the partitioning tool incorporated into the installation program. in earlier versions it was just too limited and now i don't have to install anymore.

but you can always run gparted from the live CD (System > Administration > Partition Editor), partition your disk by creating as many primary partitions as you need, and run the installation program thereafter to assign those partitions to your newly to-be-installed system. to do so select "specify partitions manually (advanced)". as a last step, install the boot loader into the Linux boot/root partition. finally, reboot (the usual reboot during installation) and re-sync GPT and MBR with rEFIt.

it's as simple as that. there's only one drawback, as mentioned in my preceding posts: older versions of Windows might not be able to access partitions beyond the first 4 due MBR restrictions. everything else is a matter of file systems, permissions, ... the usual annoying stuff.

ciao,
Mario

---

### Post by pratikiitd on 2009-09-12
HI

I installed Mac OSX(Snow Leopard) on Partition 2, then I installed rEFIt on it. Then I installed Ubuntu 9.04 on the partition 4 while partition 3 was left vacant to install Windows 7. I then inserted the Windows installation CD and tried to install it on Partition 3. Installation was complete and then it asked for reboot. However, when I rebooted I only saw two partitions(mac and ubuntu). There was no partition of Windows 7. When I ran rEFIt partition manager from boot menu, it showed me that my current MBR has 4 partitions:
1. 200 MB Protection Layer
2. 140 GB HFS+
3. 60 GB NTFS
4. 40 GB Ext3

However, GPT record showed:
1. 200 MB Protection Layer
2. 140 GB HFS+
3. 60 GB HFS+
4. 40 GB Ext3

I am not able to boot into the windows. Please help me.

Thanks.

---

