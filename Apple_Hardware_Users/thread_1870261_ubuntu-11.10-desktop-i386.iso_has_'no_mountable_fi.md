---
title: "ubuntu-11.10-desktop-i386.iso has 'no mountable file systems'?"
date: 2011-10-26
forum: Apple Hardware Users
---

### Post by irongiant14 on 2011-10-26
I downloaded two instances of **ubuntu-11.10-desktop-i386.iso** (32-bit) from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). Both .iso files failed to burn to cd. Three coasters. I thought maybe my DVD writer was fried but when I tried to mount the .iso in software, I get a warning that there are **'no mountable file systems'**.

Anyone else have this problem or know what the matter is?

I just want to create the CD on this Mac, the install is for an old Gateway with a poisoned boot disk.

---

### Post by irongiant14 on 2011-10-27
Has anyone successfully done it?

---

### Post by AdsoInk on 2011-10-27
I'm having the same issue as well. 

I installed the dev preview of Windows 8 and am looking to have an external HD install of Ubuntu for the purpose of a virtual XP and the ability to test legacy iterations of IE. Dual boot isn't an option as I don't have the time to do the heavy lifting to try and make it work. Doesn't really make sense since the .iso is either corrupt or some part of the XML is truncated.

As far as the .iso for Ubuntu is concerned, I've tried all 32-bit download methods and get this error when I try to mount the image on OSx and burn it to DVD.

We can't be the only ones experiencing this issue.

---

### Post by AdsoInk on 2011-10-27
I should add that OSx is unable to verify the image and throws an error stating that the .iso does not contain a recognizable filesystem. 

This doesn't really make a ton of sense since it's worked brilliantly in the past.

---

### Post by CamWH on 2011-10-28
I am having the same issue. When I attempt to convert it to an img (per ubuntu instructions) using the hdiutil command, it states that it is NTFS for some reason.

For example:

sh-3.2# hdiutil convert -format UDRW -o /ubuntu.img /Users/username/Downloads/oneiric-desktop-amd64.iso 
Reading Master Boot Record (MBR : 0)…
Reading Ubuntu 11.10 amd64               (Apple_ISO : 1)…
Reading  (Windows_NTFS_Hidden : 2)…

---

### Post by AdsoInk on 2011-10-28
I figured out yesterday that it's possible to burn an .iso from Windows and Linux. This seems to be an issue specific to Mac. 

I'm on Snow Leopard and have yet to make the leap over to Lion due to Lion's continued bugginess...

---

### Post by CamWH on 2011-10-28
> **AdsoInk said:**
> I figured out yesterday that it's possible to burn an .iso from Windows and Linux. This seems to be an issue specific to Mac. 

I'm on Snow Leopard and have yet to make the leap over to Lion due to Lion's continued bugginess...

You're right - I just copied the iso file over to a Windows XP virtual machine and it works as expected. Can anyone explain this?

I've never had an issue with an iso file on OS X prior to this.

---

### Post by sancra01 on 2011-10-28
I'm so glad I'm not the only one having troubles with the ISO. I've spent a week or so trying to sort it out to no avail.

I've been trying to boot my MacBook Pro 3,1 (running Leopard) with the Ubuntu 11.10 (x64) Live CD to see if all of the hardware is detected and works well.

So I downloaded the correct ISO (actually I've downloaded just about all of them now) - ubuntu-11.10-desktop-amd64+mac.iso and cannot mount it in OSX after the download. I have checked the MD5 and it's correct. I burned the ISO using disk utility anyway and attempted to boot from the CD but it failed. I've taken that same ISO to a Windows XP machine and burned the ISO to CD. The CD boots to Ubuntu from the Windows XP machine so I know that the CD has burned correctly. I then attempted to boot my MacBook Pro with the very same CD and it doesn't detect the disk.

I orginally thought the problem was with my MacBook Pro but now I'm not so sure.

It doesn't matter which ISO I download from Ubuntu (i386 etc) none of them mount.

I downloaded the Ubuntu 10.04 iso and was able to burn that to CD and it even mounts in OSX but when I attempt to boot my MacBook Pro it doesn't see the CD.

I'm stumped. It can't be this hard to boot the Ubuntu Live CD on my MacBook Pro.

Craig

---

### Post by jackdale on 2011-10-29
Hi guys, I'm a happy Mac OS X user on a MacBookPro (since Leopard and now using Lion) and Ubuntu user on custom built box and an old box (since 8.10 and now using 11.10).  I have never had any problems with burning the .iso to CD/DVD from the Mac (and I always use the mac to do it as it has the fastest burner in my house).

I'm not trying to be condescending, but your posts are a little unclear.  Can you confirm the following please:

1. Are you verifying the .iso download BEFORE trying to burn?
2. Are you using Disk Utility (rather than just do a normal burn) to correctly burn the .iso to CD/DVD?
3. Can the target computer boot from a known/trusted CD?

---

### Post by sancra01 on 2011-10-29
I can only speak for myself but as I said in my reply ...

1. I have verified the ISO by checking the MD5
2. I used Disk Utility in Leopard to burn the CD
3. I have booted my MacBook Pro with the original OS X installer CD and it works fine

Can you advise whether you have successfully booted your MacBook Pro using the Ubuntu 11.10 Live CD? No matter where I burn it (on Windows/Ubuntu/Mac OSX) I cannot boot my MacBook Pro using the Ubuntu 11.10 Live CD.

Thanks

---

### Post by sampathkuma on 2011-10-29
Try creating a bootable USB Stick.
Visit [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) for info.

---

### Post by sancra01 on 2011-10-29
I tried creating the bootable USB stick but again the MacBook Pro doesn't see it as a boot drive (doesn't matter if I hold down "C" or "Alt/Option" at boot - it just never sees the USB drive just like the it doesn't see the CD).

The problem seems to be with the ISO as stated by the original posters although the Ubuntu ISO that Mac OSX cannot mount (and cannot boot) works fine on a WinTel machine.

I guess my MacBook Pro is just not destined to run Ubuntu which is a great shame.

---

### Post by jackdale on 2011-10-30
> **sancra01 said:**
> 
...

Can you advise whether you have successfully booted your MacBook Pro using the Ubuntu 11.10 Live CD? No matter where I burn it (on Windows/Ubuntu/Mac OSX) I cannot boot my MacBook Pro using the Ubuntu 11.10 Live CD.

Thanks

Yes I can definitely boot from the 11.10 Live DVD.  After turning on, and holding Alt/Option key I get the following boot options:

MacBook Pro
Recovery HD
Windows (CD - this is how apple reads the Ubuntu DVD - essentially non-Mac must be Windows, right?)
EFI Boot

Choosing "Windows" will give you the usual Ubuntu graphical installer
EFI Boot will start-off not-so-graphical, but will get there eventually.

Also, if you check the download mirrors and the [daily build]("http://cdimage.ubuntu.com/daily-live/current/"), there is a specific Mac-64bit .iso that is supposed to "work properly" on Mac systems.

If this does not solve it, there is [this post]("http://www.multimediaboom.com/how-to-install-ubuntu-11-10-oneiric-ocelot-on-mac-osx/"), but I have never tried it, so I cannot vouch for it.

---

### Post by sancra01 on 2011-10-30
Thanks for posting those details.
 
When hold the Alt/Option key down on boot I only see MacBook Pro. I just can't figure it out.
 
I used this image ...
 
[http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-amd64+mac.iso)
 
... and it even boots on a WinTel machine but I can't see it on my MacBook Pro 3,1. I'm starting to think there's something odd about my hardware.
 
I'm going to try [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and see if that works. Will post my results.
 
Thanks
 
PS - Now that I think about it I don't believe Unetbootin will work on my MacBook Pro due to EFI but I'll give it a go when I get home tonight.

---

### Post by jackdale on 2011-10-30
> **sancra01 said:**
> 

... and it even boots on a WinTel machine but I can't see it on my MacBook Pro 3,1. I'm starting to think there's something odd about my hardware.
 


Maybe...I'm using MacBookPro 5,3

---

### Post by sancra01 on 2011-10-31
As I suspected the Unetbootin didn't work.
 
Might ask the question ...
 
Has anyone else been able to boot a MacBook Pro 3,1 with the Ubuntu 11.10 Live CD?
 
Or has anyone who has a MacBook Pro 3,1 running Leopard been able to mount the Ubuntu 11.10 iso in OSX?

---

### Post by feralman on 2011-11-02
FWIW, macbook pro with snow leopard, if I download the iso it won't mount. But if I crank up disk utility and verify the .iso, it fails to verify, but does put the .iso in the left pane. Selected that, and was able to burn a CD with the image, and that CD does mount. I haven't tried to install it and only tried it once, but figured I'd get this out there.

---

### Post by sancra01 on 2011-11-04
Thanks for trying it out and posting your results.

I'd be very interested in finding out whether you could boot your MacBook Pro from the Ubuntu CD you burned. Would also be interested in knowing what model of MacBook Pro you have (I'm running 3,1).

I'm starting to think that perhaps there's something wrong with my SuperDrive even though it can boot the OSX installer disk.

But then I've tried to boot Ubuntu from a USB drive and haven't had any luck with the computer seeing that device on boot either. I'm kind of stumped.

Cheers

---

### Post by brl on 2011-11-05
I installed Ubuntu 11.10 on my old MacBook Pro 2,1.  The amd64 version would not boot, but the 386i version loaded fine

On my new MacBook Pro 8,2 I get the 'no mountable file systems' for both 32- and 64-bit systems.  I also tried to install into a 32GB SDHC flash without success either.

rEFIt works so well on the 2,1 that it will launch Lion 10.7.2 on a disk plugged into USB.  I had hoped to put all Ubuntu onto the flash so I could just remove it.  I didn't want to use part of my 120GB SSD on my 8,2 for Linux.

For now I'll use my 2,1 for Ubuntu and hope somebody figures out this issue.

---

### Post by utah on 2011-11-14
Exact same issue here - Mac Book Pro Intel running Lion - I have installed Ubuntu quite a few times in the past with no issues. Something is not right ...

---

### Post by wentzr on 2011-11-16
macpro1,1
macpro3,1
macpro5,1

I've downloaded the ubuntuStudio 11.10 alt iso from 
[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/)

clicking the iso gives the warning

[I]The following disk images couldn't be opened:
ubuntuStudio-11.10-alternate-amd64.iso - no mountable file systems[/I]

on any of my 3 macpros... a 1,1, 3,1 AND 5,1. All three are running OS 10.6.8

This is not a PEBKAC or an ID10T error. The iso is not recognizable on a mac but the same iso (copied to external drive) works fine and can be burned to disk w/o issue from win7 or linux. 

Additionally, I just booted my macpro1,1 to a previous ubuntu 10.04 partition and was able to burn the same ISO file saved to my internal "workspace" drive from 10.04 which OS X on the same computer was telling me contained "no mountable file systems" 

something is DEFINITELY borked. 

Could somebody Canonical please stand up and explain what the hell is going on here? 

kthxbye.

---

### Post by otakusigma on 2011-11-16
I have a similar problem with this version, Ubuntu 11.10, I've downloaded the ISO file and I make a USB bootable with the Boot Disk Maker of Ubuntu 10.04, but it does not works, when I plug the Flash Drive into the Notebook to install it, it begins to load files and finally it shows a message "files error" or something like that, i need to do this again to see what's the message it shows exactly... now the question is, Could be the Ubuntu 10.04 who is causing this error? that maybe i have to make the boot USB from the Ubuntu 11.10 version?

---

### Post by majortom67 on 2011-11-18
> **brl said:**
> (...) On my new MacBook Pro 8,2 I get the 'no mountable file systems' for both 32- and 64-bit systems (...)

Me too...I believe a firmware update must come soon...
:-(

---

### Post by brl on 2011-11-21
All,

I purchased and installed VMWare Fusion for $50.  I needed it for something else (TASTE) distributed as a virtual machine.

I installed ubuntu-11.10-desktop-amd64+mac.iso without problem and it works fine, so far.

--brl

---

### Post by JollyRogers on 2011-11-30
Add me to the mix. I am glad I found this because I thought I was getting bad ISO's... MB and Mac Pro both throw the 'no mountable file error' when attempting to mount the ISO and burn it to CD/DVD. I have many Linux distress I play with and wanted to give Xubuntu a go since I really like the XFCE desktop. I guess I will attempt it in a windows machine (the burn that is).

This needs to be sorted! If I didn't have a lab where I could do this on another machine, well.. I would just run my beloved Slackware!

---

### Post by majortom67 on 2011-11-30
> **wentzr said:**
> 

could somebody canonical please stand up and explain what the hell is going on here? 

Kthxbye.

right !!!

---

### Post by brycesteiner on 2011-12-01
It appears the file system that's being used in the ISO is FAT but modified slightly and that seems to be causing the problem.

---

### Post by skr imaging on 2011-12-01
Okay, at least im not the only one with this issue.

I tried following the guide to making a usb stick installer with both i386 and amd64+mac ISOs and they both reslut in DMG files that have no mountable file system errors.

when i sudo dd to my USB key, it completes succesfully but then i get a message from OSX to initialize key because it can not be read (filesystem mimatch i suppose)

I was gonna try burning a cd istead but seeing many people have the same issue, I don't want more coasters :(

I have not yet tried the 10.04 LTS ISO.

I am using a Macbook mid 2010 (white) model:MacBook7,1.

this really sucks cause i thought Linux would be less hassle than windows...

Hope the devs get notified of the ISO having issues for mac folks.

---

### Post by davidryderuk on 2011-12-01
Maybe it's because they switched to hybrid iso files for Ubuntu 11.10. 

[http://www.h-online.com/open/news/item/Ubuntu-11-10-ISOs-to-be-hybrid-CD-USB-images-1261923.html](http://www.h-online.com/open/news/item/Ubuntu-11-10-ISOs-to-be-hybrid-CD-USB-images-1261923.html)

OS X seems to detect a different partition structure when comparing the mountable 11.04 iso file to the 11.10 iso file.

**11.10 amd64+mac CD**

```
partitions:
	partition-scheme: fdisk/ISO9660
	block-size: 512
	appendable: false
	hybrid-data:
		partition-scheme: ISO9660
		block-size: 2048
		appendable: false
		partitions:
			0:
				partition-name: Ubuntu 11.10 amd64              
				partition-start: 0
				partition-synthesized: true
				partition-length: 1428056
				partition-hint: Apple_ISO
				partition-filesystems:
					ISO9660: Ubuntu 11.10 amd
		burnable: true
	partitions:
		0:
			partition-name: Master Boot Record
			partition-start: 0
			partition-synthesized: true
			partition-length: 1
			partition-hint: MBR
			boot-code: 0x33EDFA8ED5BC007CFBFC6631DB6631C96653665106578EDD8EC552BE007CBF0006B90001F3A5EA2B06000052B441BBAA5531C930F6F9CD13721681FB55AA751083E101740B66C706D106B442EB15EB005A51B408CD1383E13F5B510FB6C64050F7E1535250BB007CB9040066A1B007E844000F828000664080C702E2F266813E407CFBC078707509FABCEC7BEA447C0000E8830069736F6C696E75782E62696E206D697373696E67206F7220636F72727570742E0D0A66606631D2660306F87B661316FC7B6652665006536A016A1089E666F736E87BC0E40688E188C592F636EE7B88C608E141B801028A16F27BCD138D64106661C3E81E004F7065726174696E672073797374656D206C6F6164206572726F722E0D0A5EACB40E8A3E6204B307CD103C0A75F1CD18F4EBFD000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000CC961500000000005E4BAD560000
		1:
			partition-name: Ubuntu 11.10 amd64              
			partition-start: 1
			partition-synthesized: true
			partition-length: 63
			partition-hint: Apple_ISO
		2:
			partition-start: 64
			partition-number: 1
			partition-length: 1427992
			partition-hint: Windows_NTFS_Hidden
			partition-filesystems:
				ISO9660: Ubuntu 11.10 amd
	burnable: true

```

**ubuntu 11.04 i386**

```
partitions:
	partition-scheme: ISO9660
	block-size: 2048
	appendable: false
	partitions:
		0:
			partition-name: Ubuntu 11.04 i386               
			partition-start: 0
			partition-synthesized: true
			partition-length: 1403484
			partition-hint: Apple_ISO
			partition-filesystems:
				ISO9660: Ubuntu 11.04 i38
	burnable: true

```

(see the 'hdiutil imageinfo' command for the whole output)

---

### Post by davidryderuk on 2011-12-01
@sancra01 

I was wondering whether your firmware is up to date, and whether you can you boot a windows CD?

[http://support.apple.com/kb/HT1237](http://support.apple.com/kb/HT1237)

---

### Post by skr imaging on 2011-12-02
OK here is an update of the situation for me. I used a PC to make the usb key using the 64bit version of 11.10. this is the software used to make bootable usb: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3)

Once key was created in windows, i plugged it in my Macbook mid 2010 and it was recognized without any issues. I could boot in live CD mode and I even Installed 11.10 on my Macbook mid 2010.

I then tried to use that same key on my other Macbook Early 2008 (core 2 duo).
it booted the live cd with no issues. I started install process and it completed succesfully.
BUT when i restarted my Mac, it never booted up to Ubuntu (all i saw after a while was the flashing question mark). I tried restart and pressing ALT to see if it detects the drive, nothing detected. I tried reinstalling with manual partitioning the drive, still no go.

I tried creating a key using 32bit 11.10 iso but it was not recognized as a boot device by the mac after creation where as the 64 bit iso worked.( I have a strong feeling the iso on site has issues.

I had a Ubuntu 10.04 LTS (32 bit) lying around, so decided to install that instead and it worked flawlessly. I will now try and just update from 10.04 to 11.10 and see if it works.

any pointers would help me a lot!!

---

### Post by davidryderuk on 2011-12-02
It sounds like you managed to install the EFI version of Ubuntu. I'm glad to hear that works, since I've got the same computer (the Macbook 7,1) and I was worried the install process might corrupt the firmware.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

Have you tried installing the propitiatory NVIDIA drivers? I was just wondering, because last time I tried that in EFI mode the display completely switched off and wouldn't work until I uninstalled the drivers again (using safe boot, apt-get and manually deleting the xorg.conf file).

In any case I'd love to hear whether everything works on that computer.

---

### Post by skr imaging on 2011-12-02
> **davidryderuk said:**
> It sounds like you managed to install the EFI version of Ubuntu. I'm glad to hear that works, since I've got the same computer (the Macbook 7,1) and I was worried the install process might corrupt the firmware.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089](https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089)

Have you tried installing the propitiatory NVIDIA drivers? I was just wondering, because last time I tried that in EFI mode the display completely switched off and wouldn't work until I uninstalled the drivers again (using safe boot, apt-get and manually deleting the xorg.conf file).

In any case I'd love to hear whether everything works on that computer.
everything worked well on Macbook 7.1... have not tried any NVIDIA drivers. kept everything stock. 

One thing I would like to add is that for fun, I resetted the PRAM of the MAcbook fter a reboot and since then, Ubuntu will not boot. I believe resetting PRAM messes up the GRUB. Some forums state that all you have to do is press alt/option key on startup and you should see the ubuntu drive... I tried but no drive is found (I never had seen the ubuntu drive when pressing ALT even when it was booting fine). I will probably just reinstall Ubuntu again by formating cause there is no important files on the drive yet.

I might try supergrub2 iso before formatting and see if i can restore grub without reinstalling. 

this sucks for someone who might have important stuff and who PRAM resets their Mac. I'll post update when i try out supergrub2.

I'm sure PC users do not have to suffer as much to install Ubuntu :(

---

### Post by davidryderuk on 2011-12-03
Maybe your problem has something to do with using the EFI version of Ubuntu. I have to admit I've never really heard of that problem before and I can only guess what cause is.

Supergrub2 would probably work, but if doesn't you might want to try 'boot repair' (just install it on your live usb).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

In particular the 'Bootinfo Summary' might give you a clue about what went wrong.

---

### Post by sancra01 on 2011-12-04
> **davidryderuk said:**
> @sancra01 

I was wondering whether your firmware is up to date, and whether you can you boot a windows CD?

[http://support.apple.com/kb/HT1237](http://support.apple.com/kb/HT1237)

Yes - my MacBook Pro 3,1 is fully up-to-date for firmware

Cheers

---

### Post by aaren_s on 2011-12-07
Hi, I faced the same problem with ubuntu-11.10-desktop-amd64.iso

This is not a straightforward iso -the real directory structures are embedded within a "Partition inside this .iso file",  but managed to create a mountable iso from it. Listed below are the steps:

1. convert the downloaded ubuntu .iso to UDRW image to burn it into a thumb drive.

$ hdiutil  convert -format UDRW -o ubuntu-11.10-desktop-amd64.img ubuntu-11.10-desktop-amd64.iso
You will get a ubuntu-11.10-desktop-amd64.img.dmg file. You can either rename it as a .dmg or as a .img, no problems ...

2. Insert the thumb drive and do a diskutil list. you should get the disk number for your thumb drive. Let's suppose it to be diskN

3. Dump the .img or .dmg file you got above into the thumb drive

dd if=ubuntu-11.10-desktop-amd64.img of=/dev/rdiskN bs=1m.

4. You should now see a strange unmountable partition diskNs1 (N=drive number for the thumb drive.) if not remove and re inser the thumb drive. This the actual .iso partition that contains the ubuntu installation/live CD stuff. To extract this, simply dump back the partition into a .iso file

dd if=/dev/rdisk1s1 of=./MyUbuntu-11-x86_64.iso bs=1m

Here rdisk1s1 is the partition inside the thumb drive I got after dumping the converted .img/.dmg in step 2.

Now MyUbuntu-11-x86_64.iso is the actual .iso image you get that you *can* open/mount in your mac by just double clicking on it or opening using diskutil. 

You can now convert *this* MyUbuntu-11-x86_64.iso into a UDRW .img for a thumb drive or just burn it into a CD. Hope it works ...

Cheers !!

---

### Post by calamaro_one on 2011-12-08
Hi aaren_s, i've tried your method on my macbook pro 3,1 but i can't boot from my usb pen even if i could mount the image fine.

---

### Post by elamd on 2011-12-08
I was having this exact problem, which led me here.

I burned the original downloaded ISO to a DVD, but OSX refused to mount it.  I re-downloaded the  ISO thinking it was bad, but still couldn't mount it, but decided to try burning it again anyway, this time to a CD, and remarkably, it worked.

Go figure.

I'm on a MB Pro 5,5 and Snow Leopard 10.6.8

---

### Post by matrym on 2011-12-13
There is a specific DVD file

[http://cdimage.ubuntu.com/releases/10.10/release/](http://cdimage.ubuntu.com/releases/10.10/release/)

If you try burning the CD file to a DVD, it won't work (at least on a macbook).

---

### Post by sancra01 on 2011-12-26
> **aaren_s said:**
> Hi, I faced the same problem with ubuntu-11.10-desktop-amd64.iso

This is not a straightforward iso -the real directory structures are embedded within a "Partition inside this .iso file",  but managed to create a mountable iso from it. Listed below are the steps:

1. convert the downloaded ubuntu .iso to UDRW image to burn it into a thumb drive.

$ hdiutil  convert -format UDRW -o ubuntu-11.10-desktop-amd64.img ubuntu-11.10-desktop-amd64.iso
You will get a ubuntu-11.10-desktop-amd64.img.dmg file. You can either rename it as a .dmg or as a .img, no problems ...

2. Insert the thumb drive and do a diskutil list. you should get the disk number for your thumb drive. Let's suppose it to be diskN

3. Dump the .img or .dmg file you got above into the thumb drive

dd if=ubuntu-11.10-desktop-amd64.img of=/dev/rdiskN bs=1m.

4. You should now see a strange unmountable partition diskNs1 (N=drive number for the thumb drive.) if not remove and re inser the thumb drive. This the actual .iso partition that contains the ubuntu installation/live CD stuff. To extract this, simply dump back the partition into a .iso file

dd if=/dev/rdisk1s1 of=./MyUbuntu-11-x86_64.iso bs=1m

Here rdisk1s1 is the partition inside the thumb drive I got after dumping the converted .img/.dmg in step 2.

Now MyUbuntu-11-x86_64.iso is the actual .iso image you get that you *can* open/mount in your mac by just double clicking on it or opening using diskutil. 

You can now convert *this* MyUbuntu-11-x86_64.iso into a UDRW .img for a thumb drive or just burn it into a CD. Hope it works ...

Cheers !!

I've just followed this procedure on my Macbook Pro 3,1 to the letter and like calamaro_one I cannot boot from the CD where I have burned the ISO. The actual ISO image that was created after running this ...

dd if=/dev/rdisk1s1 of=./MyUbuntu-11-x86_64.iso bs=1m

... is mountable under Finder which is a step in the right direction for me. When I burn it to CD it burns fine, finder mounts it once and then when I reboot the Macbook Pro and hold down the option key it doesn't see the CD and ejects it after about 20-30 seconds. After the OS has loaded and I insert the CD again the following message appears ...

"Disk Insertion - The disk you inserted was not readable by this computer".

I've tried burning the image a couple of times but with no success.

Getting closer but I still can't boot from a CD.

Craig

---

### Post by HowDidIGetHere? on 2012-01-18
Something has definitely gone wrong with Ubuntu and Macs. A 2011 MacBook Pro in my case. I have just spent a frustrating two days trying to boot from the CDs that I downloaded. I've followed all the instructions and I have partial success but it always fails with the message **'Unable to find medium containing live file system.'** I've also tried making bootable flash drives as per instructions but my Mac won't even look at the results.

I've successfully installed earlier versions of Ubuntu without any problems on Macs a few years ago but this latest version has me stumped. Judging from this thread it seems that I am not the only one having this problem. Maybe it's time that the wise men tried to fix it.

---

### Post by bytemangler on 2012-01-24
As wisemen, the first thing they need to do is acknowledge there is an issue with Mac OS X and the Ubuntu iso files

---

### Post by mypalmike on 2012-01-31
> **aaren_s said:**
> Hi, I faced the same problem with ubuntu-11.10-desktop-amd64.iso

This is not a straightforward iso -the real directory structures are embedded within a "Partition inside this .iso file",  but managed to create a mountable iso from it. Listed below are the steps:

1. convert the downloaded ubuntu .iso to UDRW image to burn it into a thumb drive.

$ hdiutil  convert -format UDRW -o ubuntu-11.10-desktop-amd64.img ubuntu-11.10-desktop-amd64.iso
You will get a ubuntu-11.10-desktop-amd64.img.dmg file. You can either rename it as a .dmg or as a .img, no problems ...

2. Insert the thumb drive and do a diskutil list. you should get the disk number for your thumb drive. Let's suppose it to be diskN

3. Dump the .img or .dmg file you got above into the thumb drive

dd if=ubuntu-11.10-desktop-amd64.img of=/dev/rdiskN bs=1m.

4. You should now see a strange unmountable partition diskNs1 (N=drive number for the thumb drive.) if not remove and re inser the thumb drive. This the actual .iso partition that contains the ubuntu installation/live CD stuff. To extract this, simply dump back the partition into a .iso file

dd if=/dev/rdisk1s1 of=./MyUbuntu-11-x86_64.iso bs=1m

Here rdisk1s1 is the partition inside the thumb drive I got after dumping the converted .img/.dmg in step 2.

Now MyUbuntu-11-x86_64.iso is the actual .iso image you get that you *can* open/mount in your mac by just double clicking on it or opening using diskutil. 

You can now convert *this* MyUbuntu-11-x86_64.iso into a UDRW .img for a thumb drive or just burn it into a CD. Hope it works ...

Cheers !!

Thanks, this was very helpful.  I found that you can reduce the steps a bit and save some time:

1.  Open the Disk Utility gui application.  (Easy way to find it:  Search using spotlight.)
2.  Drag the original .iso from Finder into the images section of Disk Utility (on the left side underneath the mounted drive list), and then double click on it there.  A faded "diskNs1" should appear underneath it, and a dialog box will say the disk is not mountable.  The "diskNs1" is the embedded .iso.
3.  Run "dd if=/disk/rdiskNs1 of=./ubuntu-extracted.iso bs=1m" to copy out the working .iso image.

I found that the "hdiutil convert" step seemed to do nothing to either .iso.  The output file was exactly identical to the input file (the file sizes and md5s match) except for the name.

---

### Post by pshapiro on 2012-02-27
Hey mypalmike, thanks for the suggestion this worked great for me.

Although on my machine (OS X 10.7.2) the disk device is at:

/dev/diskNs1

not

/disk/rdiskNs1

This is my first time trying out ubuntu on a Mac box. When I couldn't get the ISO to mount I didn't know what to think, since I've never had problems with ISOs with other distros before. I guess I just got unlucky picking this release to start with.

---

### Post by billstclair on 2012-02-27
I created a bootable USB key just as instructed at ubuntu.com. I can't mount it on my iMac, but it WILL boot on a Windows machine. I haven't tried to boot with it on my Mac. I DID try to boot a VMWare VM from it, but couldn't get the volume to appear in VMWare. Always got the message from OS X that "the disk you inserted was not readable by this computer".

The ISO file, as downloaded from ubuntu.com, works fine in a VMWare VM, if I mount it as a CD-ROM.

Fortunately, booting a Windows laptop is my intention, so no problem.

---

### Post by rpa.adak on 2012-04-18
I have the same problem. I have just format it. and it gone (in my ubuntu 11.10). try it.):P

---

### Post by bipedaljoe on 2012-09-20
thanks mypalmike and pshapiro!

the filenames were i little different for me too:
dd if=/dev/disk1s1 of=./ubuntu-12.04.1-desktop-i386.iso bs=1m
entered it in the os x Terminal
took 90 seconds... then a file copied file popped up in my documents folder
there was no loading/work indicator, so just wait for it to finish

thanks again! +1

So, anyone know why the .iso didn´t work?

EDT:  Restore Failure
Could not validate source - Invalid argument

Could not burn/restore it to a USB... probably this has happened to some of you others... will try again later

EDT: reason .iso not working:
[http://askubuntu.com/questions/153833/why-cant-i-mount-the-ubuntu-12-04-installer-isos-in-mac-os-x/153854#153854](http://askubuntu.com/questions/153833/why-cant-i-mount-the-ubuntu-12-04-installer-isos-in-mac-os-x/153854#153854)

...Recently, Ubuntu started making Hybrid ISOs. It's an ISO that can be burned onto a CD as usual, but also can be copied to a USB key and used as a LiveUSB without the help of Startup Disk Creator. It's just in so currently only the daily images are built that way....

[http://onubuntu.blogspot.se/2011/06/things-you-should-know-about-ubuntus.html](http://onubuntu.blogspot.se/2011/06/things-you-should-know-about-ubuntus.html)

EDIT: Guide on how to create a bootable USB in OS X
it´s a bit tricky if the commands are all new to you :)
[http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/](http://www.makeuseof.com/tag/how-to-create-an-ubuntu-installation-usb-on-the-mac/)

EDIT: Most of you have probably figured this out, most of the activity is from July, but I add some links if anyone stumbles upon this... :)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)

---

### Post by dmuos on 2012-12-15
Thank you mypalmike, #43 solved the problem in a ubuntu 12. (I was having the same issues in the newer versions).

D

---

