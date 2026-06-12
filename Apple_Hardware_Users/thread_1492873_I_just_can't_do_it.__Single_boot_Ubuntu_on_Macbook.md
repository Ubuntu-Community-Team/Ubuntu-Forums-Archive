---
title: "I just can't do it.  Single boot Ubuntu on Macbook pro 5,2"
date: 2010-05-25
forum: Apple Hardware Users
---

### Post by dham on 2010-05-25
I've tried everything.  Followed all tutorials(most are for dual though) and I hit snags everywhere I turn.  Seems like nothing goes right.  I did refit.  That said will not touch disk.  Booted up ubuntu live cd.  Downloaded the gptsync package.  Followed the tutorial.  Ran it on my disk and it says the same thing.  I can't reinstall grub.  It says autodetection of filesystem module failed.

I just can't catch a break with this.  I got arch linux to install fine no problems.  What should I do?  I always get no bootable devices found.  Help.

---

### Post by linuxopjemac on 2010-05-25
Did you try [this]("http://mac.linux.be/content/single-boot-linux-without-delay")?
Let us know if that works.

---

### Post by dham on 2010-05-25
The problem is step 4 everytime.

4. Put in rEFIt CD and holding down alt key, boot rEFIT cd. Synchronize  GUID and MBR. Restart.

It always says unable to touch device.

Then I follow the other tutorial where you boot into ubuntu live cd and try to synchronize using the gpt deb package.  That says the same thing.

---

### Post by linuxopjemac on 2010-05-25
Even with the new rEFIt 0.14 ?

---

### Post by sha.goyjo on 2010-05-25
Forgive me if I'm wrong, but if you are going to single boot I don't think you need refit. As long as you don't plan on running osx (you can ever run windows + linux + bsd if you like) I don't think you need it.

I say that because I'm not using it. I dual boot Ubuntu and Windows XP on my intel MacBook.

---

### Post by dham on 2010-05-25
> **linuxopjemac said:**
> Even with the new rEFIt 0.14 ?

Yes. :(.

> **sha.goyjo said:**
> Forgive me if I'm wrong, but if you are going  to single boot I don't think you need refit. As long as you don't plan  on running osx (you can ever run windows + linux + bsd if you like) I  don't think you need it.

I say that because I'm not using it. I dual boot Ubuntu and Windows XP  on my intel MacBook.

I wish that were the case.  I always get unable to find boot devices right after a single ubuntu install.

---

### Post by linuxopjemac on 2010-05-25
did you try the gpt fdisk program as proposed by another Ubuntu user here?

link: [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

Again, I have no experience with this, but you could be our guinea pig as you have nothing to lose anyway ;)

---

### Post by sha.goyjo on 2010-05-25
> 
I wish that were the case.  I always get unable to find boot devices right after a single ubuntu install.

By that do you mean the folder with the question mark? You gotta give it a little time to find grub. At least that has been my experience. Lets try everything to get this guy working.

---

### Post by dham on 2010-05-25
> **linuxopjemac said:**
> did you try the gpt fdisk program as  proposed by another Ubuntu user here?

link: [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

Again, I have no experience with this, but you could be our guinea pig  as you have nothing to lose anyway ;)

I have not tried the gdisk.  I have, however, tried the second tutorial.  I get the same error as when I do refit.  I just did another reinstall and used gparted to mange the boot flags.  I boot the boot flag on the root partition like it suggested and that didn't change anything.  Although that's what gave me a flash folder now.

I will be trying the gdisk right now in a few minutes.

But yes I have nothing to lose.  So we can try anything.

> **sha.goyjo said:**
> By that do you mean the folder with the question mark? You gotta give it a little time to find grub. At least that has been my experience. Lets try everything to get this guy working.

Yes folder with question mark.  I'll give it a few minutes to find grub.

Thanks.

---

### Post by sha.goyjo on 2010-05-25
Dham, also, some advice, make sure NOTHING else is plugged into the macbook pro when you boot. Sometimes the EFI will try to boot to anything (even an external mouse with a jtag loader) before running grub-efi. Give it a couple of minutes to find grub. If not, we can satisfactorily scratch that off of the list.

---

### Post by dham on 2010-05-25
Hey.  All that is plugged in is my ethernet cable and power.  I don't even have a mouse or keyboard plugged in.

My process is put the disk in.  Ubuntu loads up.  I say install onto hard disk.  It auto prepares the hard drives and it installs.  I reboot and it says can't find bootable hard disk.  I try to use the newest refit, ubunut live cd, gparted.  For some reason it just won't work.

I gave it 5 minutes to find grub this time.  Still nothing.
:(

---

### Post by sha.goyjo on 2010-05-25
Try unplugging the ethernet cable. I've had it hang because it was waiting for a an ethernet boot before. Maybe not, but it's worth a try.

EDIT:

Also, have you tried just (and I mean just, with no modifications) installing ubuntu with the standard graphical installer from the desktop live CD and choosing the "use entire disk" option? That is what I typically do for single boots.

---

### Post by dham on 2010-05-25
> **sha.goyjo said:**
> Try unplugging the ethernet cable. I've had it hang because it was waiting for a an ethernet boot before. Maybe not, but it's worth a try.

EDIT:

Also, have you tried just (and I mean just, with no modifications) installing ubuntu with the standard graphical installer from the desktop live CD and choosing the "use entire disk" option? That is what I typically do for single boots.


No luck with ethernet.(at least for a few minutes)

I'm going to do another reinstall using the method you suggested right now.

Thanks again guys for being so helpful.  This seems like a good community over here.

---

### Post by sha.goyjo on 2010-05-25
> **dham said:**
> 
Thanks again guys for being so helpful.  This seems like a good community over here.

We try :)

---

### Post by dham on 2010-05-25
Ok I just got done with the live cd graphical install.  I rebooted, and now it just gives me a folder with a question mark.  Didn't say no boot device found like before.  Any ideas where to go from here?

Ok I just hit option to select boot menu and chose windows.  It still comes up with flashing folder.  It wont even go to the no boot device found screen.

edit:
[http://www.ubuntuproductivity.com/journal/tips/05/2010/instal-ubuntu-10-04-single-boot-macbook/](http://www.ubuntuproductivity.com/journal/tips/05/2010/instal-ubuntu-10-04-single-boot-macbook/)

I'm going to try that.

---

### Post by sha.goyjo on 2010-05-25
Yeah, give that a try and tell us what your results are. I'd be interested in seeing if apple has changed something in the EFI.

EDIT:
Dham, it just hadn't occured to me to ask (and now, after reading that tutorial, I feel that I have too), what kind of partition table have you been using? On single boots, I use an MS-DOS partition table. If you are using a hybrid still, or a guid, you may have to do things differently. If that tutorial doesn't work, I may have some additional ideas.

---

### Post by dham on 2010-05-25
Well that tutorial told me to use the guid partition.  Then tell ubuntu to use freespace to install.  It seems to be a little progress.  Instead of the won't touch I get the "mbr partition is invalid, partitions overlap"

Should I format to MBR and try to do it that way?

I'm going to try the gpt package tutorial to sync it and see what that does.  If that doesn't work I'm going to format to mbr explicitly, and try from there.

My computer is starting to hate me I think.  Have to keep on turning it on and off:(.

---

### Post by sha.goyjo on 2010-05-25
If gpt sync doesn't work, I think formatting the MBR and then trying again with a clean sda is sane. I usually use
```

dd if=/dev/zero of=/dev/sda bs=512 count=1

```

But it's up to you how you do it. Some people prefer to use gparted.

---

### Post by dham on 2010-05-25
Oh gosh.  I give up.  I hate Apple.  I've been doing this crap all day and yesterday.  I don't know what else to try.  My laptop is like super crappy or something.

---

### Post by sha.goyjo on 2010-05-25
Don't give up Dham. I'm sure we'll find a way to make this work. All of the fun of the learning process is success after prolonged failure. Picking yourself back up and trying again will give you important skills.

I'd recommend that (if you haven't already) you boot to the live cd, run the command I listed above, and then open gparted and select "create new partition table" followed by "msdos". Then launch the gui installer and give that a try.

If that doesn't work, dd the mbr AGAIN, and create a guid partition table as listed in the tutorial you found.

If that doesn't work, dd the mbr AGAIN, and try with refit.
Slow and methodical, and you might stumble accross something successful.

Please understand that I'm not implying that you haven't been trying. If you've already done these processes (in this order) than I'd skip them. However, it's possible that the EFI is getting confused about the different partition table types.

Let me know what results you get.

Jason

---

### Post by dham on 2010-05-25
> **sha.goyjo said:**
> Don't give up Dham. I'm sure we'll find a way to make this work. All of the fun of the learning process is success after prolonged failure. Picking yourself back up and trying again will give you important skills.

I'd recommend that (if you haven't already) you boot to the live cd, run the command I listed above, and then open gparted and select "create new partition table" followed by "msdos". Then launch the gui installer and give that a try.

If that doesn't work, dd the mbr AGAIN, and create a guid partition table as listed in the tutorial you found.

If that doesn't work, dd the mbr AGAIN, and try with refit.
Slow and methodical, and you might stumble accross something successful.

Please understand that I'm not implying that you haven't been trying. If you've already done these processes (in this order) than I'd skip them. However, it's possible that the EFI is getting confused about the different partition table types.

Let me know what results you get.

Jason

I'm trying not to give up but man this is super annoying.  Haha.  I think I'm going to try to revert to a dual boot.  I think that's easier from what I read.  I'm currently trying that right now.  I just installed macosx and I'm installing ubuntu right now.  I gave macosx the smallest partition I could.  Maybe this will work.

I'm not sure what is going on though because I have single booted Windows 7 on this thing for a while.  The only thing I did was partition it to MBR and install windows.  It has been fine ever since.  I tried the same with Ubuntu and it's been a disaster.  

BTW: this is my work laptop and I'm not to fond of MacOSX(workflow is so counter intuitive) that's why I'm single booting different Os's.

---

### Post by dham on 2010-05-25
No luck:(  I have to be doing something wrong.

---

### Post by tenuki on 2010-05-25
Heh dham,

This sounds really frustrating. I'm sure it's not much comfort, but I'd say don't give up just yet. The thing that strikes me is that it sounds like you're doing everything right and there's apparently people out there with Ubuntu on a macbook pro 5,2 (I'm on a macbook pro 5,4) - so I'm concerned it must be something more fundamental. 

Two stupid questions:

1. Is there anything funny about the hardware? You say you've reinstalled MacOS on it - does everything run OK in MacOS? Is the firmware up to date?

2. Is there any possibility the ubuntu install disk is screwy? Have you tried downloading and burning the image again? 

Just for info: which ubuntu disk image did you burn for the install?

---

### Post by jamesixgun on 2010-05-25
Hello. I think this might work:

Get refit going (or use a refit cd, it doesn't matter).
Boot into Ubuntu install disc.
Go into gparted.
Create a small partition at the beginning of the drive, just after your EFI partition. 
Create a second partition, using most of the rest of the drive for Ubuntu.
Create a third partition for the swap (equal to how much ram you have, more or less).
Save changes, quit gparted.
Start up the installer.
When you get the chance, choose 'Specify partitions manually.'
For the first partition you made (should be /dev/sda2) choose Change --> use as NTFS. At Check Format, choose mount point =/windows
Select the second partition (dev/sda3) choose Change --> use as Ext4, mount point /
For the final partition, choose Add --> Use as Swap.

Click through the rest of the installer screens. At the last screen, click Advanced and choose to install GRUB to /dev/sda2 (the NTFS partition)

Finish the installation. 

When refit comes up, you should be able to sync partitions now, since GRUB won't be trying to overwrite your EFI.

If you go cd option for rEFIt, when Ubuntu installer spits the disk out, swap be quick about shoving the refit disc in and booting from it to sync partitions.

After the partition sync, shut down your computer through rEFIt.

Start up again, and say hello to what should be a functional single-boot UbuntuBook.

(Note: this is the same process I use to get dual-boot, but just leaving out the OSX partition, so I'm not positive it will work. What I am sure of is that GRUB is screwing up your partition tables, and will continue to do so until you tell it to install itself in a separate partition.)

Best of luck! (and please don't dual boot Windows and Ubuntu on your mac! Windows is yucky! Ubuntu is pretty! HA!)

---

### Post by dham on 2010-05-25
Guys.  Thank you for all your help.  I turns out my ssd that I had in there was causing major issues.  Either that or the way I installed it over windows worked.  Basically I just put the original hard drive back in there and selected install and it worked perfectly!

I'm so excited.  After all this time, I just needed to put the original hd back in.

Although I'm having major issues with my track pad.  It's super sensitive and it clicks very wierd.  I also can't scroll down or up with another finger on the trackpad.  I enabled the settings in track pad under mouse, but no luck.

Thanks again guys.

---

### Post by sha.goyjo on 2010-05-25
Glad everything worked out well for you!

---

### Post by tenuki on 2010-05-27
Great.

Re: trackpad. If you haven't already, you might want to add the Mactel Support PPA to your system's software sources and install the package xserver-xorg-input-synaptics. Might sort it out:

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

Enjoy!

---

