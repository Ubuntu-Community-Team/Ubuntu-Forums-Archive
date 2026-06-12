---
title: "Is anybody NOT having problems with a 12.04/Win 7 dual boot?"
date: 2012-07-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Buntu Bunny on 2012-07-27
The other day I ordered an Asus Essentio CM1740-02 tower. I'm just an average user with basic computer needs. The price for this model was right and the customer reviews outstanding. Then I come to the forums to research something unrelated and discover reports of booting issues with a Win7/12.04 dual boot. I inwardly groaned because I had this problem a couple years ago on my Dell with Windows and Lucid. Boot-Repair came to the rescue, but I'm wondering why this bug is still around. Shouln't it have been addressed by now? I had no problems with XP and 6.04; what happened?

My question is, has anyone NOT had problems with this? Are there any red flags I need to look for to alert me to potential problems? Anything I can do to avoid the problem again?

I know the question why I even want to keep Windows will arise. Like I said, I'm just an average user. Everytime I have hardware problems and need tech support, they can't/won't help when they find out I use Ubuntu. They want to pass me off to paid support (usually about $150 a pop). This forum is a fantastic resource and you guys have been the best in helping me, but it's a drag to try to fix a problem while running back and forth to the library computer. 

Too long winded, I know. I'd just like to hear success stories and know what to be on the lookout for before I install 12.04 LTS. Thanks.

---

### Post by OM55 on 2012-07-27
Hi Buntu Bunny,

From your text it looks like you have NOT yet tried to install Ubuntu 12.04 on the new computer, but just read somewhere that someone had a problem. Is that correct?

Dual boot is typically one of the relative easy issues to solve, the tools to resolve problems (if any) are freely available. As well, the Ubuntu 12.04 installer is more advance that its predecessors (your profile shows Ubuntu 10.04...) and would know how to overcome many issues.

I suggest you do an image backup of your new computer (use Image for Linux - [http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm) ) and then try to install Ubuntu 12.04. If you have ANY problems during or after the installation, please report back here and we'll help.

As for using dual-boot or not, have you ever consider VirtualBox? ([https://www.virtualbox.org/](https://www.virtualbox.org/)) Again, free. You can run an entire Windows machine as a window under Linux. 100% compatibility since it is Windows (need the Windows CD and serial number to install). This way you still have Windows to use when needed, without the dual boot requirement.

Anyway, try to install Ubuntu 12.04 first and report here the result.

---

### Post by Buntu Bunny on 2012-07-27
OM55, thanks! Your reply is much appreciated.

You are correct, I have not yet installed Ubuntu 12.04, in fact I'm still waiting on my new machine to arrive. It's in route and should be here by the beginning of next week. 

Yes, I have considered using VirtualBox, but my Dell did not come with a Windows CD. I'm guessing the Asus won't either. I did make the backup CDs as suggested, but could I use those to set it up in VirtualBox?

---

### Post by OM55 on 2012-07-27
I don't think any of the new computers sold today is coming with a Windows CD anymore (saving them a lot of money and hassle). Some would have an option for you to create an image CD using software they put on the hard drive, but this is different between vendors, and changing from time to time.

However, the backup CD's that you made should work just fine when you restore them into a virtual box. VirtualBox makes the environment completely like full hardware computer. Meaning, any software installed is 'fooled' to 'think' it is installed on a real computer. Since the image backup CD are of that same computer (having the same hardware drivers etc.) it should work very well when restored to a VirtualBox machine on the same computer.

Regardless, since legally you purchased the Windows license with the computer (you should have a Windows license sticker on the computer, the one with the hollogram), they HAVE to give you an option to reinstall Windows from scratch. For example - if after the warranty expired your hard disk dies and you install a new disk, you are not expected to buy a new copy of Windows... In the past they even provided a link to their site where you can download a CD image of the Windows version you have, and to install you required the number from the Windows sticker on the computer.

Again, just call your computer vendor and ask (give the example I suggested above).

Good luck!

---

### Post by drmrgd on 2012-07-27
Dual booting is generally not that much of a hassle.  However, with the new UEFI booting protocols in place (which your new computer may or may not have), it's become a little more tricky.  

My advice would be (if you don't choose to run Windows under a VW that is!) to find out if the system supports UEFI or not, and how it's currently set up (i.e. is Windows installed as UEFI or not).  That will affect how you do the Ubuntu install and the steps you'll need to take in the end.

As OM55 points, out, though, the 12.04 installer is pretty solid and took care of a lot of the work for me (I did try to over think the situation and outwit it first, which was a mistake!).  With a little help from this Forum, you should be able to get a stable dual boot system pretty easily I would think.

---

### Post by Buntu Bunny on 2012-07-30
OM55, thank you! Excellent information and that may be the way to go for me. I rarely need or use Windows, but feel better having it available just in case. 

Drmrdg, thank you to you as well! This is very helpful for me and the kind of information I needed.

New computer hasn't arrived yet; anticipated delivery is Aug. 1st. In the meantime I'm having to use a library computer. I figured I'd better do my homework while I waited. :)

---

### Post by pgmer6809 on 2012-08-03
> **Buntu Bunny said:**
> The other day I ordered an Asus Essentio CM1740-02 tower. I'm just an average user with basic computer needs. The price for this model was right and the customer reviews outstanding. Then I come to the forums to research something unrelated and discover reports of booting issues with a Win7/12.04 dual boot. I inwardly groaned because I had this problem a couple years ago on my Dell with Windows and Lucid. Boot-Repair came to the rescue, but I'm wondering why this bug is still around. Shouln't it have been addressed by now? I had no problems with XP and 6.04; what happened?

My question is, has anyone NOT had problems with this? Are there any red flags I need to look for to alert me to potential problems? Anything I can do to avoid the problem again?

I know the question why I even want to keep Windows will arise. Like I said, I'm just an average user. Everytime I have hardware problems and need tech support, they can't/won't help when they find out I use Ubuntu. They want to pass me off to paid support (usually about $150 a pop). This forum is a fantastic resource and you guys have been the best in helping me, but it's a drag to try to fix a problem while running back and forth to the library computer. 

Too long winded, I know. I'd just like to hear success stories and know what to be on the lookout for before I install 12.04 LTS. Thanks.

I am just now finishing installing 12.04 on a machine that came with Win7 installed. I will be posting my detailed description of how to do it within a day or so as soon as I finish writing it.
The short answer is that it can be dangerous if you are not  careful to preserve what windows7 wants to see. If you ARE careful it is not difficult, just a bit tedious.
pgmer6809

---

### Post by egeezer on 2012-08-04
I've been dual-booting Ubuntu or several of its derivatives with Windows 7 ever since 7 came out, and it has never given me a problem.  I just put together a homebuilt box with an Asus motherboard that has UEFI, and Ubuntu 12.04 installed slick as anything - of course there was no Windows on it to begin with, but the UEFI was essentially transparent to the boot installation process.  Your new machine was presumably made before that insidious "Secure" Boot mandate is set to begin, so you will probably just have to shrink the Windows partition enough to leave room for Ubuntu.  Some say it is best to shrink Windows with a Windows utility rather than Ubuntu's Gparted, but I've always used Gparted (usually from a PartedMagic CD) and it works like a charm.  In fact, when the installation CD shows a panel with partition choices, one should be "Install Ubuntu side-by-side with Windows".  It would most likely be safe to choose that option, because Canonical has done really well with its automatic partitioners.

---

### Post by ahlf7bfdj on 2012-08-05
How are you guys even able to boot from your Ubuntu thumbdrive?
 
Here is the scenario: I bought an Alienware X51 pc, installed with Win7 64bit and UEFI boot mode.
 
I downloaded Ubuntu and installed it using Universal USB installer.
 
I restarted my system, pressed F12 to select boot options, and choose the USB. 
 
The screen went black and then my computer proceeded to load Win7.
 
 
Can somebody please tell me how to install Ubuntu in UEFI mode alongside Win7? I went to this page: [[COLOR=blue]https://help.ubuntu.com/community/UEFIBooting[/COLOR]]("https://help.ubuntu.com/community/UEFIBooting") and got stuck at where efibootmgr comes in.
 
Would this help me: [[COLOR=blue]https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB[/COLOR]]("https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB")

---

### Post by annnomius on 2012-08-06
add me to the list of users with problems dual booting win7.

i just installed ubuntu 12.04 64-bit on a new asus zenbook prime, and the install seemed to go fine, and i can boot into ubuntu just fine.
however, the existing win7 can no longer boot. when i choose it from the grub menu, i get an "error, invalid efi path".

is there some way to recover this without requiring a re-install of win7 and loss of my existing data?

::ann

---

### Post by fab.head on 2012-08-06
> **annnomius said:**
> add me to the list of users with problems dual booting win7.

i just installed ubuntu 12.04 64-bit on a new asus zenbook prime, and the install seemed to go fine, and i can boot into ubuntu just fine.
however, the existing win7 can no longer boot. when i choose it from the grub menu, i get an "error, invalid efi path".

is there some way to recover this without requiring a re-install of win7 and loss of my existing data?

::ann

You could try to fix it with boot-repair.
Please read the following thread:

[http://ubuntuforums.org/showthread.php?t=2027888]("http://ubuntuforums.org/showthread.php?t=2027888")

---

### Post by annnomius on 2012-08-07
thanks fab.head! boot-repair did the trick (mostly-there is still some cleanup work).

i wonder, could you edit the zenbookprime wiki to make some comment about this, or to put in more precise instructions on how to install ubuntu as dual boot to win7 and what to do about uefi? i am surprised more people are not running into this problem with the zenbook prime models. perhaps they are not dual-booting.

quite honestly, i thought i totally hosed my win7 install-not a good feeling if a new user wanted to try ubuntu and seemed to lose their existing system!

---

### Post by pgmer6809 on 2012-08-07
> **fab.head said:**
> You could try to fix it with boot-repair.
Please read the following thread:

[http://ubuntuforums.org/showthread.php?t=2027888](http://ubuntuforums.org/showthread.php?t=2027888)


What has probably happened is that Grub has overwritten the MBR. 
You want to restore that to a valid Win7 MBR.
An MBR is only 512 bytes. 
If you did not make a backup of the MBR you could try to use EasyBCD to restore it. But for that to work you would need a working Windows system to run EasyBCD.
I don't know how interchangeable Win7 MBR's are; I think they are pretty generic. 
If you can get a Windows7 MBR from someehere you can use UBuntu to write it to your hard drive with the dd command. 
Of course then you would not be able to boot Ubuntu. 
See my post regarding how to create a dual boot system for ideas.
pgmer6809

---

### Post by drmrgd on 2012-08-07
> **pgmer6809 said:**
> What has probably happened is that Grub has overwritten the MBR. 
You want to restore that to a valid Win7 MBR.
An MBR is only 512 bytes. 
If you did not make a backup of the MBR you could try to use EasyBCD to restore it. But for that to work you would need a working Windows system to run EasyBCD.
I don't know how interchangeable Win7 MBR's are; I think they are pretty generic. 
If you can get a Windows7 MBR from someehere you can use UBuntu to write it to your hard drive with the dd command. 
Of course then you would not be able to boot Ubuntu. 
See my post regarding how to create a dual boot system for ideas.
pgmer6809

I don't believe this user is installing via MBR, but rather UEFI, as indicated by the "error, invalid efi path" error that she saw.

---

### Post by ahlf7bfdj on 2012-08-07
> **RustyLambda said:**
> How are you guys even able to boot from your Ubuntu thumbdrive?
 
Here is the scenario: I bought an Alienware X51 pc, installed with Win7 64bit and UEFI boot mode.
 
I downloaded Ubuntu and installed it using Universal USB installer.
 
I restarted my system, pressed F12 to select boot options, and choose the USB. 
 
The screen went black and then my computer proceeded to load Win7.
 
 
Can somebody please tell me how to install Ubuntu in UEFI mode alongside Win7? I went to this page: [[COLOR=blue]https://help.ubuntu.com/community/UEFIBooting[/COLOR]]("https://help.ubuntu.com/community/UEFIBooting") and got stuck at where efibootmgr comes in.
 
Would this help me: [[COLOR=blue][https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)[/COLOR]]("https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB")
 
Can anyone please assist me? I have asked on many forums for help, most say I should come here.

---

### Post by Petro Dawg on 2012-08-07
Just be sure to make a win 7 restore and repair disk set before trying a dual boot.  I've had no problems with my dual boot set up, just read several online tutorials before attempting, and everything went pretty easy.  preparation is the key to effective dual booting.

---

### Post by drmrgd on 2012-08-07
> **RustyLambda said:**
> Can anyone please assist me? I have asked on many forums for help, most say I should come here.

I'm not familiar with the Universal USB Installer (although it looks pretty interesting).  Your problem as you describe it suggests that there is a problem with the Ubuntu USB Installation drive that you made, since you're unable to boot to it.  Do you have any way to verify that the Ubuntu Live USB that you made is OK (e.g. try booting it from another computer)?  You might also try to create it again in the event that something didn't go right with the original creation.  I've only personally done this with the USB-creator software mentioned in the Community Documentation, but I'm sure the Universal USB Installer works fine.

[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)

---

### Post by ahlf7bfdj on 2012-08-08
> **drmrgd said:**
> I'm not familiar with the Universal USB Installer (although it looks pretty interesting). Your problem as you describe it suggests that there is a problem with the Ubuntu USB Installation drive that you made, since you're unable to boot to it. Do you have any way to verify that the Ubuntu Live USB that you made is OK (e.g. try booting it from another computer)? You might also try to create it again in the event that something didn't go right with the original creation. I've only personally done this with the USB-creator software mentioned in the Community Documentation, but I'm sure the Universal USB Installer works fine.
 
[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)
 
Yeah, thanks for your reply! I am able to boot from my Ubuntu USB drive fine if I my switch boot mode to Legacy boot. However, when I proceed to install Ubuntu onto a partition, it cannot detect Win7 (because it is UEFI, and I am on Legacy). Different boot modes =/= work together well.

---

### Post by drmrgd on 2012-08-08
OK, good to know the drive is bootable; that's one thing out of the way.  If Oldfred pops in this thread he can confirm, but I'm pretty sure that mixing and matching boot modes (i.e. BIOS and UEFI) won't work very well.  What I'm not clear on from your original post, though, is whether or not you're able to boot the USB in UEFI mode.  Are you saying that you can boot the USB in BIOS mode, but can not boot it in UEFI mode?  

I know for a fact that the latest (12.04) version of Ubuntu is bootable in UEFI mode.  However, after a quick Google search, I've found a few threads in Dell forums suggesting that there's something awry with these Dell systems that aren't allowing booting of CDs (nothing yet on USB Drives):

[http://en.community.dell.com/owners-club/alienware/f/3746/p/19455075/20144598.aspx#20144598](http://en.community.dell.com/owners-club/alienware/f/3746/p/19455075/20144598.aspx#20144598)

There is a link to this post (people trying to dual boot Windows 7 and Windows 8) that drives formatted as NTFS are not bootable by the system, and the drive has to be formatted as FAT.  How is your USB drive formatted?  Maybe this is related:

[http://forums.bit-tech.net/showthread.php?t=209045](http://forums.bit-tech.net/showthread.php?t=209045)

Not sure this is much help, but could be a start.

---

### Post by Buntu Bunny on 2012-08-08
UPDATE: Success, but ***not*** without problems. 

I finally got Ubuntu 12.04 installed as a dual boot with Win7 on my new machine. The problem was that while loading the live CD, I got the black screen. An good explanation and solutions for this and similar problems, can be viewed at this thread:
[URL="http://ubuntuforums.org/showthread.php?p=10069997#post10069997"]
"How to set NOMODESET and other kernel boot options in grub2"[/URL]

---

### Post by oldfred on 2012-08-08
@   	Buntu Bunny
Glad you got it working.

@RustyLambda
Please start your own thread and include UEFI in title if that is how your system is configured. Post hardware and screenshot of from gparted or list of existing partitions. It gets too confusing to answer different issues in one thread.

---

### Post by Cavsfan on 2012-08-08
Just in reply to the OP's question. I am quad booting Ubuntu 10.04, 12.04, 12.10 and Windows 7 all 64 bit without any problems what so ever.

---

