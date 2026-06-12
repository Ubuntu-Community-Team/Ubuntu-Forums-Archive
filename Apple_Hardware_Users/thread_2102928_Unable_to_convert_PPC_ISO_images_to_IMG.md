---
title: "Unable to convert PPC ISO images to IMG"
date: 2013-01-08
forum: Apple Hardware Users
---

### Post by oli1987 on 2013-01-08
Hello

I am really curious about trying Ubuntu for the first time on my aging but still running Powerbook G4 12"

No problem w/ OS X 10.5, but I'm just looking to try something new.

I am going the USB stick route, interested in trying a live version first.
SO, I am following the exact steps described on this page :
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)

Except that the hdiutil tool seems to exit w/ an invalid usage flag...
gives me this after hinting at progress (the "..........." that indicates the process is working)
> "Usage:    hdiutil convert -format <format> -o <outfile> [options] <image>
    hdiutil convert -help
oli-buro:~ smoke$ 
If I try to do the conversion via Apple's Disk Utility.app interface, the app, after, again, progressing a little bit, will throw an "invalid arguments" error.

So in short I am unable to convert the ISO to DMG so that my Powerbook will read it on startup. 

I tried to format my USB stick w/ the ISO image (instead of dmg) and the Powerbook seems to be unable to boot w/ it, even if it does recognize it's a Linux boot.

Thanks for any help.

PS I've tried w/ these 3 images :
lubuntu-12.04-alternate-powerpc
lubuntu-12.10-desktop-powerpc
ubuntu-12.04-desktop-powerpc
tried conversion on 10.6 (mactel) & 10.5 (ppcg4), both fail w/ same err
IIRC this didn't happen w/ non-ppc mactel ISO's...
btw what are the checksums for these files ? maybe they got corrupted somehow over IP

---

### Post by oli1987 on 2013-01-08
Well I guess I'm having the same problem as the OP of this thread...
[http://ubuntuforums.org/showthread.php?t=1988291&highlight=hdiutil](http://ubuntuforums.org/showthread.php?t=1988291&highlight=hdiutil)
and [https://discussions.apple.com/thread/2715783?start=0&tstart=0](https://discussions.apple.com/thread/2715783?start=0&tstart=0) as well
Which hasn't been solved. 



:popcorn:

---

### Post by oli1987 on 2013-01-08
well ! I was going to use bittorrent to re-download because I thought the images I got thru HTTP had been somehow corrupted....
wrong !
it really looks like the ISOs I dled are in check with the MD5s on the server

> oli-buro:~ smoke$ md5 /Users/smoke/Downloads/lubuntu-12.10-desktop-powerpc.iso 
MD5 (/Users/smoke/Downloads/lubuntu-12.10-desktop-powerpc.iso) = df0e8ffda72778c8c0eb7a94714019d3
> **from the ubuntu servers**
df0e8ffda72778c8c0eb7a94714019d3 *lubuntu-12.10-desktop-powerpc.iso

Went down to 10.04, same errors. I wonder how people are getting those ISOs to convert.... (??!?!?!?!)

---

### Post by oli1987 on 2013-01-08
oddly enough, the downloaded ISOs *will* mount (w/ warnings). and once mounted, if I try to clone the mounted disk to my key, it works. then, the thing is the powerbook won't recognize it on startup... 

this is kind of driving me nuts at the moment.

---

### Post by oli1987 on 2013-01-08
anyone ? so everyone is able to convert to IMG w/o any prob ? every ppc user ?

sincerely, I really don't get it. I am also trying w/ 2 different macs here...
how can I get a readable disk image ?

---

### Post by oli1987 on 2013-01-09
anyone ? why is everyone able to convert the ISO to IMG but me, and on 2 totally different Macs ?
am I dumb ? or is this a bug ?

---

### Post by barbaGNU on 2013-01-11
last time i tried it worked like a charme following this howto:
[http://mintppc.org/content/usb-installation-osx](http://mintppc.org/content/usb-installation-osx)

---

### Post by iMac71 on 2013-01-11
the following tutorial might be useful:
[http://www.proposedsolution.com/howto/howto-macosx/create-bootable-usb-thumb-drive-iso/](http://www.proposedsolution.com/howto/howto-macosx/create-bootable-usb-thumb-drive-iso/)

---

### Post by oli1987 on 2013-01-13
> **iMac71 said:**
> the following tutorial might be useful:
[http://www.proposedsolution.com/howto/howto-macosx/create-bootable-usb-thumb-drive-iso/](http://www.proposedsolution.com/howto/howto-macosx/create-bootable-usb-thumb-drive-iso/)

well.. this seems to do the same as when I burn the ISO directly w/o converting...

e.g. the powerbook g4 12" will boot (w option key),  recognize a linux thumb drive.
but when I try to actually boot with it, a blank or black screen will appear like 1 second and it will fallback to the boot choices screen.

maybe the thumb drive is 100% readable then, but another, separate and new problem prevents from booting into ubuntu successfully... ?!

---

### Post by rsavage on 2013-01-13
> **oli1987 said:**
> 
e.g. the powerbook g4 12" will boot (w option key), recognize a linux thumb drive.
but when I try to actually boot with it, a blank or black screen will appear like 1 second and it will fallback to the boot choices screen.

 
Well if it is before 12.10 then yes it will do this. You will save yourself a lot of time if you read the Ubuntu PowerPC FAQ [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

---

