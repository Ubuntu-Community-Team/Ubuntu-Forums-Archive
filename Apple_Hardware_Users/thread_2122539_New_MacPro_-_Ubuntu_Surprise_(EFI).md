---
title: "New MacPro - Ubuntu Surprise (EFI)"
date: 2013-03-05
forum: Apple Hardware Users
---

### Post by crjackson on 2013-03-05
My new MacPro arrived in all it's glory yesterday. I had some grand plans of putting Ubuntu and Windows on, each with a drive to itself. I should have done some reading and researching first I suppose. I just learned that there is no BIOS for this xeon core beast. I know that it IS possible to install Ubuntu/Windows, but not in the manner I wanted. I'm a little disappointed but not heart broken.  I have several machines, all have Ubuntu, most dual boot to Windows too, and I was hoping for the same with this machine.

Well, OSX 10.8.2 is pure Unix, so at least I'm still loyal to the Nix family.  I have to say, I really am loving OSX and all the speed of this thing.  It inspired me to go out and buy a new monitor and update some of my peripherals.  They all still worked with OSX but I couldn't have this rock star machine crowded in with old outdated accessories.

I'm considering purchasing Parallels 8 for her.  I'm wondering if I could install Ubuntu / Windows 7 under Parallels and be without any performance hits, or other drawbacks. 

Any information or advice on the subject would be much appreciated.  Even if I can only run OSX, I'm still happy with her. I may as well be, considering the investment I've made.  It would be nice however to have the other OS's on here, since I support other Ubuntu / Windows machines for friends and family members.

Of course I know there are ways to force install each of the other OS's on the same drive using Boot Camp, but I'd rather not mess with the OSX drive until I'm very familiar it.

---

### Post by UltimateCat on 2013-03-06
Hi:;)

Your new Mac sounds really nice!

> i'd rather not mess with the OSX drive until I'm very familiar it. 		

If I were you I would get to know your system  well before proceeding with the Linux install but that's **just me-**

You would have to shrink your Mac partition and than allocate what space you would want for Ubuntu.

>   I'm wondering if I could install Ubuntu / Windows 7 under Parallels and be without any performance hits, or other drawbacks. 

I honestly don't know if there would be drawbacks; sorry
I'd get confirmation on that-:)

Here's a few links to help you install Ubuntu on your Mac-

[http://askubuntu.com/questions/151371/how-to-install-ubuntu-12-04-on-mac-os-x](http://askubuntu.com/questions/151371/how-to-install-ubuntu-12-04-on-mac-os-x)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)

If I had a Mac I would follow this video but disable the music. It's a tad distracting to be able to focus on a fresh install-
[http://www.youtube.com/watch?v=G0Ae1mSICO8](http://www.youtube.com/watch?v=G0Ae1mSICO8)

BTW Linux looks great on a Mac from what I have heard and read-
[http://www.zdnet.com/search?q=linux+on+a+mac](http://www.zdnet.com/search?q=linux+on+a+mac)

Good luck!

---

### Post by crjackson on 2013-03-06
Thanks for the reply.  I'll have a look at those links now.

---

### Post by buzzingrobot on 2013-03-07
I've followed this: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/) to successfully install Ubuntu on a MacBook Pro in EFI mode. It's a convoluted process. 

Apple created what is, in effect, a BIOS compatibility mode to facilitate running Windows with Bootcamp.  Ubuntu, and many other distributions, seem to install under that.  I know I can install a stock 12.04 LTS image on the MacBook with no problems.

My MacBook has two video cards. Choosing between the cards is only possible if the OS is installed in EFI. That was my motivation for trying the install.  

However, if your Pro only has a single video card, then the difference between an EFI install and a BIOS compatibility install might not be important.

I gave up on Linux on the MacBook due to excessive heat and maxed-out fans. Apple's software clearly has the edge there.

(FYI:  Fedora 18 installed in EFI mode on the MacBook with no hoop-jumping required.)

---

### Post by pelle.k on 2013-03-07
Hi. I'd recommend buying another HD for ubuntu and windows, that way you wont have to deal with a hybrid GPT/MBT partition table and the limitations that follow.
If you just want to run a virtualized ubuntu, for the moment vmware fusion runs it best (in fact, it's almost like running it natively). Virtualbox currently has some graphic glitches/issues with ubuntu 12.10.

---

### Post by crjackson on 2013-03-07
Well, I don't need to buy a HD, I have several in my old tower.  I was going to add three more to the Pro when I thought I could get away with installing each OS on it's own drive but it seems I can't do that without a real bios.  In my now retired system, I have Ubuntu on drive0 Windows7 on drive1 and data on drives3s&4.

What I typically do is install each OS on it's own drive (with) the other drives disconnected during the install. That way the boot record of each OS remains independent of the other.  Also, each OS drive has it's own dedicated Data drive.  One NTFS and one EXTx for data storage.  It also helps tremendously well for me because the OS drive works best when unencumbered by the video processing by that's going on in the data drive.  Video processing systems have special drive needs if you want to have speed and reliability.  It's just a hobby but I take my hobbies seriously.

I was hoping I could disconnect the OSX drive, install Ubuntu on a fresh drive, then disconnect those 2 and install windows on another, then add a huge data drive and partition it in different file formats to accommodate each OS for it's related data.  

It seems this is no longer possible due to no bios on the motherboard.  I'm a little disappointed but it's not a big deal.  I really intend on spending most of my time in OSX now, so it's not show stopper.  I do both Window / Ubuntu support for friends and family members and it helps to jump on the same OS i'm supporting when needed.  There are some good RDP and VNC tools for OSX that support both Windows/Ubuntu specifically so that much is covered anyway.

I have no intention of putting ANY OS on the same drive as my OSX.  Honestly, I'm in AWE of OSX Mountain Lion and all the Xeon cores.  This is absolutely the most advanced OS and hardware I've ever used (short of a mini, and even that wasn't as impressive).  I'm protecting my OSX install until I manage to come up with a OSX Full install Disc or USB.

I'll get around to making that happen next month probably.  Apple doesn't give out the Disc or the USB sticks anymore.  They now have NET recovery systems to go with restore partitions, so you have to do a little voodoo to make that happen.  I've looked at the procedure and it's pretty simple, but I have to purchase a separate copy of the OS from the app store first, then extract the proper files from the install package.  Pretty easy stuff.

I'm even thinking there might be a way to install OSX on each drive just to get the EFI on there in lieu of a bios, then installing the wanted OS and blowing away OSX on the individual drive and resizing the partition afterwards.  I think that might work, but I don't know how the system would behave when all three drives are eventually connected at the same time.  Not sure how to control the boot at that point, so more research will be needed.  It may not work at all, I don't know, just a thought. 

If anyone has any ideas along those lines, chime in and I'll play with it over the next month.

---

### Post by pelle.k on 2013-03-09
You can download the disk image and transfer it to a usb stick to reinstall ML just like you used to do with a DVD. If you purchased it preinstalled, hold option (alt) while clicking the "installed" button in the MAS to download it.

If you are unable to do so, you could do something like this (from memory, i did it a long time ago). Find the recovery partition:
```
diskutil list | grep -i recovery | grep -o disk.*
```
Mount it using:
```
diskutil mount <insert_outout_of_above_command_here>
```
Open it using finder, open the "Mac OSX Base System", and there you have the "Install OSX Mountain Lion" app. Run that, and start the download of a larger (full size) "install OSX Mountain Lion" app that will be placed in the /Applications folder (i think), but from what i can remember, it's important to not go through the actually reboot and install step, but to force quit the installer at that point (hold shift while scrubbing the apple menu, and "force quit" should become "force quit install osx mountain lion" instead) because the download is deleted if the installer is allowed to go through the full process.

Now with the (full) installation package in /Applications (acquired using one of the above methods), do something like this: [http://arstechnica.com/apple/2012/07/how-to-create-a-bootable-backup-mountain-lion-install-disk/](http://arstechnica.com/apple/2012/07/how-to-create-a-bootable-backup-mountain-lion-install-disk/)

Furthermore, you don't need to install OSX on every disk just to have an EFI on it. Just create a GPT partition table instead of a MBR partition table. An MBR partition table will still be emulated (up to 3 partitions, any more than that you need to specify with gptsync). At least i'm pretty sure that's the case...

---

### Post by supermariofan25 on 2013-03-10
First of all I don't have a Mac Pro... yet, but I do have a fair bit of experience with Macs as I have an iMac.
So you want to install Ubuntu on one HDD of the multiple HDD's in your Mac Pro, Well First you will need to make shure that you are able to back up you OS X partition so if something does go wrong you can always restore it. The second thing you need to do is to open Disk Utillity to partition the Hard Drive that you want to use, to do so open your Applications folder and open the Utilities folder inside there, inside you will find Disk Utility, another way you can do this is by pressing Command and Space together and then typing Disk Utility and pressing Enter. Lets say you are using the second HDD to install Ubuntu, this will usually be the second HDD in the list and have the identifier of disk1, you have to select that Disk and then select the Partition tab, in the drop down list that says "Current Layout" Select "2 Partitions", Click on the "Options" button and make shure that GUID Partition Map is selected then click Done, rename the first partition to Ubuntu and set its partition format to MS DOS FAT, rename the second partition to Linux Swap and and set the partition format to MS DOS FAT, next you will need to set the size of the Swap partition to 2 - 4GB's whichever one you want the swap to be, this makes shure that the Linux Swap isn't half of your HDD, next click "Partition" (It may help to turn off you computer and remove all hard drives except the First HDD in slot "1" and the hard drive that you wish to install Ubuntu on to minimise confusion). Once this is done you may insert your Ubuntu disk into the DVD drive and turn off your computer, If you want you can remove the OS X HDD in slot "1" so that Ubuntu only sees the HDD that you want to install to. When turning on your computer make shure you are holding down the Option/Alt key on your keyboard as this will open the OS selection menu, use your mouse or keyboard to select the "Windows" disk icon not the "EFI" disk icon, this will start the Ubuntu live CD so you can start the installation, pick either "Try Ubuntu Now" or "Install Ubuntu", I personally pick "Try Ubuntu Now" so I can setup Wifi, change some settings before installing, Go though setup as usuall until you get to the screen that says Choose installation type, Click "Something Else" instead of erasing the entire disk, once on the next screen you will need to select the First Partition of /dev/sdb (or /dev/sda if you chose to remove the OS X HDD before installing), click Change and set the partition type to ext4, set the mount point to "/" and check the Format option, click done and select the second partition, this partition should be 2-4 GB as it is the swap partition, set the partition type to Linux Swap and click done, next make shure the boot loader is set to install on /dev/sdb (or /dev/sda if you took all other HDD's out before hand), finally make shure that the first partition is highlighted and click Install, continue installation as usual until it finishes, when finished don't restart your computer as you will need to shut it down so you can insert the HDD with OS X on it if it was removed and then start up your computer, at this stage your computer will start up to OS X and not Ubuntu, this is fine as you will need to install rEFIt in order to be able to boot Ubuntu, to do so goto [http://refit.sourceforge.net/](http://refit.sourceforge.net/) and download the .DMG file from there, open the DMG file and select the installer file that is inside it, continue with the installation of rEFIt, make shure you check "Macintosh HD" as the install destination or it may stuff up your computer or just won't work properly. Once done you will be prompted to restart your computer, when booting nothing will show up and OS X will start as usual, your will need to restart a second time for the rEFIt menu to show up, once your Mac has restarted rEFIt should have shown up on your screen and you can select either Mac OS X or Linux, don't select Linux yet as you will need to open the Partition Tool at the bottom of your screen, it may or may not say that your partition table needs resyncing, if so type y and press Enter if not press Enter anyway, reboot once more than Select either OS X or Linux, Enjoy!
This method if done properly should work as the Mac EFI automatically knows if the BIOS emulation layer needs to be used and rEFIt handles booting Linux more better the the Mac EFI does, please note that rEFIt, even thou works very well, is outdated and may not work with future updates of OS X, but for now it works fine and is the best way to run Ubuntu on a Mac, hope this helps you on your quest to Triple boot OS X, Ubuntu and Windows on your new Mac Pro!

Best regards, supermariofan25

P.S. If this method doesn't work then try setting the Partition Table Map to Master Boot Record instead. Disclaimer, I have not tried this method before as I currently don't have a Mac with multiple hard drives and should only be used as a guide line so please do proceed at your own risk, I will update or remove this post later on when I do have access to a Macintosh with multiple hard drives in the near future. Therefore I do highly recommend that you make a backup of you entire OS X HDD with Time Machine on an external HDD before proceeding so that if anything does seem to go wrong then you can restore your Mac to its original condition.

---

### Post by supermariofan25 on 2013-03-10
> **crjackson said:**
>  I'm considering purchasing Parallels 8 for her.  I'm wondering if I could install Ubuntu / Windows 7 under Parallels and be without any performance hits, or other drawbacks.

Well It depends on what specs you have, my Quad Core iMac with 4 GB RAM runs Parallels 8 with Windows XP and both Mac OS X and Windows run slower than they would by the selfs and Mac OS X gets pretty slow when Windows XP is running in the background, but I gave half of the computers resources to the VM and I got the base model for 2011, but with you it may be a different story as you have 6 cores and 8 Gigs of RAM to distribute, graphics wise games can run fairly smoothly on the windows side as well as the Mac side with the VM running in the background and if you have enough resources (which you do) then you will able to run windows at half the power that it could be but it would still run smoothly.

---

### Post by supermariofan25 on 2013-03-10
> **crjackson said:**
> I don't know how the system would behave when all three drives are eventually connected at the same time.  Not sure how to control the boot at that point, so more research will be needed.  It may not work at all, I don't know, just a thought. 

If anyone has any ideas along those lines, chime in and I'll play with it over the next month.

Like I said in my previous post rEFIt is better for booting Linux based operating systems and is also a great help with triple booting.

---

### Post by crjackson on 2013-03-20
> **pelle.k said:**
> You can download the disk image and transfer it to a usb stick to reinstall ML just like you used to do with a DVD. If you purchased it preinstalled, hold option (alt) while clicking the "installed" button in the MAS to download it.

If you are unable to do so, you could do something like this (from memory, i did it a long time ago). Find the recovery partition:
```
diskutil list | grep -i recovery | grep -o disk.*
```
Mount it using:
```
diskutil mount <insert_outout_of_above_command_here>
```
Open it using finder, open the "Mac OSX Base System", and there you have the "Install OSX Mountain Lion" app. Run that, and start the download of a larger (full size) "install OSX Mountain Lion" app that will be placed in the /Applications folder (i think), but from what i can remember, it's important to not go through the actually reboot and install step, but to force quit the installer at that point (hold shift while scrubbing the apple menu, and "force quit" should become "force quit install osx mountain lion" instead) because the download is deleted if the installer is allowed to go through the full process.

Now with the (full) installation package in /Applications (acquired using one of the above methods), do something like this: [http://arstechnica.com/apple/2012/07/how-to-create-a-bootable-backup-mountain-lion-install-disk/](http://arstechnica.com/apple/2012/07/how-to-create-a-bootable-backup-mountain-lion-install-disk/)

Furthermore, you don't need to install OSX on every disk just to have an EFI on it. Just create a GPT partition table instead of a MBR partition table. An MBR partition table will still be emulated (up to 3 partitions, any more than that you need to specify with gptsync). At least i'm pretty sure that's the case...

Thanks for the great info.  I bought a new system with OSX preinstalled, so there was no way to download it without buying it again.  Which I did.  It trys to automatically install, but I just closed the install script, and then copied the install fille to 3 different safe places.  Then I tested each one to make sure it would start.  Then I deleted the one that was in my app folder (so no one - including me - could accidentally click on it).

Then I read the online methods for making install discs and thumb drives.  I made one of each, and tested each.  My Mac will boot from all of the back up copies, so I'm good there.

Thanks for your help.

---

### Post by crjackson on 2013-03-20
> **supermariofan25 said:**
> Like I said in my previous post rEFIt is better for booting Linux based operating systems and is also a great help with triple booting.

Actually, I'm still learning and loving OSX.  I haven't yet tried installing anything else yet.  I'm not going to do that until I can buy a new 4TB drive to play with and learn.  I'm protecting my original drive/install like it's gold at this point.  I've got to craw before I walk.

I did however make an rEFit USB stick and tried to boot 2 other intel laptops I own.  Neither worked past the boot selection screen that the USB stick presented.

---

### Post by crjackson on 2013-03-20
> **supermariofan25 said:**
> Well It depends on what specs you have, my Quad Core iMac with 4 GB RAM runs Parallels 8 with Windows XP and both Mac OS X and Windows run slower than they would by the selfs and Mac OS X gets pretty slow when Windows XP is running in the background, but I gave half of the computers resources to the VM and I got the base model for 2011, but with you it may be a different story as you have 6 cores and 8 Gigs of RAM to distribute, graphics wise games can run fairly smoothly on the windows side as well as the Mac side with the VM running in the background and if you have enough resources (which you do) then you will able to run windows at half the power that it could be but it would still run smoothly.

Right now I'm upgrading all my peripherals and adding a internal Blu-ray drive.  When finished, I'm going to upgrade memory to 32GB and the boot drive to SSD. I was originally purchasing the 12 core machine, but I found that the 6-core machine was faster (due to clock speed) for 99% of my usage.  I do dabble (only a little) with video editing and rendering that would have benefited more by the 12 core system, but given the small amount of dabbling, I opted for the faster core speed rather than the raw pulling power of the 12 core. The system is so much faster than my previous dual core system that I have no regrets at all. 

I'll prolly wait until I get an additional drive before playing with windows / linux on this machine.  OSX is VERY fast on this system, I'm astonished at it's speed really.  I can't wait to do the SSD / Memory upgrade.  I'm going to install a Sonnet card that provides SATA3 and 2 512 SSD cards in raid 0.

Thanks for the information.

---

### Post by crjackson on 2013-03-20
> **supermariofan25 said:**
> First of all I don't have a Mac Pro... yet, but I do have a fair bit of experience with Macs as I have an iMac.
So you want to install Ubuntu on one HDD of the multiple HDD's in your Mac Pro, Well First you will need to make shure that you are able to back up you OS X partition so if something does go wrong you can always restore it. The second thing you need to do is to open Disk Utillity to partition the Hard Drive that you want to use, to do so open your Applications folder and open the Utilities folder inside there, inside you will find Disk Utility, another way you can do this is by pressing Command and Space together and then typing Disk Utility and pressing Enter. Lets say you are using the second HDD to install Ubuntu, this will usually be the second HDD in the list and have the identifier of disk1, you have to select that Disk and then select the Partition tab, in the drop down list that says "Current Layout" Select "2 Partitions", Click on the "Options" button and make shure that GUID Partition Map is selected then click Done, rename the first partition to Ubuntu and set its partition format to MS DOS FAT, rename the second partition to Linux Swap and and set the partition format to MS DOS FAT, next you will need to set the size of the Swap partition to 2 - 4GB's whichever one you want the swap to be, this makes shure that the Linux Swap isn't half of your HDD, next click "Partition" (It may help to turn off you computer and remove all hard drives except the First HDD in slot "1" and the hard drive that you wish to install Ubuntu on to minimise confusion). Once this is done you may insert your Ubuntu disk into the DVD drive and turn off your computer, If you want you can remove the OS X HDD in slot "1" so that Ubuntu only sees the HDD that you want to install to. When turning on your computer make shure you are holding down the Option/Alt key on your keyboard as this will open the OS selection menu, use your mouse or keyboard to select the "Windows" disk icon not the "EFI" disk icon, this will start the Ubuntu live CD so you can start the installation, pick either "Try Ubuntu Now" or "Install Ubuntu", I personally pick "Try Ubuntu Now" so I can setup Wifi, change some settings before installing, Go though setup as usuall until you get to the screen that says Choose installation type, Click "Something Else" instead of erasing the entire disk, once on the next screen you will need to select the First Partition of /dev/sdb (or /dev/sda if you chose to remove the OS X HDD before installing), click Change and set the partition type to ext4, set the mount point to "/" and check the Format option, click done and select the second partition, this partition should be 2-4 GB as it is the swap partition, set the partition type to Linux Swap and click done, next make shure the boot loader is set to install on /dev/sdb (or /dev/sda if you took all other HDD's out before hand), finally make shure that the first partition is highlighted and click Install, continue installation as usual until it finishes, when finished don't restart your computer as you will need to shut it down so you can insert the HDD with OS X on it if it was removed and then start up your computer, at this stage your computer will start up to OS X and not Ubuntu, this is fine as you will need to install rEFIt in order to be able to boot Ubuntu, to do so goto [http://refit.sourceforge.net/](http://refit.sourceforge.net/) and download the .DMG file from there, open the DMG file and select the installer file that is inside it, continue with the installation of rEFIt, make shure you check "Macintosh HD" as the install destination or it may stuff up your computer or just won't work properly. Once done you will be prompted to restart your computer, when booting nothing will show up and OS X will start as usual, your will need to restart a second time for the rEFIt menu to show up, once your Mac has restarted rEFIt should have shown up on your screen and you can select either Mac OS X or Linux, don't select Linux yet as you will need to open the Partition Tool at the bottom of your screen, it may or may not say that your partition table needs resyncing, if so type y and press Enter if not press Enter anyway, reboot once more than Select either OS X or Linux, Enjoy!
This method if done properly should work as the Mac EFI automatically knows if the BIOS emulation layer needs to be used and rEFIt handles booting Linux more better the the Mac EFI does, please note that rEFIt, even thou works very well, is outdated and may not work with future updates of OS X, but for now it works fine and is the best way to run Ubuntu on a Mac, hope this helps you on your quest to Triple boot OS X, Ubuntu and Windows on your new Mac Pro!

Best regards, supermariofan25

P.S. If this method doesn't work then try setting the Partition Table Map to Master Boot Record instead. Disclaimer, I have not tried this method before as I currently don't have a Mac with multiple hard drives and should only be used as a guide line so please do proceed at your own risk, I will update or remove this post later on when I do have access to a Macintosh with multiple hard drives in the near future. Therefore I do highly recommend that you make a backup of you entire OS X HDD with Time Machine on an external HDD before proceeding so that if anything does seem to go wrong then you can restore your Mac to its original condition.

I really appreciate the time you took to make this post.  I'm quoting the entire post just in case you decide to remove it, I'll still be able to refer back to it.  I actually do have 2 other drives already installed, but one is a data drive and the other is a BU drive for time machine.

I actually want to take a fresh drive (all other drives removed) and install Ubuntu there along with rEFIt that is needed to boot. Then I'd like to pop all the drives back into there desired places and see if I can use the command key to select the rEFIt / Ubuntu drive without disturbing the OSX drive.  I realize I would end up having to navigate through to boot menus (if this works) but that's fine too.  If possible, I'd prefer NOT to have rEFIt on my OSX drive.  This may not be possible, but that's what I'm hoping for.

---

### Post by crjackson on 2013-03-23
Okay, I realize we've kind of covered this already, but I do have this nagging question I hope I can get answered befoe I take the plunge. I can boot to the Ubuntu CD perfectly as with any other PC.  If I install a clean HD and disconnect the OSX drive, will simply installing to a clean drive work without the rEFIt solution?  Probably not, but I just don't see how it can boot the CD (oh wait, does it read the EFI on the HD before it try's to boot the CD?  I bet that's it).

[ATTACH=CONFIG]240472[/ATTACH]

I've got to say, I've never seen a faster Ubuntu session.  I guess my old system with a dual core 2.4GHz AMD CPU was a dog comparatively speaking.  Man, everything worked... Wireless, MagicMouse, Sound etc...  I was a great surprise, but the biggest surprise was the quickness.  Now don't get me wrong, OS X is blazingly fast on this system and just as snappy as Ubuntu, but when I compare Ubuntu on this system to my old system... Well... It was shocking to say the least.  Like I said, I guess my old system was a dog and I didn't know it.

---

### Post by supermariofan25 on 2013-03-26
> **crjackson said:**
> Actually, I'm still learning and loving OSX.  I haven't yet tried installing anything else yet.  I'm not going to do that until I can buy a new 4GB drive to play with and learn.  I'm protecting my original drive/install like it's gold at this point.  I've got to craw before I walk.

I did however make an rEFit USB stick and tried to boot 2 other intel laptops I own.  Neither worked past the boot selection screen that the USB stick presented.

Where they Mac laptops or PC laptops? if they where PC laptops then rEFIt doesn't work with PC laptops, even with UEFI

---

### Post by supermariofan25 on 2013-03-26
> **crjackson said:**
> Okay, I realize we've kind of covered this already, but I do have this nagging question I hope I can get answered befoe I take the plunge. I can boot to the Ubuntu CD perfectly as with any other PC.  If I install a clean HD and disconnect the OSX drive, will simply installing to a clean drive work without the rEFIt solution?  Probably not, but I just don't see how it can boot the CD (oh wait, does it read the EFI on the HD before it try's to boot the CD?  I bet that's it).

[ATTACH=CONFIG]240472[/ATTACH]

I've got to say, I've never seen a faster Ubuntu session.  I guess my old system with a dual core 2.4GHz AMD CPU was a dog comparatively speaking.  Man, everything worked... Wireless, MagicMouse, Sound etc...  I was a great surprise, but the biggest surprise was the quickness.  Now don't get me wrong, OS X is blazingly fast on this system and just as snappy as Ubuntu, but when I compare Ubuntu on this system to my old system... Well... It was shocking to say the least.  Like I said, I guess my old system was a dog and I didn't know it.

Seems like you already have the CD/DVD booted anyway, good luck!

---

### Post by supermariofan25 on 2013-03-26
> **crjackson said:**
> I really appreciate the time you took to make this post.  I'm quoting the entire post just in case you decide to remove it, I'll still be able to refer back to it.  I actually do have 2 other drives already installed, but one is a data drive and the other is a BU drive for time machine.

I actually want to take a fresh drive (all other drives removed) and install Ubuntu there along with rEFIt that is needed to boot. Then I'd like to pop all the drives back into there desired places and see if I can use the command key to select the rEFIt / Ubuntu drive without disturbing the OSX drive.  I realize I would end up having to navigate through to boot menus (if this works) but that's fine too.  If possible, I'd prefer NOT to have rEFIt on my OSX drive.  This may not be possible, but that's what I'm hoping for.

Dont worry, Im not going to remove it :) in fact im thinking of reposting it more spaced out and with steps so its easier to read and understand

---

### Post by crjackson on 2013-04-02
> **supermariofan25 said:**
> Where they Mac laptops or PC laptops? if they where PC laptops then rEFIt doesn't work with PC laptops, even with UEFI

Sorry for the belated reply, I've been under the weather.  They were PC laptops with Core2Duo processors and i5 processors with Intel Video.  An OSX without rEFIt does nothing at all on these systems, with rEFIt I get to the rEFIt boot screen and that's as far as it goes.  It won't even give me a flashing cursor without rEFIt.  I thought that was the point of the rEFIt loader (to provided an EFI emulation so that a non-Mac could boot).  How else would you get a non-Mac to boot OSX then.

---

### Post by crjackson on 2013-04-02
> **supermariofan25 said:**
> Seems like you already have the CD/DVD booted anyway, good luck!

Yeah, but I'm thinking it had some help from the OSX HD or something.  I could be wrong.  As soon as I'm feeling well again, I'll crack it open and pull the boot drive, and then see if it'll boot the CD.  If it does, I'll try an install on a clean drive and see what happens.

---

### Post by crjackson on 2013-04-02
> **supermariofan25 said:**
> Dont worry, Im not going to remove it :) in fact im thinking of reposting it more spaced out and with steps so its easier to read and understand

Great, please do that for posterity.

---

### Post by supermariofan25 on 2013-04-04
> **crjackson said:**
> Sorry for the belated reply, I've been under the weather.  They were PC laptops with Core2Duo processors and i5 processors with Intel Video.  An OSX without rEFIt does nothing at all on these systems, with rEFIt I get to the rEFIt boot screen and that's as far as it goes.  It won't even give me a flashing cursor without rEFIt.  I thought that was the point of the rEFIt loader (to provided an EFI emulation so that a non-Mac could boot).  How else would you get a non-Mac to boot OSX then.

Yeah rEFIt actually needs an EFI to work but doesn't work with the UEFI in the Win8 PC's, only Intel Macs. If you you want to boot OS X on Windows BIOS PC's google OS X x86, booting OS X on a PC is dependent on if your hardware or Computer are compatible with the custom drivers they have made so far. for the best chance look at the compatibility list for OS X 10.6.2 or 10.6.8 "Snow Leopard" as it has been out for longer. To stay with the law, do not download a pre made DVD ISO as that would be pirating, please do your best to buy a legit retail disk and then put the additional drivers and mods together your self, if you do find that to hard than buy a retail disk and then download a pre made "illegal" ISO file, dont feel to bad for yourself if you choose to download the illegal ISO file pre made, just make shore that you but a legit retail disk to at least give apple some money for the modded ISO file and you should be fine :) if you do choose to do so I would recommend OS X x86 Snow Leopard by Hazard, just Google it! but make shure you research what hardware of consumer PC's it is compatible with before you go wasting money and downloads ;)

P.S. I do not encourage pirating of copyrighted objects or media.

---

### Post by supermariofan25 on 2013-04-04
> **crjackson said:**
> Great, please do that for posterity.

Yes, I will do that! and as of right now I cant do Pictures sorry (Again i dont have a Mac Pro yet... maybe in the years to come :D). Haven't been checking the forums lately so no repost yet, will do so in my spare time. Also if you are new with the World of Macintosh then I sugest you check the Mac Rumors Forums for everything Macintosh!

---

### Post by crjackson on 2013-04-04
> **supermariofan25 said:**
> Yeah rEFIt actually needs an EFI to work but doesn't work with the UEFI in the Win8 PC's, only Intel Macs. If you you want to boot OS X on Windows BIOS PC's google OS X x86, booting OS X on a PC is dependent on if your hardware or Computer are compatible with the custom drivers they have made so far. for the best chance look at the compatibility list for OS X 10.6.2 or 10.6.8 "Snow Leopard" as it has been out for longer. To stay with the law, do not download a pre made DVD ISO as that would be pirating, please do your best to buy a legit retail disk and then put the additional drivers and mods together your self, if you do find that to hard than buy a retail disk and then download a pre made "illegal" ISO file, dont feel to bad for yourself if you choose to download the illegal ISO file pre made, just make shore that you but a legit retail disk to at least give apple some money for the modded ISO file and you should be fine :) if you do choose to do so I would recommend OS X x86 Snow Leopard by Hazard, just Google it! but make shure you research what hardware of consumer PC's it is compatible with before you go wasting money and downloads ;)

P.S. I do not encourage pirating of copyrighted objects or media.

The law is the leas of my worries. I purchased from Apple through the app store, then extracted the install from the img file and put it on a DVD, it boots fine on my Mac.  I also put it on a USB stick which also boots fine on my Mac (With or without rEFIt).

---

### Post by supermariofan25 on 2013-04-06
> **crjackson said:**
> The law is the leas of my worries. I purchased from Apple through the app store, then extracted the install from the img file and put it on a DVD, it boots fine on my Mac.  I also put it on a USB stick which also boots fine on my Mac (With or without rEFIt).

I was talking about snow leopard, to use on a "Hackintosh" (Windows PC that runs OS X), I wasn't talking about Mountain Lion although Mountain Lion does work with some products.

---

