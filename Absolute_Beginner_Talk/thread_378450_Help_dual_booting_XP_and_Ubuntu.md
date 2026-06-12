---
title: "Help dual booting XP and Ubuntu"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Cannonade on 2007-03-07
I need a little bit of help dual booting XP and ubuntu on separate hard drives. My master drive is an 80GB drive with XP Professional installed and my slave will be, when it arrives, a 250GB drive which I intend to install Ubuntu 6.10 onto. I have been using Ubuntu on my laptop for a few weeks, but my laptop is a little too pathetic to run anything, so I would like an install on my main computer.

I've read around some of the posts about how to get this to work. Sadly, I notice it involves unplugging XP drives and editting the boot files. I'm completely new to Linux and I hate messing with the internals of my computer, mainly because I need my computer for uni and I'm lost without it! Is there anyway I can install ubuntu to my slave drive without having to physically unplug my master? I've checked in my bios, and it's rubbish, all I can do is change the boot order. In previous machines I've built myself, I can disable the hard drive in the bios. However, this is a cannibalised Compaq machine and the BIOS is somewhat limited.

Also, I've read posts that say to edit grub to pick up Windows. I have a program called bootpart that changes the Windows boot.ini to pick up other OS like Linux, and it's supposed to work. Could I also use this to boot to Linux? I trialled this when tyring to boot Sabayon Linux from an external drive, and it picked up the Linux install, but grub had troubled with by USS HDD.

Thanks in advance for any help.
Cannonade

---

### Post by mikewhatever on 2007-03-07
One reason people unplug the Windows HDD is to make sure GRUB goes to the right place, namely Ubuntu HDD MBR. Since you do not plan installing GRUB, there may be no need to do that. I think you'll aso be better of with Altarnate installer which lets you skip GRUB installation. 
One more reason I can think of for unplugging the HDD is to have less confusion while setting up partitions.

---

### Post by tocleora on 2007-03-07
If I understand correctly, I haven't tried it with newer versions of Linux but I'd say around Red Hat 7.2(?) I was running Linux on a secondary hard drive and Windows on the primary hard drive.  I was able to install Red Hat normally without having to do anything special, it put the boot loader (could have been grub by then) on the primary hard drive and everything worked correctly.  I could be wrong though that was a long time ago now.  Now there was a point where I did just what you're talking about so I could keep them completely separate, I unplugged my primary hard drive, installed Linux to my secondary hard drive, then what I'd do is turn the primary drive on and off in bios, on to run windows, off to run linux.  Then Grub wasn't installed on my primary hard drive and therefore didn't affect it in any way.  I would assume you wouldn't be switching back and forth a lot (I only go to windows to play games now) so it wouldn't be as painful as it might seem.  Sounds like you have options though...

---

### Post by ArieT on 2007-03-07
I think it works if you change the boot order of the two harddisks. You must ensure youself that the Linux disk boots first. After that you could install Ubuntu onto this harddisk. Ubuntu should detect Window automatically and ads an entry in the grub bootmenu. I thinks this is all you have to do but you'd better wait for someone to confirm this.

PS: unplugging your Windows harddrive is only for your own safety. You can't format accidentally your unplugged hard drive accidentally  ;-)

---

### Post by Sbarton on 2007-03-07
For dual booting this site is very informative, have a look around it!
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
regards

---

### Post by Cannonade on 2007-03-07
Cheers, thanks for the advice!

mikewhatever, you mentioned about not planning to install grub. When I first tried Sabayon Linux on the external, the first thing I told it to do was not to install grub. (I was hoping the just switch the boot priorities in the BIOS between my internal and USB HDD). However, everytime I tried to boot I just had the error "Missing Operating System". Now, I know there is a problem booting from USB hard discs, I was wondering if I'd encounter this same problem if not installing grub onto my internal slave.

Also, just to make sure, if I did install grub on my XP drive (I don't mind repairing the MBR from the XP disc so long as it works!), would it boot Windows ok? I'm a little worried about it not booting Windows ok, I need it for games and for MathCAD and Excel. But if there is no problems installing grub to the XP drive, I'd have no problems doing it if it didn't mess up XP.

The problem is, I am not sure if this bootpart program I have works properly. Seeing as the only time I've tried it is with a USB HDD, I'm not sure whether the problem is bootpart or the external drive! If it doesn't work properly, can I easily install the grub bootloader onto my Linux drive after ubuntu is installed?

---

### Post by confused57 on 2007-03-07
> **mikewhatever said:**
> One reason people unplug the Windows HDD is to make sure GRUB goes to the right place, namely Ubuntu HDD MBR. Since you do not plan installing GRUB, there may be no need to do that. I think you'll aso be better of with Altarnate installer which lets you skip GRUB installation. 
One more reason I can think of for unplugging the HDD is to have less confusion while setting up partitions.
I agree with mikewhatever's suggestion to use the alternate cd, it allows you to have better control of your installation and where to install grub.  I don't know anything about bootpart, but you can select not to install grub on your initial install & see if bootpart will boot Ubuntu.

If you need to install grub to the root partition(or the 2nd hard drive mbr) to get bootpart to work, then you could use the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Another option with the alternate cd would be to install grub to a floppy, which you would have to boot into Ubuntu temporarily.

Another suggestion, which you might consider is to select your slave drive as your first hard drive in your bios boot sequence before install Ubuntu...use the alternate cd, when asked to install grub to the mbr, select "no", then you will be taken to another screen where you can select where you want to install...type in **/dev/hdb**...this will install grub to your 2nd hard drive mbr and you can boot Windows or Ubuntu from grub.

This should give you a few options...take your pick.

---

### Post by Cannonade on 2007-03-07
I'm a little confused with the alternate CD and the standard one with the grub loader. I downloaded a 1.59GB file of Ubuntu Ultimate 1.2 and looked at the install for that. When it listed me the details for my install, it said it was going to install grub to (hd0). I could click on this bit and a little box came up. I could change the (hd0) field, but I'm not sure what to change it to.

Is this where I can type in /dev/hdb?

I'm a little confused, I've not long changed to trying to dual boot Linux, the only things I've dual booted is Windows 2000 and Windows 95.

---

### Post by confused57 on 2007-03-07
> **Cannonade said:**
> I'm a little confused with the alternate CD and the standard one with the grub loader. I downloaded a 1.59GB file of Ubuntu Ultimate 1.2 and looked at the install for that. When it listed me the details for my install, it said it was going to install grub to (hd0). I could click on this bit and a little box came up. I could change the (hd0) field, but I'm not sure what to change it to.

Is this where I can type in /dev/hdb?

I'm a little confused, I've not long changed to trying to dual boot Linux, the only things I've dual booted is Windows 2000 and Windows 95.

I'm not familiar with the Ultimate 1.2...but I would think this is where you could type in /dev/hdb...make sure your slave drive is selected as the first hard drive booted in bios(before your master drive with Windows) before you begin the installation...you'd need to leave your system setup this way...

Set up this way, your slave drive "should" be recognized as hd0 in grub(therefore opting to install on hd0 should be OK, also...I can't really guarantee this, but I believe that will be th e case) and your master drive would be hd1.  I've always used the alternate cd, but designating /dev/hdb should work the same in the live cd.

If you'd rather, you can wait on someone else to verify this.

---

### Post by kittyhawk63 on 2007-03-07
Cannonade.
I also have a Compaq system. Just testing out different Ubuntu versions I have installed Dapper and Edgy several times over the past few weeks. I just finished a few minutes ago of doing a full install of Edgy from a CD Live disk which I made from downloading a .tar file off the Internet.
 The easiest way that I have found is to remove your Windows HDD. Make it a slave drive. Make your new 250GB HDD your Master. With a Live CD in your CD ROM drive boot up. Once the Live CD comes to the desktop and everything seems "quiet", choose "Install". Let the program start to install itself. During the install, you can choose to partition as you desire. I let it use the entire disk. I'm not interested in partitioning my 80 GB HDD. Once you have the program installed, you can reattach the Windows HDD. Reboot and both of your HDDs will (or should) be recognized. You choose then which you want to go into. Hope this helps. It has worked for me every time using this method. If you have built a computer before, removing and putting back the HDD will be a cinch.
kh

---

### Post by Cannonade on 2007-03-07
Well, I downloaded the iso for the alternate CD and started to install with text. It gave me the option also to install with OEM or with command line. It all went well, though I was a little worried when it started formatting the partitions to my drive before the process was finished. Then it asked me to type in my user details, and then it started set up the DHCP. Then it starts installing base system. At this point, I'm starting to panic because it hasn't asked me anything about grub.

However, when it was installing, I get a message below the progress bar that says "retrieving ..." with a file. However I then got an error back about several files being corrupt. I click on continue, and then I get another error that says "cannot download package". It does this continuously. I thought it might be an error on the iso file, but I ran an md5 checksum test and that compared fine with the md5 sum I got from the mirror site.

At the moment, because it doesn't look my hard drive wont be turning up for a while, I'm still trying to get it to work with my USB HDD. So whether this is the problem, I'm not sure, but at that time, it seemed to be reading the CD rather than writing to the hard disc.

---

### Post by kittyhawk63 on 2007-03-07
Cannonade,
You may be a little over my head on this one. I am still relatively new to Linux. However, did you partition your present HDD to take a new OS? Do you know how to install to a new partition? When I installed Edgy as a fresh install on my HDD, I did not get any notice of Grub. I assumed Edgy placed it on the Linux HDD. Not sure about that. There is a way to find out. I will have to ask someone for the sudo command.
Don't give up, someone will be able to help you. "Taurus" is a good encyclopedia on these matters. He knows quite a bit about Linux. He is on this site most every day. Maestro23 is also helpful, as are others.
Sorry, I can't help you out any more. I've told you all I know so far.

---

### Post by Cannonade on 2007-03-07
When I partition the drive, I ask it to erase the drive completely and use the entire drive for the partitions. It automatically partitions the drive. I bought that drive specifically to install Linux onto, so I have no other partitions on it for anything else. The only thing that was on it was an install of Sabayon I couldn't get to boot due to an issue with USB hard discs.

I'm still waiting for my hard drive to turn up (I ordered it with a network card, which is waiting for restocking, so it'll take a while). So I'm currently attemping to install ubuntu to my external drive.

The easiest solution is what I did with my laptop, which was remove Windows and run ubuntu off one drive! But cannot make the switch completely yet, due to things I still need Windows for.

I may have better luck when my internal drive arrives.

PS. Sorry, the drive I want to install ubuntu to is picked up as sda, not hdb. (It shows both of my USB hard discs as sdx)

---

### Post by kittyhawk63 on 2007-03-07
Canonade, 
If you don't get any replies you may want to repost with "Unresolved" by your tag. Go to your original post and click "Edit". Then you click on "Advanced Edit". Toward the top of the page you will see several choices that will tell others reading your post whether it is resolved or unresolved. Choose the Unresolved. Scroll down and click on Save. 
When you have your answer and all is well, come back here and choose resolved. That will let others who are having a similar problem know that they can look at your post and possibly fix their problem. It will also let others know that you no longer need help.
Sure hope that you can get this figured out soon. 
kh

---

### Post by kittyhawk63 on 2007-03-07
Cannonade,
If you downloaded an ISO and burned it to CD, what rate did you burn the CD? If you did it faster than 4X, you will probably have problems. I highly recommend not to burn it faster than 1X. You will get the best quality at that speed.

If you burned faster than 4X, I suggests you burn another CD. If it is a CD-RW, erase it and burn it at 4X or slower. I am heading out for my daily six mile walk. Hope to hear that you were able to get your problem fixed when I return in a couple hours.
kh

---

### Post by Cannonade on 2007-03-07
> **kittyhawk63 said:**
> Cannonade,
If you downloaded an ISO and burned it to CD, what rate did you burn the CD?

I burn the CD at 4x, it wont go any higher with the discs I have.

I've recently tried something else. I went back to my DVD disc of Ubuntu Ultimate 1.2, went through the config, etc etc, until it asked me where to install the bootloader. I changed (hd0) to /dev/sda as previously suggested. It went though the install fine on the external HDD (I had to eject it first to get it to partition). I switched the drive priorities in the BIOS also.

So I boot to Linux when the install is complete with the BIOS set to have the external as the first boot, as I had when I installed it. Now, when I tried with Sabayon, I simply got a screen with the words GRUB and a flashing cursor after it. This time with ubuntu, I get something which looks a little more promising, even though it still doesn't boot! I get something like:

grub stage 1.5

something about initiating, I can't remember exactly
error 18

Any help with this? Maybe I need to tell it to install grub to /dev/sda1 instead of just /sda?

---

### Post by confused57 on 2007-03-07
> **Cannonade said:**
> I burn the CD at 4x, it wont go any higher with the discs I have.

I've recently tried something else. I went back to my DVD disc of Ubuntu Ultimate 1.2, went through the config, etc etc, until it asked me where to install the bootloader. I changed (hd0) to /dev/sda as previously suggested. It went though the install fine on the external HDD (I had to eject it first to get it to partition). I switched the drive priorities in the BIOS also.

So I boot to Linux when the install is complete with the BIOS set to have the external as the first boot, as I had when I installed it. Now, when I tried with Sabayon, I simply got a screen with the words GRUB and a flashing cursor after it. This time with ubuntu, I get something which looks a little more promising, even though it still doesn't boot! I get something like:

grub stage 1.5

something about initiating, I can't remember exactly
error 18

Any help with this? Maybe I need to tell it to install grub to /dev/sda1 instead of just /sda?

Installing to an external hard drive can be difficult on some systems...what you can try is boot to your external drive, in the grub menu, highlight the entry to boot Ubuntu, press "e" to edit, then change the line with root to (hd0,0), then press "b" to boot...if it works, this is temporary, but you can make it permanent in your boot/grub/menu.lst.

See the link in my signature for Dualboot with 2 hard drives for editing.
Don't install grub to /dev/sda1, that is your root partition.../dev/sda is the mbr.

---

### Post by Cannonade on 2007-03-07
> **confused57 said:**
> Installing to an external hard drive can be difficult on some systems...what you can try is boot to your external drive, in the grub menu, highlight the entry to boot Ubuntu, press "e" to edit, then change the line with root to (hd0,0), then press "b" to boot...if it works, this is temporary, but you can make it permanent in your boot/grub/menu.lst.

See the link in my signature for Dualboot with 2 hard drives for editing.
Don't install grub to /dev/sda1, that is your root partition.../dev/sda is the mbr.

Thing is, I don't get a grub menu come up asking me to boot to an operating system. I just get the stage 1.5 bit and it ends with error 18. Then a little flashing cursor you can't type anything into.

To edit the grub menu.lst, I think I can possibly get at it if I boot from the liveCD and access my external drive. I could do this with the Sabayon install, except I didn't have permission to access the file, so could do nothing with it!

---

### Post by kittyhawk63 on 2007-03-07
Cannonade,
Someone else is having your problem. See the newest posts. He mentions the error 18. There are some suggestions to fix his problem.
kh

---

### Post by confused57 on 2007-03-07
See this link for mounting a Linux partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

May be something in this thread that will help:
[http://www.ubuntuforums.org/showthread.php?t=363306&page=4](http://www.ubuntuforums.org/showthread.php?t=363306&page=4)

---

### Post by Cannonade on 2007-03-07
Right, I know that I have Ubuntu sitting on my external hard drive because I'm using it right now! I still get the error 18 message when booting from the drive.

I tried using my Ultimate Boot CD, which has super grub on it. From this, I was able to access the hard drive which has my Linux installed (hd1 according to the CD) and I booted from the master boot record.

It went through fine and I got a nice little menu up listing ubuntu, ubuntu restore, memory check and Windows XP Professional. I booted into Linux and, amazingly, I now have ubuntu loaded on my computer!

Now the problem is getting into ubuntu without the use of this super grub disc.

---

### Post by mikewhatever on 2007-03-07
Can you please open the terminal (Application->Accessories->Terminal) and post the output of the following:
> sudo fdisk -l
sudo gedit /boot/grub/menu.lst
sudo gedit /boot/grub/device.map

---

### Post by robophred on 2007-03-07
I set up my dual boot do use the basic XP boot loader to run grub, and from there run Ubuntu.

See this site:
[http://www.oreillynet.com/pub/h/2337](http://www.oreillynet.com/pub/h/2337)

---

### Post by confused57 on 2007-03-07
> **Cannonade said:**
> Right, I know that I have Ubuntu sitting on my external hard drive because I'm using it right now! I still get the error 18 message when booting from the drive.

I tried using my Ultimate Boot CD, which has super grub on it. From this, I was able to access the hard drive which has my Linux installed (hd1 according to the CD) and I booted from the master boot record.

It went through fine and I got a nice little menu up listing ubuntu, ubuntu restore, memory check and Windows XP Professional. I booted into Linux and, amazingly, I now have ubuntu loaded on my computer!

Now the problem is getting into ubuntu without the use of this super grub disc.

Ubuntu is recognized as hd1 by super grub, because you probably had the internal drive selected in bios to boot before the external hard drive when you installed Ubuntu.  After installing Ubuntu, then when you select to boot first to your external hard it is recognized as hd0 by grub, but your menu.lst has already been written to show hd1, for example root  (hd1,0).
You've probably seen the solutions for error 18  in this link in other threads:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

Some people have found shrinking the root partition helps, I don't know if this would help you or not.
The link robophred gave sounds like a possibility, since you're able to boot into Ubuntu with super grub.

See the reply by Herman in this thread:
[http://www.ubuntuforums.org/showthread.php?t=311774](http://www.ubuntuforums.org/showthread.php?t=311774)

Here is Herman's website, excellent information about bootloaders,etc:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Cannonade on 2007-03-08
Thanks for all the feedback guys!

This morning, things have taken a different turn. With the drive Ubuntu is installed to being a USB drive, the BIOS always changes my main boot drive back to Windows, the internal. So I tried to boot into Ubuntu this morning (it is now hd2 rather than hd1) and I get an error 15 file not found.

I change the boot order back with the Ubuntu drive first and still the same problem. This is booting from the Ultimate Boot CD, super grub disc. However, I also plugged my J: drive, which is my second external drive containing music, videos, downloads, etc. This may have effected my boot order and caused this error.

I am going to try again with J: unplugged and see if I can get anywhere.

However, my hard drive is coming in tomorrow, so I'll be able to get that installed. Then I can change the jumpers round and make sure that the Ubuntu drive is the primary and get to start on the proper work of getting Linux bootable. I was just using the external drive to 'practice on' so to speak!

PS. The BIOS picks up my external hard drive as being 250GB and it is a new computer, only bought new last year. I will be able to tell whether it's a BIOS problem rather than a USB HDD problem tomorrow when my IDE drive comes.

---

### Post by Cannonade on 2007-03-08
Ok, so I removed J: drive from the system before rebooting and making sure my external HDD was down as the first boot disc. I got into super grub, boot from the mbr of hd1 and I get the lovely grub menu up asking for ubuntu or XP. I select ubuntu and magically, I have ubuntu!

I believe the problem here is either because I didn't have the J: drive plugged in when I installed ubuntu or because the BIOS changes the boot priority when both USB drives are plugged. Sadly, they are both exactly the same drive, so the BIOS picks them up with the same name, except one is HDD0 and the other is HDD1!

I am now trialling editting the grub to try and get it to boot. I know someone with the same problem (having XP on an IDE drive and ubuntu on a SATA drive) who has solved his problem. Then I will know exactly what to do when my external drive arrives.

---

### Post by confused57 on 2007-03-08
> **Cannonade said:**
> Ok, so I removed J: drive from the system before rebooting and making sure my external HDD was down as the first boot disc. I got into super grub, boot from the mbr of hd1 and I get the lovely grub menu up asking for ubuntu or XP. I select ubuntu and magically, I have ubuntu!

I believe the problem here is either because I didn't have the J: drive plugged in when I installed ubuntu or because the BIOS changes the boot priority when both USB drives are plugged. Sadly, they are both exactly the same drive, so the BIOS picks them up with the same name, except one is HDD0 and the other is HDD1!

I am now trialling editting the grub to try and get it to boot. I know someone with the same problem (having XP on an IDE drive and ubuntu on a SATA drive) who has solved his problem. Then I will know exactly what to do when my external drive arrives.
You're right if you plugged in the other external drive after installing Ubuntu, that could very well change how grub sees the order of your hard drives...which would necessitate switching the drives(external) around or editing grub to account for the new hard drive designation(hd1, hd2)...booting first to your Ubuntu external hard drive, it will  be recognized as hd0, regardless of how your rearrange any other drives....Good luck.

---

### Post by Cannonade on 2007-03-08
Ok I have had a go at editting the grub file, but still no success. I get stuck at:

grub stage 1.5
loading grub...
Error 18

With no menu coming up at all, just this. The only way I can boot in is still using the super grub disc. I have editted menu.lst in the following way:
It used to read:

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

Then I changed the last part to:

title		Microsoft Windows XP Professional

map (hd1) (hd0)

map (hd0) (hd1)

rootnoverify (hd1,0)

savedefault

makeactive

chainloader	+1

But still no luck. I also tried changing the root of the ubuntu bit to (hd0,0) instead of (hd1,0) but this didn't solve it either. In fact, it also made things worse because I got an error back from the super grub saying: Error 17 cannot mount selected partition, and refused to boot.

---

### Post by Cannonade on 2007-03-08
> **mikewhatever said:**
> Can you please open the terminal (Application->Accessories->Terminal) and post the output of the following:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

This is what I get from typing sudo fdisk -l

My device.map is
(hd0,0) hda
(hd1,0) sda

---

### Post by 4seasonphotos on 2007-03-08
Well I am brand new to this and I just loaded Ubuntu on my pc from a cd. I used Gpart on the cd and partitioned my HD made two partitions apart from the XP partition. One for the Ubuntu program and another small one for the swap temp memory storage.. I don't know if I did it right but my pc works and Ubuntu works as well as the dual booting works.. So I did something right.. 

Hope this helps in some way..

Dave

---

### Post by dstew on 2007-03-08
Your device.map file seems to be incorrect. You are mapping partitions to drives. Shouldn't it be 

(hd0) hda
(hd1) sda

?

---

### Post by Cannonade on 2007-03-08
> **dstew said:**
> Your device.map file seems to be incorrect. You are mapping partitions to drives. Shouldn't it be 

(hd0) hda
(hd1) sda

?

#-o oops! yeah, sorry 'bout that!

(hd0) /dev/hda
(hd1) /dev/sda

---

### Post by Cannonade on 2007-03-09
Right, I now have my second internal drive but I still have problems.

Firstly, I formatted my 250GB IDE drive with half of the partition as NTFS and the other half for Linux. So I now have technically 4 drives. hda (Windows), hdb5 (NTFS parition), hdb2 (Ubuntu) and sda (USB hard drive for storage), Fat32).

The Linux section of the drive has two partitions, hdb2 and hdb3 and I installed grub to /dev/hdb the master boot record for that drive. Everything went well. Although hdb is the slave drive and hda is the master, I can make the BIOS happily boot from hdb first and this gives me the grub menu.

However, when I go to boot ubuntu, I now get Error 22: No such partition.

Now I have editted the menu.lst file as before, changing the drive mapping with hd1 and hd0 both way round, and still no such luck.

However, I have noticed that the root for ubuntu, instead of being hd1,0 is now hd1,1. Is this likely to be the problem? If this is a problem, I know my BIOS will boot from a 250GB hard drive, so will happily erase the disc and start again with Linux taking up the whole drive.

Thanks again for any help!
Cannonade

PS. My device map is as follows:

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda

---

### Post by dstew on 2007-03-09
I think you must also have hdb1. Grub is finding its menu ok, so it must be unable to find the kernel. Assuming that the /boot/grub/menu.lst file is on hd1,1 which is probably hdb2, your root line in the menu.lst item for your Ubuntu kernel should also be (hd1,1). Check that first. Also, to make sure, you can go to the  grub command line and type

grub> find /boot/vmlinuz-2.6.17-11-generic

It should come back with (hd1,1). If it does not, change the root entry in your menu.lst to the true location of your kernel, save, reboot, and see what happens. However, if your kernel is on a different partition than /boot/grub/menu.lst you have more problems. That would indicate that you might have two linux installations, in two different places.

---

### Post by confused57 on 2007-03-09
Did you have your hdb slave drive set as the first hard drive booted in bios?  If you didn't, what I would do if it were my system, is to set your hard drive boot sequence in bios to hdb(slave), hda(master), & sda(if it's only going to be for data storage, you could leave it disconnected during install)...in that order, before you try reinstalling Ubuntu.  You can still select to install grub to /dev/hdb...you'd need to leave your system set up that way(booting first to the slave drive).

I think I've given this link already, if you don't mind switching your Ubuntu to master & Windows as slave:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Cannonade on 2007-03-09
Yes, I did set my BIOS as the slave to be my first drive.

I've been checking my menu.lst file again. And have found that:

title     ubuntu ...kernel version...
root    (hd1,1)

title     Microsoft Windows XP Professional
root    (hd1,0)

Now, I was just thinking, shouldn't my ubuntu root be (hd0,0)? Or should that be Windows and ubuntu be (hd1,0)?

Just that both my hard drives are set to cable select on the jumpers, and to change them, I'd need to take the drives out and move them round so the cables can change. Which would be easier than taking the jumper off the pins on my new HD, which has proven troublesome. Also, would Windows object if I made it the slave? I don't really want to have to reinstall Windows.

---

### Post by dstew on 2007-03-09
I think you should figure out exactly where everything is before you change any disks around. Changing disk order physically or in BIOS can be very confusing to poor grub.

What was the output of grub> find /boot/vmlinuz-2.6.17-11-generic ?

That will tell you where your kernel really is, in grub-talk, and even if you have two kernels.

---

### Post by confused57 on 2007-03-09
> **Cannonade said:**
> Yes, I did set my BIOS as the slave to be my first drive.

I've been checking my menu.lst file again. And have found that:

title     ubuntu ...kernel version...
root    (hd1,1)

title     Microsoft Windows XP Professional
root    (hd1,0)

Now, I was just thinking, shouldn't my ubuntu root be (hd0,0)? Or should that be Windows and ubuntu be (hd1,0)?

Just that both my hard drives are set to cable select on the jumpers, and to change them, I'd need to take the drives out and move them round so the cables can change. Which would be easier than taking the jumper off the pins on my new HD, which has proven troublesome. Also, would Windows object if I made it the slave? I don't really want to have to reinstall Windows.
I'm not sure what's going on with grub, but I believe your Ubuntu root partition should be (hd0,1)...Windows on root (hd1,0) should be correct, but you'd need mapping commands, e.g.
map (hd0) (hd1)
map (hd1) (hd0)

Try editing your Ubuntu entry in the grub menu at boot to root (hd0,1), by highlighting your Ubuntu, press "e", then edit, press "b" to boot.
Hard drive jumpers can definitely be troublesome to remove, I have to use a small pair of needlenose pliers.
Windows can definitely be happy as slave, with the mapping commands...See the dualboot with 2 hd in my signature(I think I've already referred you to this thread previously).

---

### Post by Cannonade on 2007-03-09
> **confused57 said:**
> Try editing your Ubuntu entry in the grub menu at boot to root (hd0,1), by highlighting your Ubuntu, press "e", then edit, press "b" to boot.

Yes, you were quite right. Changing the root for ubuntu to (hd0,1) did work. I can now boot in without the grub disc. So then, should I modify my menu.lst file to have all the ubuntu root entries (5 of them I think, yes I indeed have 2 kernels!) from (hd1,1) to (hd0,1)?

---

### Post by confused57 on 2007-03-09
> **Cannonade said:**
> Yes, you were quite right. Changing the root for ubuntu to (hd0,1) did work. I can now boot in without the grub disc. So then, should I modify my menu.lst file to have all the ubuntu root entries (5 of them I think, yes I indeed have 2 kernels!) from (hd1,1) to (hd0,1)?

As dstew mentioned, you may have 2 different Linux installations, you could determine this by opening a terminal & posting the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Another possibilty is that an entry was added to boot the Ubuntu install on your external drive...which could be the root (hd1,1).
You could determine this by looking at the kernel line in your menu.lst for each Ubuntu entry, your internal drive should have something like  root=/dev/hdb2 and your external drive would possibly have root=/dev/sdaX.

You can make your changes permanent in your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

---

### Post by Cannonade on 2007-03-09
Yes, I have now made the change to menu.lst.

I now have it working. I can boot into XP and ubuntu straight from the grub menu!

Thanks ever so much to you guys for helping me get this sorted! I can now enjoy my new system! Wonderful job, ace!:biggrin:

---

### Post by confused57 on 2007-03-09
> **Cannonade said:**
> Yes, I have now made the change to menu.lst.

I now have it working. I can boot into XP and ubuntu straight from the grub menu!

Thanks ever so much to you guys for helping me get this sorted! I can now enjoy my new system! Wonderful job, ace!:biggrin:
Good job, glad you were able to get it working OK.  You probably learned quite a lot & you'll be able to troubleshoot if you have problems booting.

---

