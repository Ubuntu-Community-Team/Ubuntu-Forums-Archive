---
title: "Hello everyone, I wonder if..."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by rock-hopper on 2007-09-02
Hello everyone.  I have come to Linux rather late in years and have been loving my experience of Feisty Fawn, which is dual-booted with M$ Windows XP which my good lady uses - I am trying hard to convert her to Penguin Power, but that is another story - and thereby lies my problem, any help for which would be most welcome.

Our XP is a 'mature installation' and is suffering from bloat, sloth and undoubtedly most of the other seven deadly sins too; I honestly think that a re-install might be the only sensible solution, but if this is so, what will happen to my Ubuntu partitions?  I know they are logically separate, but will the re-installation of XP upset the boot settings and if so, what should I do about preserving them.  I know that re-installation of Ububtu is not an arduous task, but I was wondering if I could completely separate the 2 systems by installing Ubuntu on a new and separate HDD - SATA 2 in this case?

If this is possible, how would I manage OS selection at boot-up without messing up the boot order?

I suppose it could be achieved by altering the BIOS settings each time to set the first boot device but this seems to be a bit of a chore and I wondered if there was an easier way to do it.  I imagine it comes around to separating GRUB from the M$ MBR but I haven't been able to discover much about this possibility.

Again, any assistance you can offer would be more than welcome and I apologise in advance if my questions just rake over old ground; if posts already exists, would you be so kind as to point me towards them?

---

### Post by forestpixie on 2007-09-02
Basically what will happen when you reinstall XP is that you will lose the grub menu - MS really doesn't like sharing. IT can be resolved quite easily (he says never having had to do it)

have a look at these two, but there is quite a lot if you have a google - restoring grub, there is an Ubuntu page as well

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Good luck :)

---

### Post by meborc on 2007-09-02
i guess the wiki is the best guide - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by rock-hopper on 2007-09-02
I would like to thank meborc and forestpixie for their help to a very uncertain newcomer; it's really gratifying that such a great forum exists and that the members aren't too busy to take note of the problems of people such as me!

I shall read all the stuff you have recommended and search for more, now I have an idea what to look for.

Thanks again - long live Ubuntu - and the forum.

rock-hopper

---

### Post by Hospadar on 2007-09-02
What sorts of boot reinstallation issues you would need to deal with have mostly to do with here the boot loaders happen to be.  When you reinstall windows, it will put the NT bootloader in the master boot record of your drive.

Now if grub was installed into the master boot record, you'll need to replace grub and add some files to your windows install.  Grub however might not be in the mbr, it might be in a boot record for the partition.  So my suggestion would be just to reinstall window, and then try booting from both partitions to try and figure out which bootloaders still exist where.  Then you can go about restoring bootloaders to the proper places

---

### Post by sailor2001 on 2007-09-02
back-up, back-up, back-up and also for safety sake, download and burn a "super grub"

---

### Post by rock-hopper on 2007-09-17
Hello everyone - I'm sorry about the break in communications, but I've had a little spell in the QMC over the last week and haven't been near my computer lately - twitch, twitch!

Again, thank you all for your replies and here is yet another question for you!

I am really starting to 'get intu' Ubuntu and have bought a couple of books which have helped me a lot.  I am actively considering installing Ubuntu on a new Hard Disk drive and reinstalling the other lot's OS on the old one, not that I envisage using it all that much.

                       Windoze on HD 1
                       Ubuntu 7.0.4 0n HD 2

                       Restored MBR on HD 1
                       Grub on HD 2

I have an Asus mainboard and if I tap the F8 key on Start-up, I can access a 'Boot Menu'.  Am I right in thinking that from here I can choose to start either Windoze or Feisty Fawn?  That would be marvellous and avoid messing with partitions and bootloaders on a shared disk.  I was thinking of setting up a System Partition, a Swap Partition and a Home Partition on the Linux disk, similar to the way I have been using MS stuff for so many years - is this a good way to go, would you say?  Or have you any other ideas that might be better?

Again gentlemen - and any ladies, of course - I would be most grateful for your help.  With any luck, I can then get down to actually using Ubuntu rather than asking fool questions about getting it to work!

Best regards,

rock-hopper

---

### Post by forestpixie on 2007-09-17
hi - good to see you again 

> I was thinking of setting up a System Partition, a Swap Partition and a Home Partition - that's how I have mine set up - I have 8Gb for root, 1 for a swap rest for home. Seems to be best way - you can muck up your installation and reinstall without touching you 'personal' stuff.

> Am I right in thinking that from here I can choose to start either Windoze or Feisty Fawn? - can't answer that question from experience, but it sounds logical to me 

If it works that way and assuming you don't want to access win files from Ubuntu maybe you could remove the win drive when you install Ubuntu - although I believe you can change where grub goes by going advanced just after the partitioning part of the install 

I'd be thinking about going for it now :)

---

### Post by Skidpad on 2007-09-17
> **rock-hopper said:**
> I have an Asus mainboard and if I tap the F8 key on Start-up, I can access a 'Boot Menu'.  Am I right in thinking that from here I can choose to start either Windoze or Feisty Fawn? 
I would be more inclined to think that by hitting F8, that this would take you directly to the *device* boot options in the BIOS, not to choose a different OS.  The key-press options during start-up are all BIOS related.

I don't have an ASUS board, but that's how my MSI board is.  Easy enough to check without harm.

---

### Post by rock-hopper on 2007-09-17
Sorry - please forgive my sloppy thinking and writing - I'm getting old I guess.

What I meant to say was that if Windows was installed on, say HD 1 and Linux was installed on, say HD 2, both of which were separate devices with their own respective bootloaders, would pressing F8 allow me to choose which [COLOR="Blue"]device[/COLOR] took precedence and with it the [COLOR="Blue"]OS[/COLOR] of my choice?  If this was indeed the case, I think it would be a perfect solution for my problem.

Thanks also for the information about Partitions - it's starting to sink in - very slowly, I'm sorry to say!

Best regards,

rock-hopper

---

### Post by diatribe on 2007-09-17
> **rock-hopper said:**
> Sorry - please forgive my sloppy thinking and writing - I'm getting old I guess.

What I meant to say was that if Windows was installed on, say HD 1 and Linux was installed on, say HD 2, both of which were separate devices with their own respective bootloaders, would pressing F8 allow me to choose which [COLOR="Blue"]device[/COLOR] took precedence and with it the [COLOR="Blue"]OS[/COLOR] of my choice?  If this was indeed the case, I think it would be a perfect solution for my problem.

Thanks also for the information about Partitions - it's starting to sink in - very slowly, I'm sorry to say!

Best regards,

rock-hopper

I think it depends on your bios whether you can select which device at boot

---

### Post by ugm6hr on 2007-09-17
This gives a lot of useful info regarding your planned situation with 2 HD's.

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

And, as mentioned, if your BIOS allows selection of 1st boot device, then you could do it that way.  It is important to ensure that GRUB does not over-write the XP HD MBR though.  See the link above.

---

### Post by Mr.Beast on 2007-09-17
Hi RockHopper,

Your theory is good and sound from my first impressions of what you are trying to achieve, it seems very sensible and achievable.
It is very important that you identify which devices are which in the hardware configuration of the operating system of your choice.  (Linux advice here please)
they may identify themselves as HDA0, HDA1, or HD0, HD1 write this down, and make notes of the manufacturers details and size differences, on a piece of paper, you will be thankful later, trust me.

To echo what some other have posted, you need to really secure your current installation(s) prior to doing anything.
With the price of hard disks today this really won't cost you too much but this is what I would do to ensure I don't lose anything.

Firstly, but a reasonably large external USB2 (or esata, or firewire if you have them, but USB2 are  more versatile and compatible I have found) I would suggest something around 250GB could be had for as little as £30-£40 

I'm not "that" conversant with linux so I'm sure some gurus can chime in here with how to do it with linux but...
format the large external drive with Fat32 (windows and ubuntu can read and write to this without modification) Name the volume usb-disk. also, at this stage name your current volumes as OLD-disk.
Then select your tool to create an image of your existing disk.  I would either use an illegal copy of Norton/Symantec Ghost, or download a trial of snapshot (a truly fantastic product)
install / run your product of choice and create an image of your existing disk.

Also get your hands on your second / new disk (you wanted this for your plan of dual booting by device anyway)  
create a boot disk / boot CD and put the snapshot tool on it, making sure that you have the correct drivers for your chipset (if you have a modern motherboard you may need some bespoke drivers for things like sata controllers)  (Again, any linux gurus wanting to advise in this area feel free to chip in) (you could try Hiren's boot CD / Recovery CD, download this as it may have "cough" some tools you could use.)
Now you crack open your pc, Plug in your secondary hard disk and format this as Fat32 to make sure it's readable name the volume of the disk NEWDISK
Now, power off your machine, unplug the old hard disk drive, plug in the new drive and use the same connector for the data as you were using on the old hard disk.
Now, reboot your machine, booting from the CD /floppy and lay the image you created over the top of the new disk. (Your old disk is unplugged and completely isolated  and your data is safe) 
( All the above is with your USB2 external hard drive plugged in and powered on.)
Once the process is complete, try and boot form the new hard disk (don't forget to remove the CD from the drive first!)
 
When you power your system on, it SHOULD look like nothing has changed on your system, you should still have Ubuntu, and windows on one disk booting nicely, with your old disk as a backup. + a backup image on your external hard disk.

At this point, you can do a little dance and say "Oh yeah", I'm fab, I'm great!!!" a lot and punch the air several times.
(I like to celebrate every win, no matter how small)

Thats half the battle.
Now choose your main boot disk.  You may notice that your new disk is your main drive, and this may make a performance difference (better if you chosen a reasonable hard drive with a good cache and access speed level or newer / faster bus speed, worse if you've gone cheap on the disk. but personally I like the samsung spinpoint range, good speed, good price, and almost silent in operation. (I don't just like them I have 4 at home, and have installed them as upgrades to at least 3 other systems.  I also have found them to be reliable.) (IDE rather than SATA due to aging hardware I'm afraid)

Right. back to the matter at hand.
now plug in your old drive to the secondary port on your cable (if it's IDE) or onto a secondary SATA port (if it's sata).
It can get confusing at this stage, but don't forget to make sure you know which disk is which.
At this stage, don't forget that even though the second disk is installed, all boot options are happening on the first disk, your second disk is not used(at the moment)
Now, decide what you want to boot by default. At this stage, you need to decide if you are going to use your F8 option or if you are going to dual boot. 
If you decide to use your F8 option, then set the default to whatever you wish it to be in the bios. 
Lets assume that you want to keep your primary as ubuntu, and your secondary as windows.
select your primary boot device to be your secondary hard disk (your original) 
boot form your windows CD and then select your OLD disk, and wipe all the data off it, (remove all the partitions and re-partition it as FAT32, or NTFS (NTFS would be preferred, but you'll need additional linux tools to read and write to it.)

Then Tell windows to install to the new blank partition and do what you have to do for this.

I go a bit flakey here as one of two things will / may happen.
As it's a clone of the first disk, windows MAY write it's boot partition to the primary hard disk anyway and goose your install of Grub for Ubuntu. OR, the install will just write a new boot sector to the second disk drive (Which is what we want) and leave your ubuntu alone.

In case the first option happens, can "we" advise how to secure the grub files and process to recover Grub on the first disk please of gods of ubuntu?

Lets assume that windows does what it is bloody well told :), and installs everything to the old-disk. you then have nearly what you want, with the exception of wiping the additional and no longer required windows data from the primary disk.

BTW you can get grub to present the menu for booting from different partitions and disks if you like. but I'd need to know more grub than I do to tell you how to do this but it's quite straight forward from memory.
I'm not sure how, or even if, windows boot loader could handle it the other way round, I'm sure it can if you have 2 installs of windows, but not windows and A.N.Other O/S.

Good luck, and don't foget, you still have your boot CD and your backup you made so if all else fails, wipe and get back to where you were.

Ps sorry for the huge text tomb.  but it's broken down into straightforward steps as far as I can see.

---

### Post by rock-hopper on 2007-09-18
Thanks again to everyone, and particularly to Mr Beast for preparing such a detailed How-to for me.

I was a little nervous to start with on joining the Forum - almost everyone has heard terrible things about Linux geeks who spit and snarl and yell RTFM at newbies like myself - happily I have found the exact opposite here and people only too ready to share their thoughts and knowledge.

Thank you all - perhaps in a day or two I can actually get down to finding out what Ubuntu can really do rather than worry about getting it going.

Very best regards,

rock-hopper

---

