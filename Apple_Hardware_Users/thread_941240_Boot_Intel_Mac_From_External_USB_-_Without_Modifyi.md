---
title: "Boot Intel Mac From External USB - Without Modifying Host"
date: 2008-10-07
forum: Apple Hardware Users
---

### Post by WaeV on 2008-10-07
**Problem background:**
I do not actually own a mac, but my school owns several.  I have an online course that requires  a C++ compiler, and I am tired of having to do all my work at home on Visual Studio.  I have found a linux replacement (works on my home ubuntu partition) and have decided to try and boot linux at school from a usb drive such that I might do my schoolwork at school. (A novel concept, i know.)


**Problem Goals and Restraints:**
-Boot Ubuntu off of my USB external drive (5th Gen 30GB iPod with no music partiton - I'm using it simply as a USB drive)
-I may not alter the school mac in any way. (No installing programs, no putting a /boot partition on the host system)
-I have normal user access to the macs at school, so it's unlikely I would be able to use any mac formatting tools or the terminal (especially if it requires root).
-Compiz at school would be amazingly cool.  The computers definitely have the power to run it (2.2 Ghz, 2 GB ram).


I've read a lot of articles and I've heard of many different methods of success, failure, and partial success.  There are many things I have heard that I don't fully understand, including grub2, gptsync, bless, and how to make a /boot partition on the external drive be anything other than ext2 or ext3.

Any assistance would be appreciated.

---

### Post by cyberdork33 on 2008-10-07
> **WaeV said:**
> **Problem background:**
I do not actually own a mac, but my school owns several.  I have an online course that requires  a C++ compiler, and I am tired of having to do all my work at home on Visual Studio.  I have found a linux replacement (works on my home ubuntu partition) and have decided to try and boot linux at school from a usb drive such that I might do my schoolwork at school. (A novel concept, i know.)


**Problem Goals and Restraints:**
-Boot Ubuntu off of my USB external drive (5th Gen 30GB iPod with no music partiton - I'm using it simply as a USB drive)
-I may not alter the school mac in any way. (No installing programs, no putting a /boot partition on the host system)
-I have normal user access to the macs at school, so it's unlikely I would be able to use any mac formatting tools or the terminal (especially if it requires root).
-Compiz at school would be amazingly cool.  The computers definitely have the power to run it (2.2 Ghz, 2 GB ram).


I've read a lot of articles and I've heard of many different methods of success, failure, and partial success.  There are many things I have heard that I don't fully understand, including grub2, gptsync, bless, and how to make a /boot partition on the external drive be anything other than ext2 or ext3.

Any assistance would be appreciated.I can honestly say that this will likely be a dead end path.

Why can you not just use the compiler in OS X? It is just gcc.

---

### Post by WaeV on 2008-10-07
How do I use gcc without the terminal?  Also, it's a C++ course, and I had to install g++ before it would compile at home.

---

### Post by cyberdork33 on 2008-10-07
> **WaeV said:**
> How do I use gcc without the terminal?  Also, it's a C++ course, and I had to install g++ before it would compile at home.
You should be able to run the terminal as a normal user.

*IF* the developer tools are installed on the Macs (which includes gcc), then you should have g++ available.

Otherwise, you could look into a LiveCD that has gcc on it by default.

---

### Post by RavUn on 2008-10-07
I thought you could always get to the terminal; if you could, gcc is pretty good for C++.  From what I've read, it's still not possible to boot non-Mac OS from USB.  I've heard about a boot CD but it was a hassle.

---

### Post by Nasaki on 2008-10-07
Have you ever heard of [refit]("http://refit.sourceforge.net/"). Try installing Refit on the root of the USB drive, obviously you would need to do that from your home computer (running OSX). Then try booting to the USB refit should start and from there you can boot OSX. Im not totally sure this will work but its just a suggestion.

Good luck

---

### Post by WaeV on 2008-10-07
Thank you, Nasaki, for your informative post.  I didn't realize rEFIt could be installed to anything other than the internal HD.

So the unmodified mac would recognize rEFIt on the external USB drive?  If it did, would rEFIt then allow me to boot into one of the partitions on the USB drive?  Can anyone verify this?

---

### Post by cyberdork33 on 2008-10-07
> **WaeV said:**
> So the unmodified mac would recognize rEFIt on the external USB drive?  If it did, would rEFIt then allow me to boot into one of the partitions on the USB drive?  Can anyone verify this?
no. The only way you will get it to work is if you create a boot cd with the Linux kernel you want on it, which can then load the root partition on the external hard drive. This method is cumbersome, but it is detailed in the post linked in the FAQ on this subject.

---

### Post by WaeV on 2008-10-07
Oh, I see.  I didn't see your post beyond "no" for some reason, initially.

Correct me if i'm wrong, but is what you said essentially putting /boot on a CD and having it point to the USB drive as / ?

---

### Post by cyberdork33 on 2008-10-08
> **WaeV said:**
> Oh, I see.  I didn't see your post beyond "no" for some reason, initially.I was probably editting then.

> **WaeV said:**
> Correct me if i'm wrong, but is what you said essentially putting /boot on a CD and having it point to the USB drive as / ?
Yep

---

### Post by WaeV on 2008-10-08
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html) says that rEFIt can be installed to and booted from USB drives, provided they are HFS+ format.

As it turns out, I can use Diskutil at school, and I took advantage of that to format a small partition at the front of my USB drive to HFS+.  Unfortunately, I couldn't execute the enable.sh without sudo.  I am working on getting a release of Darwin running at home so I might execute it.  (It can't be run in linux)

Here is what my USB drive looks like at the moment:

50MB HFS+ rEFIt
27GB ext2 Complete Ubuntu Installation
2GB swap


Also, I had an amusing thought today:  If I pull this off, it will be a Mac booting rEFIt booting GRUB booting Ubuntu.

---

### Post by cyberdork33 on 2008-10-08
> **WaeV said:**
> [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html) says that rEFIt can be installed to and booted from USB drives, provided they are HFS+ format.

Also, I had an amusing thought today:  If I pull this off, it will be a Mac booting rEFIt booting GRUB booting Ubuntu.Feel free to try, but having rEFIt on the USB device has nothing to do with whether or not GRUB will from there. rEFIt is just a GUI for the Mac EFI. The Mac EFI system will not boot "legacy" operating systems from USB.

---

### Post by WaeV on 2008-10-09
If rEFIt is only a GUI for the Mac EFI, how can rEFIt allow people to boot linux off their main drive?

> Note that starting with version 0.6, rEFIt can boot legacy OSes directly, without the additional reboot used in 0.5. It also recognizes common Linux and Windows boot sectors and displays the appropriate icon. 

Ooh, this could help:
> NOTE: It is currently recommended to boot Linux through BIOS compatibility mode (a.k.a. Boot Camp) using LILO or GRUB. Otherwise, the fully accelerated ATI and Intel graphics drivers will not work.

Add a folder inside the &#8220;efi&#8221; folder. Copy the following files there:

    * elilo (called either &#8220;elilo.efi&#8221; or &#8220;e.efi&#8221;)
    * &#8220;vmlinuz&#8221;
    * &#8220;initrd.gz&#8221; (if present)
    * &#8220;elilo.conf&#8221; (if present)

Make sure that elilo.conf uses relative paths for the &#8220;image=&#8221; and &#8220;initrd=&#8221; options (no leading slash). The folder will show up in the rEFIt menu automatically. You can make as many folders with different configurations as you like. 

Edit:  nevermind, elilo is for booting from EFI.  The following link does assure that Macs can boot to legacy OSes with nothing but rEFIt, however:

[http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/](http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/)

My biggest problem now is getting a copy of OSX or Darwin working so I can run enable.sh on the rEFIt partition (don't know the school sudo password :/)

---

### Post by senuxis on 2008-10-09
[This site]("http://icrontic.com/articles/triplebootmbp") will help you. Also read the text attachment.

---

### Post by cyberdork33 on 2008-10-09
> **WaeV said:**
> If rEFIt is only a GUI for the Mac EFI, how can rEFIt allow people to boot linux off their main drive?Because you don't even need rEFIt to boot from the main drive either... You can hold alt on startup of your mac, and it will allow you to boot linux, windows, LiveCDs, etc.



> **WaeV said:**
> Ooh, this could help:


Edit:  nevermind, elilo is for booting from EFI.
using elilo / grub-efi is an option, but there are other limitation doing that, and it is not well supported yet. There are few people here that have messed with it before.
[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

> **WaeV said:**
> The following link does assure that Macs can boot to legacy OSes with nothing but rEFIt, however:

[http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/](http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/)Yes every once in awhile someone claims to get it working, but then nobody else can. You can read through the "booting from external drives" thread in the FAQ for more examples of that. 

Here is a discussion about the inability of Macs to boot Linux from USB.

[http://discussions.apple.com/thread.jspa?threadID=1723157&tstart=0](http://discussions.apple.com/thread.jspa?threadID=1723157&tstart=0)


> **WaeV said:**
> My biggest problem now is getting a copy of OSX or Darwin working so I can run enable.sh on the rEFIt partition (don't know the school sudo password :/)what you really need is the "bless" command. I don't know if this is on the Darwin CD or not. You can boot a OSX install disc and use bless in the terminal.

---

### Post by WaeV on 2008-10-09
> At this point in the process, rEFIt will see all three operating systems and will be able load Mac OS and Windows. Linux, however, needs to have its own partition records updated to properly load.

1. Once the machine is rebooted and on the rEFIt screen, press the arrow keys until you reach the &#8216;Partitioning Tool&#8217; icon. Press the &#8216;Enter&#8217; key.

2. When it asks, &#8220;May I update the MBR as printed above?&#8221;, press the &#8216;y&#8217; key. rEFIt&#8217;s partition records will update.

3. You should now be able to boot into any Operating System.

Ok, I see how that could help, but I don't see how the text attachment is of much use.  I am dealing with OSX and Linux only, not Windows.  Thanks for your post anyways, but I would need further explanation as to how the attachment is of use.

Edit:
> i have tried to use refit by having a small refit partition at the beginning of the usb device. i then boot with the option key and get the mac, windows and refit option.
selecting the refit partition starts refit and lists my linux partition correctly but then cannot boot it giving me the error regarding limited firmware support.
Hmm... this was the next step I was going to take.  So the new obstacle to tackle is to discover what is meant by "limited firmware support" and how to either fix it or bypass it.  In the meantime, I will work on getting to this point so I can try for myself.

> what you really need is the "bless" command. I don't know if this is on the Darwin CD or not. You can boot a OSX install disc and use bless in the terminal.
Getting the OSX disc is the current problem.  Maybe I can get a teacher to run the script on their macbook...

---

### Post by cyberdork33 on 2008-10-09
> **WaeV said:**
> Hmm... this was the next step I was going to take.  So the new obstacle to tackle is to discover what is meant by "limited firmware support" and how to either fix it or bypass it.  In the meantime, I will work on getting to this point so I can try for myself.
That sounds like they didn't update the firmware to enable "bootcamp" stuff. You will probably get a different error because you are not trying to boot from the internal drive.

---

### Post by WaeV on 2008-10-09
While we're on the topic of boot camp, I have heard that there are boot camp drivers for Windows.  Are there any such drivers or other modification required for Linux?

> [QUOTE]The following link does assure that Macs can boot to legacy OSes with nothing but rEFIt, however:

[http://tubeshards.wordpress.com/2006...osh-usb-drive/](http://tubeshards.wordpress.com/2006...osh-usb-drive/)
Yes every once in awhile someone claims to get it working, but then nobody else can. You can read through the "booting from external drives" thread in the FAQ for more examples of that.[/QUOTE]
There are many comments afterwards claiming success.  Differences between that scenario and mine, however, are that they are using Windows, not Linux. (And a specially modified version at that!)

---

### Post by cyberdork33 on 2008-10-09
> **WaeV said:**
> While we're on the topic of boot camp, I have heard that there are boot camp drivers for Windows.  Are there any such drivers or other modification required for Linux?
You can check the wiki page for your hardware specifically on direction to get everything working properly. See the "Before You Post" link in my signature to find the right page.

---

### Post by WaeV on 2008-10-09
> rEFIt is a user friendly interface to the Mac EFI that will cause a boot menu (to select between OS X/Ubuntu) to appear on every boot. You can make Ubuntu boot by default by uncommenting the 'legacyfirst' option and change the menu timeout in the "refit.conf" file (described on the above website).

Ok, so I need some clarification here.  What is actually causing the Mac to recognize and boot legacy OSes here?

[http://www.matisse.net/OSX/darwin_commands.html](http://www.matisse.net/OSX/darwin_commands.html)
This website confirms that Darwin can 'bless' drives.  Unfortunately, My CD drive is broken and I can't install it. I'll try a virtual machine.

---

### Post by cyberdork33 on 2008-10-10
> **WaeV said:**
> Ok, so I need some clarification here.  What is actually causing the Mac to recognize and boot legacy OSes here?The EFI firmware in your Mac can recognize and boot legacy OSes, just not ones that are on an external hard drive. 
> **WaeV said:**
> 
[http://www.matisse.net/OSX/darwin_commands.html](http://www.matisse.net/OSX/darwin_commands.html)
This website confirms that Darwin can 'bless' drives.  Unfortunately, My CD drive is broken and I can't install it. I'll try a virtual machine.I don't know that a VM will work since you would be blessing the virtual disk(s) and not the actual hardware.

---

### Post by WaeV on 2008-10-10
> The EFI firmware in your Mac can recognize and boot legacy OSes, just not ones that are on an external hard drive.
But the EFI firmware can recognize and boot Mac OSX from an external drive.  Do we know why it doesn't do the same for legacy OSes?

> I don't know that a VM will work since you would be blessing the virtual disk(s) and not the actual hardware.
I was under the impression that you could mount actual drives whilst running a virtual machine.

Ok, I just checked; you can mount external drives with VMware workstation but not player.  I would be using the 30-day trial so I should be set.

Edit:
On the default graphical bootloader for EFI Intel Macs:
>     *  It displays any "blessed" volume on any available disk, including external USB and FireWire hard disks, USB flash memory disks, flash memory cards in USB card readers, and CD/DVD drives.
    * It supports HFS+ partitions on disks formatted with GPT, Apple Partition Map, and even MBR.
    * Apparently it doesn't support FAT partitions at all, because it looks at the info in the HFS+ volume header placed there by bless. You can use FAT only for the default boot volume (see above).
    * El Torito is supported as well, but the boot image must contain a HFS+ file system to show up in the chooser. It appears that some kind of partition table (e.g. an Apple Partition Map) is also required; this might be a minor issue caused by the sector size. (Note: This no longer works with the firmware updates for Boot Camp. Details are still under investigation.)
    * Displays the volume icon as set in the Finder's "More info" dialog. (NTFS partitions will always display the generic disk icon because the firmware can't read that file system.)
    * The volume name label displayed is taken from a pre-rendered graphics file. It can be controlled through bless options, but the --label option is broken in current versions. More info on labels.
    * The chooser can be controlled by keyboard, mouse, or IR remote control. 
So an aluminum Intel iMac would be able to recognize a blessed HFS+ partition on an external USB device.  That HFS+ partition could contain rEFIt for the sake of having the partitioning tool needed to make Hardy bootable.

Also, rEFIt "gives you direct access to the EFI shell and the built-in EFI maintenance menus."

Since rEFIt only offers increased control and not more detection / boot options (I think), wouldn't Ubuntu need to have /boot on a blessed HFS+ partition?

---

### Post by cyberdork33 on 2008-10-10
> **WaeV said:**
> But the EFI firmware can recognize and boot Mac OSX from an external drive.  Do we know why it doesn't do the same for legacy OSes?The definition (as Apple makes it) of a "legacy" OS is one that is not booted by EFI natively, but must be booted instead by it's "emulated" BIOS. It is a bug / limitation / lockout by Apple in the EFI firmware. You can boot Linux by EFI natively, but that is a much more involved process, and there are other limitations you face by doing that. (Basically, it is still quite underdeveloped.)

> **WaeV said:**
> I was under the impression that you could mount actual drives whilst running a virtual machine.

Ok, I just checked; you can mount external drives with VMware workstation but not player.  I would be using the 30-day trial so I should be set. Even then I am not sure if it is work since the device being "translated" into the VM... You are not accessing the device directly, but it would be a good experiment. Please post your results.

> **WaeV said:**
> On the default graphical bootloader for EFI Intel Macs:

So an aluminum Intel iMac would be able to recognize a blessed HFS+ partition on an external USB device.  That HFS+ partition could contain rEFIt for the sake of having the partitioning tool needed to make Hardy bootable.yes, it could actually be a blessed FAT32 partition too. (or the EFI partition on the disk, although it is really just a FAT32 partition as well.)

> **WaeV said:**
> Also, rEFIt "gives you direct access to the EFI shell and the built-in EFI maintenance menus."yes

> **WaeV said:**
> Since rEFIt only offers increased control and not more detection / boot options (I think), wouldn't Ubuntu need to have /boot on a blessed HFS+ partition?no, The Mac EFI can see other blessed partitions besides HFS+. Also, having /boot formatted as HFS+ would not work because All the current linux bootloaders are incapable of reading that filesystem. That means they cannot see the kernel, and that means it cannot boot anything.

---

### Post by WaeV on 2008-10-15
> Even then I am not sure if it is work since the device being "translated" into the VM... You are not accessing the device directly, but it would be a good experiment. Please post your results.
I'm afraid VMware fell through.  I'll have to find some way to get password access to a mac.

> The definition (as Apple makes it) of a "legacy" OS is one that is not booted by EFI natively, but must be booted instead by it's "emulated" BIOS. It is a bug / limitation / lockout by Apple in the EFI firmware. You can boot Linux by EFI natively, but that is a much more involved process, and there are other limitations you face by doing that. (Basically, it is still quite underdeveloped.)

yes, it could actually be a blessed FAT32 partition too. (or the EFI partition on the disk, although it is really just a FAT32 partition as well.)

no, The Mac EFI can see other blessed partitions besides HFS+. Also, having /boot formatted as HFS+ would not work because All the current linux bootloaders are incapable of reading that filesystem. That means they cannot see the kernel, and that means it cannot boot anything.
So the mac EFI loader can see any blessed partition, but what about booting?  How do we get it to boot a blessed external ext2 partition?  Once we solve that problem and can get GRUB up and running, I think we'll be golden.

---

### Post by cyberdork33 on 2008-10-15
> **WaeV said:**
> I'm afraid VMware fell through.  I'll have to find some way to get password access to a mac.


So the mac EFI loader can see any blessed partition, but what about booting?  How do we get it to boot a blessed external ext2 partition?  Once we solve that problem and can get GRUB up and running, I think we'll be golden.

it is a problem that is circular.

In order to have usb support (which you need for an external hard drive to work) you have to load the Linux kernel, and in order to load the linux kernel, you have to access files in the external drive... The EFI system's "BIOS" has limited ability to utilize USB, and GRUB has none.

---

### Post by WaeV on 2008-10-15
What?  I know for a fact that Macs can boot OSX from an external drive, and that GRUB boots fine from the external drive on any PC.  Could you explain further?

---

### Post by pxwpxw on 2008-10-15
> **WaeV said:**
> What?  I know for a fact that Macs can boot OSX from an external drive, and that GRUB boots fine from the external drive on any PC.  Could you explain further?


Apple macintels boot macosx from external because macosx has an efi bootloader (boot.efi) which is "blessed".

grub1 is a linux bootloader which depends on pc bios information to boot externals. This info is not available from apples msdos compatibility mode. 

grub2-efi is an efi application which boots linux kernels, it can be installed on externals drives and blessed, and will then be recognised by macintel efi.

I expect that the blessing can be done using Macosx on another Mac.
(I cant confirm that as I have just the one macbook)
That seems to be the only way to achieve your goal.

---

### Post by cyberdork33 on 2008-10-15
> **WaeV said:**
> What? I know for a fact that Macs can boot OSX from an external drive, and that GRUB boots fine from the external drive on any PC. Could you explain further?Your PC has in its firmware the capability to boot from USB. The software required to boot code on the external hard drive is in its BIOS.

OSX does not boot via the emulated BIOS on the Mac. You have to seperate what you can do with OSX (the OS this hardware is designed to run) and Linux (which it is not designed to run). The boot process for the two is entirely different. 

> **pxwpxw said:**
> grub2-efi is an efi application which boots linux kernels, it can be installed on externals drives and blessed, and will then be recognised by macintel efi.

I expect that the blessing can be done using Macosx on another Mac.
and that has other issues associated as I stated before...

blessing should be capable from another Mac via Target mode or just booting up the OSX install dvd.

---

### Post by WaeV on 2008-10-15
I was under the impression that [color="DarkRed"]"Apple released the needed firmware changes to emulate a &#8220;legacy&#8221; BIOS and MBR along with a partitioning tool / Windows drivers CD package named Bootcamp," [/color] but that  [color="DarkRed"]"the Bootcamp application is not required, just the updated firmware is, which new Macs ship with already." [/color]
[http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/)

I was also under the impression that the default EFI bootloader  [color="DarkRed"]"displays any "blessed" volume on any available disk, including external USB and FireWire hard disks, USB flash memory disks, flash memory cards in USB card readers, and CD/DVD drives," [/color] but that rEFIt's partitioning tool was needed to fix Hardy to make it bootable.

> [QUOTE][QUOTE]i have tried to use refit by having a small refit partition at the beginning of the usb device. i then boot with the option key and get the mac, windows and refit option.
selecting the refit partition starts refit and lists my linux partition correctly but then cannot boot it giving me the error regarding limited firmware support.
Hmm... this was the next step I was going to take. So the new obstacle to tackle is to discover what is meant by "limited firmware support" and how to either fix it or bypass it. In the meantime, I will work on getting to this point so I can try for myself.[/QUOTE]
That sounds like they didn't update the firmware to enable "bootcamp" stuff. You will probably get a different error because you are not trying to boot from the internal drive.[/QUOTE]
Which brings us back to this vague error message that I'm supposed to get.  Does anyone know the _exact problem_ with using rEFIt to boot a blessed ext2 partition located on an external drive?

---

### Post by cyberdork33 on 2008-10-16
> **WaeV said:**
> I was under the impression that [COLOR=DarkRed]"Apple released the needed firmware changes to emulate a “legacy” BIOS and MBR along with a partitioning tool / Windows drivers CD package named Bootcamp," [/COLOR] but that  [COLOR=DarkRed]"the Bootcamp application is not required, just the updated firmware is, which new Macs ship with already." [/COLOR]
[http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/](http://www.rickycampbell.com/the-intel-mac-partitioning-system-efi-and-gpt/)and it does. I don't understand your point. Some BIOS software has features that others don't. The Mac one is quite limited.

> **WaeV said:**
> I was also under the impression that the default EFI bootloader  [COLOR=DarkRed]"displays any "blessed" volume on any available disk, including external USB and FireWire hard disks, USB flash memory disks, flash memory cards in USB card readers, and CD/DVD drives," [/COLOR] but that rEFIt's partitioning tool was needed to fix Hardy to make it bootable.and it does. you can install to the external, and rEFIt will see it as bootable, but when you try to boot it, it doesn't get far.


> **WaeV said:**
> Which brings us back to this vague error message that I'm supposed to get.  Does anyone know the _exact problem_ with using rEFIt to boot a blessed ext2 partition located on an external drive?asking the same question over and over doesn't get a better answer.

---

### Post by WaeV on 2008-10-16
> and it does. you can install to the external, and rEFIt will see it as bootable, but when you try to boot it, it doesn't get far.
How far does it get?

> asking the same question over and over doesn't get a better answer. 
Sorry for repeating myself, I guess I'm used to having forum conversations with people of... lower intellect than here.  Rephrasing a question almost always results in a different answer on the forums I frequent.

I'm sure you've answered the question to the best of your ability, but I either don't fully understand it or the answer I'm looking for hasn't been discovered yet.  Either way, you've been a great help so far, thanks.  I suppose the next step still rests on me securing a mac to bless the drive.  :?

---

### Post by pxwpxw on 2008-10-16
> **WaeV said:**
> How far does it get?

thanks.  I suppose the next step still rests on me securing a mac to bless the drive.  :?

Seems to have missed the point that it will need an EFI bootloader to bless, and the EFI bootloader has to load the OS kernel. rEFIt on the usb can serve to demonstrate the feasibility, but can not boot linux kernels, it is not a bootloader.

---

### Post by WaeV on 2008-10-16
If EFI can't boot the linux kernel, how does it boot to linux whilst on the internal drive?  I swear I'm missing some key concept here.

---

### Post by pxwpxw on 2008-10-16
> **WaeV said:**
> If EFI can't boot the linux kernel, how does it boot to linux whilst on the internal drive?  I swear I'm missing some key concept here.

"rEFIt" passes the job to either Grub legacy version (pc) or the apple firmware.
Other EFI programs can load linux kernels.
One is the EFI version of Grub2.

Good grub2 (and grub1) info is here:
[http://grub.enbug.org/FrontPage](http://grub.enbug.org/FrontPage)

The documentation on the rEFIt web site is also a good reference.
[http://refit.sourceforge.net](http://refit.sourceforge.net)

---

### Post by WaeV on 2008-10-16
> "rEFIt" passes the job to the Grub legacy version
Ok, this is what I'm trying to do.  What is the limitation that prevents this from happening on an external drive, or is there none?

Thanks for the other info, but I ruled out booting natively from EFI due to a lack of hardware support.

---

### Post by cyberdork33 on 2008-10-16
> **WaeV said:**
> Ok, this is what I'm trying to do.  What is the limitation that prevents this from happening on an external drive, or is there none?
Apple's firmware has a bug (or it is there on purpose) and/or the fact that when control is passed to the legacy bootloader, there is no longer any driver to maintain the USB service (i.e. USB device are not available anymore). There used to be a note about this in the rEFIt site somewhere, but I couldn't find it this time. So, it very well may be that we just "don't know" but several people have worked on this and nobody has "found the answer" and several, several derivations from the normal process has been attempted. There are quite a few threads here where people document their experimentation, the most extensive of which is linked in the FAQ at the top of the forum.

As for how far it gets, it really doesn't do anything. If you get everything setup properly to boot (like you would from the internal drive) rEFIt usually gives an error about Apple's poor support for booting legacy OSs from an external hard drive. (pretty much worded like that).

---

### Post by WaeV on 2008-10-16
Ok, that's exactly the answer I was looking for, thanks.  I'll see what I can do to work around the problem.

---

### Post by WaeV on 2008-10-21
Ok, I don't think I'll have password access to a Mac in the near future.  How would I go about putting /boot on a CD?

---

### Post by cyberdork33 on 2008-10-21
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

Still the same thread in the FAQ...

---

### Post by WaeV on 2008-10-21
I looked through the entire thread, and while there are many posts regarding having a CD as /boot, nobody explains how to do it.  There is one post that links to a premade CD, but I would want a current one.


> OK I shall try to summarise the various failed attempts I have made to get this working.

My objective (despite the fact that I am posting in an Ubuntu forum) is to get XP running from an external USB HDD on my MacBook Pro Core 2 Duo. Due to the amount of time I have spent trying to achieve this and reading and posting on various forums I am beginning to think that, with my setup at least, this is currently not possible but I am writing this in the hope that someone will say "of course it is" and will tell me what I have been doing wrong.

Because there is a lot of this and I may not have time to document this now, I shall make a separate post for each method I attempted.

Attempt #1

My first attempt was to install XP on a USB HDD using my Compaq nc4200 laptop (which is running Ubuntu 7.10). The installation went smoothly and XP booted and ran fine.

This disk was partitioned by Windows and has a MBR and standard partition table.

I tried to boot this disk on my MBP using rEFIt. I tried rEFIt on the MBP HDD, on a USB flash drive and on a CD with identical results. rEFIt saw the XP installation and recognised it as such, but when I selected it to boot I got the following error messages:

rEFIt - Booting Legacy OS


Starting legacy loader
Using load option 'USB'
Error: Not Found returned from legacy loader
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Load Error while (re)opening our installation volume

The firmware refused to boot from the selected volume. Note that external
hard drives are not well-supported by Apple's firmware for legacy OS booting.

* Hit any key to continue *

I also tried booting another external USB disk which had a working installation of Ubuntu 7.10 on it with identical results.

This attempt seems to be the error I would have recieved if I had managed to get it 'working'.

---

### Post by WaeV on 2008-10-27
Ooh!  I think this idea might work!

Have an HFS+ partition on the USB drive with GRUB2

Have an ext2 partition with regular GRUB on it

Have the Ubuntu partition

Use the default EFI mac bootloader to boot GRUB2, then use GRUB2 to boot to regular GRUB, then use regular GRUB to boot to Ubuntu!

---

### Post by cyberdork33 on 2008-10-27
> **WaeV said:**
> Ooh!  I think this idea might work!

Have an HFS+ partition on the USB drive with GRUB2

Have an ext2 partition with regular GRUB on it

Have the Ubuntu partition

Use the default EFI mac bootloader to boot GRUB2, then use GRUB2 to boot to regular GRUB, then use regular GRUB to boot to Ubuntu!
I think you might still use USB that way, but that is an interesting method to attempt.

---

### Post by WaeV on 2008-10-29
I've looked around but can't find any resources on how to get GRUB to boot to another GRUB (especially GRUB2).  Most of the conversations on the topic have been to the extent of "you don't need to do that" or "GRUb can only boot to an OS with a /boot."  I know the second comment to be false, because GRUB can boot Windows.

I know that when GRUB is booted from an external drive, it views that drive as hd0, so should I install GRUB2 and simply point it to (hd0,1) like so?

```
title		Legacy GRUB
root		(hd0,1)
makeactive
chainloader	+1
```

---

### Post by cyberdork33 on 2008-10-29
> **WaeV said:**
> I've looked around but can't find any resources on how to get GRUB to boot to another GRUB (especially GRUB2).  Most of the conversations on the topic have been to the extent of "you don't need to do that" or "GRUb can only boot to an OS with a /boot."  I know the second comment to be false, because GRUB can boot Windows.

I know that when GRUB is booted from an external drive, it views that drive as hd0, so should I install GRUB2 and simply point it to (hd0,1) like so?

```
title        Legacy GRUB
root        (hd0,1)
makeactive
chainloader    +1
```
It depends on where the grub bootcode is stored, but yes something like that... (For example, if it was on the MBR, it would just be hd0 instead of hd0,1) I thought that the GRUB2 syntax was different than the legacy grub though.

---

### Post by WaeV on 2008-10-29
Yes, GRUB2 starts numbering at 1 instead of 0 (as well as other things, I'm sure), but I'm more familiar with GRUB's syntax, so I thought I'd get the gist, then work on translating to GRUB2's syntax.

---

### Post by billbear on 2008-10-31
> **WaeV said:**
> Ooh!  I think this idea might work!

Have an HFS+ partition on the USB drive with GRUB2

Have an ext2 partition with regular GRUB on it

Have the Ubuntu partition

Use the default EFI mac bootloader to boot GRUB2, then use GRUB2 to boot to regular GRUB, then use regular GRUB to boot to Ubuntu!

You will not be able to boot grub2 from efi if you are not able to bless it.
If you are able to bless grub2, it can boot ubuntu directly, no need to boot to regular GRUB; 
if you boot grub2 then boot to grub, you will lose the ability to boot from usb that grub2 provides.

---

### Post by billbear on 2008-10-31
A grub2 developer Bean debugged and tested on his macbook(64 bit efi) and my macbook(32 bit efi) from June to July and successfully made the 2 machines boot linux from usb with grub2-efi. He then wrote this article [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
If you will be able to bless, try it. It may still be buggy for your model of Mac, if you wish to help the developer to debug grub2-efi, I think Bean will be glad to help you too.

---

### Post by cyberdork33 on 2008-10-31
> **billbear said:**
> A grub2 developer Bean debugged and tested on his macbook(64 bit efi) and my macbook(32 bit efi) from June to July and successfully made the 2 machines boot linux from usb with grub2-efi. He then wrote this article [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
If you will be able to bless, try it. It may still be buggy for your model of Mac, if you wish to help the developer to debug grub2-efi, I think Bean will be glad to help you too.
do all the graphics issues still exist? (no 3d?)

---

### Post by pxwpxw on 2008-11-01
> **cyberdork33 said:**
> do all the graphics issues still exist? (no 3d?)

I have had to use agp=off and video=efifb since around august, maybe later svn grub-efi versions plus later macbook have changed that. I should check it out again I suppose. Not sure where the limitation lies (mac, grub, kernel?).

---

### Post by billbear on 2008-11-01
> **cyberdork33 said:**
> do all the graphics issues still exist? (no 3d?)

Yes unfortunately

---

### Post by WaeV on 2008-11-01
> You will not be able to boot grub2 from efi if you are not able to bless it.
Yeah, that's one of my main roadblocks atm.

> If you are able to bless grub2, it can boot ubuntu directly, no need to boot to regular GRUB;
But if it booted to regular GRUB, would there still be graphics problems?

> if you boot grub2 then boot to grub, you will lose the ability to boot from usb that grub2 provides.
I don't see why.  GRUB can boot to USB, it's the Mac EFI bootloader that can't.

Even if it couldn't boot to USB, it would be running from the USB drive anyways, and would see it as hd0. (Right?)

---

### Post by WaeV on 2008-11-01
Ok, I now have access to a mac and can bless drives!

Now to get GRUB2 installed...

---

### Post by billbear on 2008-11-02
> **WaeV said:**
> > if you boot grub2 then boot to grub, you will lose the ability to boot from usb that grub2 provides.
I don't see why.  GRUB can boot to USB, it's the Mac EFI bootloader that can't.

Even if it couldn't boot to USB, it would be running from the USB drive anyways, and would see it as hd0. (Right?)

Legacy grub can see usb storages only if bios can boot from usb.
Apple's 'bios' cannot see usb storages, so legacy grub can only see internal disks, even if you manage to start grub from external. And I don't know a way to start legacy grub from grub2-efi.

---

### Post by billbear on 2008-11-02
> **WaeV said:**
> Ok, I now have access to a mac and can bless drives!

Now to get GRUB2 installed...

The easy way is to install rEFIt onto the usb storage, then copy grub.efi to the root of any HFS+/EXT2/EXT3/FAT partition of the usb storage. rEFIt will list it.

---

### Post by WaeV on 2008-11-02
> Legacy grub can see usb storages only if bios can boot from usb.
Apple's 'bios' cannot see usb storages, so legacy grub can only see internal disks, even if you manage to start grub from external.

I suppose that makes sense.  I'll try it anyways just to be sure.  I thought it would work because on PCs, if booted from an external drive, GRUB sees the external as hd0.

> And I don't know a way to start legacy grub from grub2-efi.
chainloader +1?

---

### Post by cyberdork33 on 2008-11-02
> **WaeV said:**
> I suppose that makes sense.  I'll try it anyways just to be sure.  I thought it would work because on PCs, if booted from an external drive, GRUB sees the external as hd0.
Yes, but as I said before, the PC BIOS software allows booting from USB like that, the Mac firmware does not. (Actually, older PCs did not allow booting from USB either.)

---

### Post by WaeV on 2008-11-02
Well, as of this moment I have GRUB2 blessed and ready to chainload an ext2 partition with grub and ubuntu.  I made sure to specifically install GRUB to sdc2 instead of sdc, if that makes any difference.  On my PC at home the GRUB2 prompt doesn't even come up (it goes straight to sdc2), but on the macs at school it ought to be the only thing the mac bootloader will see.  We'll know tomorrow, anyways.

If I can't get this to work, I guess I can just buy a small firewire drive.

---

### Post by pxwpxw on 2008-11-02
**WaeV**

Although it may be possible to load grub-pc (grub-legacy) from grub.efi (by passing the job back to apple pc-bios compatibility), you don't want to do that here. 

You have to avoid involving grub-pc for external booting on macintel.

If you can get the blesed grub.efi to just be seen and boot on the macintel, that will be a good step 1. You also need to have the necessary grub efi modules with,  or preloaded in grub.efi to support what you want to do. 

Then you have to write a grub.cfg file for grub-efi to boot the ubuntu vmlinux and initrd.img directly. The grub.cfg file goes in the same partition as grub.efi, you should be able to write it using the macintel.

I have a grub.cfg on a usb stick with grub.efi here somewhere, if you want it for an example, you are going to have to experiment.

There are several refernces and good advice already quoted above.

But I may have misunderstood what you are doing with what there, so be patient.

---

### Post by cyberdork33 on 2008-11-02
> **WaeV said:**
> If I can't get this to work, I guess I can just buy a small firewire drive.
I don't think that will make a difference. Same problem.

---

### Post by billbear on 2008-11-03
Another way i have tried with success:
    You know with one cdrom and one usb stick ubuntu can boot.
    And there are special tools to write the usb stick's firmware to simulate a cdrom. I successfully modified a usb stick's firmware, it was recognized as one usb cdrom + one usb stick.
    Apple's &#8220;bios" can boot from a usb-cdrom. when the usb stick declares it was a usb cdrom, it boots fine. And since it boots from bios, no graphics issues.  With one usb stick i can boot macs and PCs.

Drawbacks: Modifying the cdrom part of the usb stick will destroy all data on the stick. Unfortunately different versions of ubuntu needs different boot cd. I am still looking for a way to use one same cd to boot all ubuntus. I'm waiting for grub2-bios's usb support function (see usb when bios can't see)

---

### Post by pxwpxw on 2008-11-03
> **WaeV said:**
> 
If I can't get this to work, I guess I can just buy a small firewire drive.

If it does not work on an efi macintel, here is a grub.efi you can download that does work-
I built it from svn version 1833.

Re: Boot from external usb DVD Drive with REFIT?
[http://ubuntuforums.org/showpost.php?p=5579534&postcount=16](http://ubuntuforums.org/showpost.php?p=5579534&postcount=16)
 attachment File Type: gz  	grub-svnx.efi.gz 129.6 KB

I just rechecked it -
```
 $ zcat grub-svnx.efi.gz > grubpxw.efi 
``` copy to  an hfsplus partition on a usb stick, bless it, and the macbook boots it from an option restart  (no refit). It works standalone very well, has preloaded modules, and can boot linux kernels from its command line, as well as many other useful commands.

---

### Post by WaeV on 2008-11-03
> **billbear said:**
> Another way i have tried with success:
    You know with one cdrom and one usb stick ubuntu can boot.
    And there are special tools to write the usb stick's firmware to simulate a cdrom. I successfully modified a usb stick's firmware, it was recognized as one usb cdrom + one usb stick.
    Apple's &#8220;bios" can boot from a usb-cdrom. when the usb stick declares it was a usb cdrom, it boots fine. And since it boots from bios, no graphics issues.  With one usb stick i can boot macs and PCs.

Drawbacks: Modifying the cdrom part of the usb stick will destroy all data on the stick. Unfortunately different versions of ubuntu needs different boot cd. I am still looking for a way to use one same cd to boot all ubuntus. I'm waiting for grub2-bios's usb support function (see usb when bios can't see)

I don't mind erasing the hard drive.  This sounds like it may work, although convincing the iPod that 's a CD would probably ruin my ability to reformat it back to being an iPod.  (ATM it prompts me to reformat every time I plug it in)

Alternatively, I could use my 2GB stick as a booter for the iPod.  I don't mind screwing with the 2GB stick.  or was that what you said originally?

Edit:
Ok, I found this tutorial on replacing the U3 loader with a custom ISO.  How do I go about making a boot ISO?
[http://forums.msiwind.net/windows/usb-stick-rom-emulation-trick-t2838.html](http://forums.msiwind.net/windows/usb-stick-rom-emulation-trick-t2838.html)

What if I reinstalled ubuntu to the 30GB usb drive, setting the 2GB stick as /boot, then copied the 2GB stick's files into an iso, then put that iso into the U3 section of the 2GB stick?

---

### Post by pxwpxw on 2008-11-03
Here  is a grub.cfg file, all working for grub.efi from the usb stick.
drop the .txt off the end -> grub.cfg

---

### Post by billbear on 2008-11-03
> **WaeV said:**
> I don't mind erasing the hard drive.  This sounds like it may work, although convincing the iPod that 's a CD would probably ruin my ability to reformat it back to being an iPod.  (ATM it prompts me to reformat every time I plug it in)

Alternatively, I could use my 2GB stick as a booter for the iPod.  I don't mind screwing with the 2GB stick.  or was that what you said originally?

Edit:
Ok, I found this tutorial on replacing the U3 loader with a custom ISO.  How do I go about making a boot ISO?
[http://forums.msiwind.net/windows/usb-stick-rom-emulation-trick-t2838.html](http://forums.msiwind.net/windows/usb-stick-rom-emulation-trick-t2838.html)

What if I reinstalled ubuntu to the 30GB usb drive, setting the 2GB stick as /boot, then copied the 2GB stick's files into an iso, then put that iso into the U3 section of the 2GB stick?

Your iPod is a hard disk, not a usb stick, cannot simulate a cd.
It's possible to make your stick a cdrom, but different sticks require different tools, you don't know which tool will work for yours. You can search and try, but you can ruin your usb stick completely. 
ipod+stick? Why not just ipod+real cd? that will be much easier and safer.

---

### Post by WaeV on 2008-11-03
My CD drive is out of commission, so I have no way of burning a CD.

This site [http://www.u3community.com/viewtopic.php?t=434](http://www.u3community.com/viewtopic.php?t=434) explains how to replace the U3 iso on my drive with a custom iso, which can be the boot CD.

Even if I decided against putting my USB stick 'on the line', I would need verification that the above method would work.
(What if I reinstalled ubuntu to the 30GB usb drive, setting the 2GB stick as /boot, then copied the 2GB stick's files into an iso, then put that iso into the U3 section of the 2GB stick?)


```
## USB what? don't know
menuentry "Boot from USB1" {
  appleloader USB
}
```

pxwpxw, I agree that this would fail because it tells apple to load the USB drive.  Why not use the command "chainloader +1" (or its GRUB2 equivalent)?

---

### Post by pxwpxw on 2008-11-03
The menu was for you to try and learn by, it is a working example.

You will have to run grub.efi and experiment with commands and configuration to get an understanding. 

'appleloader' is a grub.efi command that refers back to the apple legacy loader, and can be used for HD CD or USB. 'chainlaodeer' is used to transfer to another efi application such as macosx boot.efi or refit or another grub.efi.
That is in an efi context, not a pc-bios context.

The '##USB what? don't know' comment was an old  one I forgot to delete, it is an irrelevant distraction. That menu item is legitmate, but it just tries to get apple to boot from the usb mbr, which we know will not work. You would use one of the other menuentry  to directly boot the linux kernel, I  provided a full selection of booting options.

---

### Post by WaeV on 2008-11-04
I restored my iPod today - I was beginning to miss my music.  I will continue to play with U3 iso loading, however, and once I know that works I can simply resize the fat partition.

I'm also planning on ordering a firewire external hard drive enclosure - I have 2 60GB drives lying around so I figured i might as well.  I'm about 80% sure Macs allow legacy booting from firewire, and if not I get 60GB of extra storage (120 if I'm motivated enough to switch the drives :p ).

**pxwpxw**
Doesn't booting from EFI as you are showing me limit 3D acceleration?  I appreciate the help, but a large motivational factor in booting Ubuntu like this was to show Compiz off on the school computers. :twisted:

Or maybe the first goal is to boot, the next goal is to get 3D working?

---

### Post by cyberdork33 on 2008-11-04
> **WaeV said:**
> Or maybe the first goal is to boot, the next goal is to get 3D working?
Booting legacy = 3d graphics
Booting through EFI = no 3D graphics

It's a problem that has been worked on for a very long time.

---

### Post by WaeV on 2008-11-04
That's what I thought.  Do we have any clue why?

---

### Post by pxwpxw on 2008-11-04
> **WaeV said:**
> 

**pxwpxw**
Doesn't booting from EFI as you are showing me limit 3D acceleration?  I appreciate the help, but a large motivational factor in booting Ubuntu like this was to show Compiz off on the school computers. :twisted:

Or maybe the first goal is to boot, the next goal is to get 3D working?

Ah, well sorry, yes the latest grub.efi (v1892) still requres the efi framebuffer, so you are out of luck.

---

### Post by cyberdork33 on 2008-11-04
> **WaeV said:**
> That's what I thought.  Do we have any clue why?

haven't figured out how to initialize the hardware properly. (Mainly because Apple won't tell us)

I think there are patches to get it working on certain Mac minis but that is all.

---

### Post by pxwpxw on 2008-11-04
BTW, its easy to boot from a boot CD with kernel, to external using grublegacy, but I think you got some other problem with that.

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by WaeV on 2008-11-04
That's interesting, If I could get a GRUB CD like that, I could just boot up and go, then take out the CD and still have freedom to burn CDs or whatever.

> haven't figured out how to initialize the hardware properly. (Mainly because Apple won't tell us)
It seems odd to me that the manner of booting makes any difference.  Less control over the system during boot maybe?  I dunno.

---

### Post by pxwpxw on 2008-11-04
> **WaeV said:**
> That's interesting, If I could get a GRUB CD like that, I could just boot up and go, then take out the CD and still have freedom to burn CDs or whatever.


So try it!

---

### Post by WaeV on 2008-11-04
I definitely will.  I'll resize my iPod partition tomorrow.

Ooh, I can even burn my own CD with my new DVD/CD burner!  (My old one broke about 7 months ago - I've been managing with Daemon Tools for my windows programs :/ )

---

### Post by WaeV on 2008-11-06
Ok I burned a copy of Super Grub Disk which I plan to practice with before I use it at school.  Nothing more awkward than a teacher asking what they hell you're doing whilst in the middle of typing in grub commands...

On a side note, I burned the CD with my new CD/DVD drive!  I've gone without one for too long.  After installation XP started hollering about "radical system changes" or summat and promptly bluescreened :roll: but Ubuntu is as good as ever.  I'll give word on my progress later.

---

### Post by pxwpxw on 2008-11-06
> **WaeV said:**
> Ok I burned a copy of Super Grub Disk which I plan to practice with before i use it at school.  
...
 I'll give word on my progress later.

Good move, will be interested to hear more.

---

### Post by WaeV on 2008-11-07
Well, the school macs won't take CDs for some reason.  I brought a live CD in today, but when I stuck it in the slot, nothing tried to suck it in.  I think they may have disabled the CD drive somehow.  Yes, I tried ejecting first, and I also tried it on multiple machines.

---

### Post by pxwpxw on 2008-11-07
What macs are they?
```

About This Mac - More Info
Hardware Overview:

  Machine Name:	Power Mac G5
  Machine Model:	PowerMac7,2
  CPU Type:	PowerPC 970  (2.2)
  Number Of CPUs:	1
  CPU Speed:	1.6 GHz
  L2 Cache (per CPU):	512 KB
  Memory:	2.25 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	5.1.5f2
  Serial Number:	YM413PDGPGA

```

---

### Post by WaeV on 2008-11-08
I have a four day weekend and can't check, but I know they're aluminum macs, 2.2 Ghz processor.

Also, I replaced my U3 USB drive's U3.iso with a live CD iso.  The drive is pretty well fooled, my BIOS lists an additional "Sandisk Cruzer" entry under the CD Drives category.

---

### Post by The PastyGangsta on 2008-11-08
Usually any Mac at a school (even the teacher's) is an older Mac, incapable of having the software or firmware updated due to the blocks installed by the lovely Tech. Dept.

Whatever was the absolute latest Mac firmware 3-4 years ago is most likely what you're dealing with.

---

### Post by WaeV on 2008-11-08
The macs are brand new this year.  Aluminum siding, OSX Leopard, and 2.2 Ghz processor.  I think they're even a late enough version to have bootcamp drivers preinstalled.

A fragment of the About I just realized I had saved:
> ATI Radeon HD 2400 XT:

  Chipset Model:    ATI Radeon HD 2400
  Type:    Display
  Bus:    PCIe
  PCIe Lane Width:    x16
  VRAM (Total):    128 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x94c8
  Revision ID:    0x0000
  ROM Revision:    113-B2250H-259
  EFI Driver Version:    01.00.259
  Displays:
iMac:
  Display Type:    LCD
  Resolution:    1680 x 1050
  Depth:    32-bit Color
  Built-In:    Yes
  Core Image:    Hardware Accelerated
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported
Display Connector:
  Status:    No display connected

---

### Post by _Poincare on 2008-11-09
So instead of all the bickering .... can someone answer the simple questioned asked back in page 1 "how do we boot Ubuntu from an external USB drive???"

---

### Post by cyberdork33 on 2008-11-09
> **_poincare said:**
> so instead of all the bickering .... Can someone answer the simple questioned asked back in page 1 "how do we boot ubuntu from an external usb drive???"
*sigh*

---

### Post by The PastyGangsta on 2008-11-10
> **_Poincare said:**
> So instead of all the bickering .... can someone answer the simple questioned asked back in page 1 "how do we boot Ubuntu from an external USB drive???"
The point of all the bickering is we cannot figure out how to do it, there is no simple predefined answer.  Everyone in here is probably going to wind up programming something completely new to solve this problem, or (like the author said) the answer is booting Ubuntu through grub through grub2 or something.

---

### Post by WaeV on 2008-11-10
I'll see how the U3 drive works on Wednesday, maybe that will be your answer.

---

### Post by WaeV on 2008-11-13
The Mac didn't recognize the drive during boot.

---

### Post by WaeV on 2008-11-17
Does anyone think that the school may have disabled booting from any device but the hard drive?  Not viewing the CD could have been normal, people have trouble booting from USB DVD drives as well, I've seen.  Plus the CD drives are disabled.

If I got an external firewire harddrive, how certain can I be that it will boot legacy?

---

### Post by shadowdude1794 on 2008-11-24
It's possible, I'd guess that they didn't because they are desktops but it is possible. As for the firewire... maybe target disk mode would work? It's possible that they didn't disable that for servicing reasons.

---

### Post by cyberdork33 on 2008-11-24
> **WaeV said:**
> If I got an external firewire harddrive, how certain can I be that it will boot legacy?It won't

---

### Post by WaeV on 2008-12-01
Do you have any suggestions as to why it wouldn't?

---

### Post by cyberdork33 on 2008-12-01
> **WaeV said:**
> Do you have any suggestions as to why it wouldn't?
for the exact same reason that USB doesn't work. You are trying to do the same thing, just over a different cable.

---

### Post by WaeV on 2008-12-04
Well, the firewire external enclosure arrived today.  I assume I would need to bless it for it to show up?

---

