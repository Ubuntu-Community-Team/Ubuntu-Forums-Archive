---
title: "Lubuntu 14.10 PPC Live CD Doesn't Advance Past Splash Screen"
date: 2014-06-19
forum: Apple Hardware Users
---

### Post by JGreenidge on 2014-06-19
Greetings:

I have a heirloom G3 full-RAM 900mHz iBook with a long defunct/dead hard drive according to S.M.A.R.T.  I wish to at least partially resurrect it sans HD via a Live CD by whose LibreOffice and Firefox apps I can use to work with documents I store on a USB flash on the go. 

I have tried to boot up a Lubuntu 14.10 Live CD on it and only get the blue splash screen running with blinking dots for over two hours. To break this deadlock I hit F6 as some Ubuntu forum users mentioned and the blue screen turned black with the lines:

stdin: Not a typewriter
stdin: I/O error
stdin: I/O error
stdin: Not a typewriter

It returns to blue splash screen if I hit other F-keys.

I'm a nontechie senior trying to play this by ear. Any assist would be much appreciated!

Thanks!
Jim in NYC

---

### Post by JGreenidge on 2014-06-20
It appears it takes almost 90+ minutes for Lubuntu 14.04 or 14.10 to load on my G3 iBook. Is this normal? Is there any way it can be speeded up? Are there any speedier alternatives? I plan to let the system sleep than reboot for the rest of the time once it's up.

Thanks!

Jim in NYC

---

### Post by Bucky Ball on 2014-06-20
Don't use 14.10. It is very much a development release, testing, buggy and not released until October! Stay away, that's not for you from your description of yourself (non-techie). 

Stick with 14.04 LTS. ;)

Also, by the sounds of your description, what you want is a persistent install to USB, not a LiveUSB boot everytime. Much more appropriate. See here for an explanation:

[http://www.linuxliveusb.com/en/help/faq/persistence](http://www.linuxliveusb.com/en/help/faq/persistence)

And here for a bit of a how-to:

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

With a persitentence install to USB you can save files directly to the USB you're booting from. It is like a completely self-contained OS and storage. Good luck. 

PS: I'm not an Apple user, but the creation of the media shouldn't be that different. :-k

---

### Post by JGreenidge on 2014-06-20
Thanks heartily for your swift reply! I will stick with Lubuntu 14.04 even though 14.10 did work when it finally booted. I was given by some users that G3 Mac computers can't boot from USB ports like later ones, so would that cripple any persistent install? My original idea was booting off the live CD then getting data off the USB flash. 

Jim in NYC

---

### Post by rsavage on 2014-06-20
> **Bucky Ball said:**
> 
PS: I'm not an Apple user, but the creation of the media shouldn't be that different. :-k

It actually is! [EDIT: that second link is okay - see post #14] There are some PowerPC instructions for live usb persistence in this section [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F) . I wrote those instructions just so that a testcase could be completed, but I don't recommend you follow them.

Taking apart an iBook is a bit of a traumatic experience, but it can be done.  If you ask around it is amazing how many people have spare hard drives that may go in it.  Or you can get a SSD drive for quite cheap money (make sure it has the old ide connection and not sata).  That would be the better solution.

Failing that, if you have a usb flash drive then just install the system to that.  It would be better than the live persistence route.

---

### Post by Bucky Ball on 2014-06-20
Ok, got ya. If you can't boot from a USB then I guess the LiveCD and USB storage is the go. 

I will change the title of the thread to reflect 14.04 LTS.

---

### Post by rsavage on 2014-06-20
> **JGreenidge said:**
> I was given by some users that G3 Mac computers can't boot from USB ports like later ones, so would that cripple any persistent install? My original idea was booting off the live CD then getting data off the USB flash. 

Jim in NYC

Actually, the G3 iBooks are better at booting usb than G4 ones.  They can all do it though.  p.s. 12.04 is the version to go for.

---

### Post by Bucky Ball on 2014-06-20
> **rsavage said:**
> It actually is!  There are some PowerPC instructions for usb persistence in this section [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F) . 

Thanks for the info. ;)

> **rsavage said:**
>  If you ask around it is amazing how many people have spare hard drives that may go in it.  Or you can get a SSD drive for quite cheap money (make sure it has the old ide connection and not sata).  That would be the better solution.

A new hard drive or SSD would definitely be easiest, and if you only need a USB dongle size, an SSD wouldn't be that expensive (and would be fast). 

> **rsavage said:**
> Failing that, if you have a usb flash drive then just install the system to that.  It would be better than the live persistence route.

Just wondering how if the hard drive isn't working ... with two USBs plugged in, one of them a LiveUSB?

---

### Post by rsavage on 2014-06-20
> **Bucky Ball said:**
> Just wondering how if the hard drive isn't working ... with two USBs plugged in, one of them a LiveUSB?
Presumably Jim already has a CD burned so he just needs to boot from that.  Once booted up, plug the USB flash drive in, run the installer program and select the usb flash drive as if it were a hard drive.  The only 'tricky' bit is getting the ibook to automatically boot from usb, but that is just a case of figuring out the openfirmware path.  

If he doesn't have a CD burned, then yes he could use a liveusb instead of a CD.

For completeness, you could even do a 'wubi' - [http://ubuntuforums.org/showthread.php?t=2224808](http://ubuntuforums.org/showthread.php?t=2224808)  (12.04 is the easier version to do this on).

---

### Post by Bucky Ball on 2014-06-20
> **rsavage said:**
> 

For completeness, you could even do a 'wubi' - [http://ubuntuforums.org/showthread.php?t=2224808](http://ubuntuforums.org/showthread.php?t=2224808)  (12.04 is the easier version to do this on).

Be aware, Wubi is no longer supported by Canonical and is no longer supported on these forums. Please refer here:

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

This is a recent decision by forum staff. Thanks.

---

### Post by JGreenidge on 2014-06-20
You people are amazing! If U.S. stores had such customer service response our economy wouldn't be the toilet it's in. Thanks!

Regarding any replacement HDs, right now consider this project a zero-cost challenge since I'm just stretching retirement keeping food on the table and weren't for third-hand hand-me down computers and free community WIFI like here I wouldn't have the pleasure of getting computer educated by the likes of you two! Thanks!

So things seem to be shaping up that my iBook might boot USB but I need to reconfigute my Live CD and install Casper persistence on one of these flash drives. I like the idea that the Live CD might tap configurations off a flash drive so you don't have to reinvent the wheel each time you boot up!! Fantastic! I'll see if I could mug through the info on the links you left and I'll report to you how well I've manged to grasp it all to do the job!

Good work!

Jim in NYC

---

### Post by Bucky Ball on 2014-06-20
If you have two USB slots, and can boot from a USB dongle, that is the best way rather than booting from the CD. It will be faster, but the disadvantage is you are a USB slot down permanently. That may be no deal-changer though. Depends how many USB slots you have and need. You can probably beg, borrow or steal a USB hub, with a bit of luck. ;)

PS: All good. We're here to help and glad we can be of some. ;)

---

### Post by rsavage on 2014-06-20
> **Bucky Ball said:**
> Be aware, Wubi is no longer supported by Canonical and is no longer supported on these forums. Please refer here:

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

This is a recent decision by forum staff and new threads asking for support with Wubi will be closed. Thanks.
Well the link was not for the real wubi (it being windows based), think of it more like a manual 'lubi'.  

Installing the system to a virtual disk (what I refer to as wubi) would be an elegant solution for Jim. Somebody might point out that SSDs are more likely to fail and virtual file systems are more vulnerable to corruption, but if you save your documents on the root flash drive folder outside the virtual filesystem then I don't see what the problem is.  This also means you can easily move and share the files between computers.

Whatever way you decide to go, Jim please read the PowerPC wiki pages.  For example, the Known Issues page has something about installing to usb on 12.04.  Don't waste your time doing internet searches, there is a lot of wrong or misleading information out there!

---

### Post by rsavage on 2014-06-20
Looking at the link Bucky Ball gave earlier ( [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) ) most of it should work on PowerPC.

At the yaboot prompt (instead of hitting F6) you will have to type
```

live [COLOR=#333333][FONT=Ubuntu]persistent
[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]

It is this link [/FONT][/COLOR]https://wiki.ubuntu.com/LiveUsbPendrivePersistent that doesn't really work on PowerPC.

---

### Post by rsavage on 2014-06-20
My final thought on this is that all the instructions make it look extremely complicated!!!  But in reality it isn't!!!

---

### Post by JGreenidge on 2014-06-22
Greetings!

An update of my struggle so far!

I successfully installed Lubuntu 14.04 via Live Installer CD to a 8gig flash drive. GPart reports that the flash is /dev/sdb1 unknown file system 31 KiB and /dev/sdb2/ ext4 7.27 GiB. I then stuck the flash in the brain-dead G3 iBook and followed most straightforward instructions at [https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware](https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware) 

The dev/ls came out with:  ff984730 usb@18 /disk@1

I did the boot as mentioned and I ended up on a "OF" line stating:

Specified partition is not valid. Can't OPEN: usb1/disk@1:2,\yaboot

I did try tinkering with it as usb0 and got -

MAC PARTS = Specified partition is not valid. Can't OPEN: mac 0/ata-4@f000/:10,11 tbxr@0, but isn't "ata" meant for a hard drive that's dead and which I'm trying to by-pass via booting up a flash?

My flash's yaboot config file in etc is:

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-Maxtor_2F040L0_F1HKEWEE-part2"
partition=2
root="UUID=1052cdf8-9b9f-44ab-8c0e-17e03927ce3e"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash video=radeonfb:1024x768-32"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash video=radeonfb:1024x768-32"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda3.
image=/pci@f4000000/ata-6@d/@0:3,/boot/vmlinux
    label=Ubuntu-Linux
    root="UUID=21f027dc-44b0-4234-b45e-1916e6e55afd"
    append=" ro quiet splash video=radeonfb:1024x768-32"
    initrd=/pci@f4000000/ata-6@d/@0:3,/boot/initrd.img
```

Any tips to keep me on track would be much appreciated!

Jim in NYC

---

### Post by Bucky Ball on 2014-06-23
I can't give you any tips with your problem, but I can give you this tip: Please use [code] tags [ /code] when posting terminal output/code. Makes it a lot easier to read, clear and keeps the format. Thanks.

I have inserted them in your last post as an example. Edit and have a look how they're used (you can also use Adv Reply or Go Advanced when editing a post, highlight the code and click the # icon).

---

### Post by JGreenidge on 2014-06-25
Greetings:

I'm starting to wonder whether anyone's actually flash-booted Lubuntu off a PPC G3 iBook or any PPC Mac in general since it seems that it's the few people who write of such in articles who have ever done it. I Yahoo'ed and Googled for users who tell their tales of success and nothing comes up. Is there a way to find out whether any UbuntuForum subscribers have accomplished this? If it really isn't possible I'd like to know before delving any further.

Should I somehow re-title this topic to "Booting Ubuntu on PPC Macs"?

Thanks for any assist!

Jim in NYC

---

### Post by rsavage on 2014-06-25
> **JGreenidge said:**
> 
GPart reports that the flash is /dev/sdb1 unknown file system 31 KiB and /dev/sdb2/ ext4 7.27 GiB.
By the sounds of it you've somehow - and I really don't know how - managed to install without a bootstrap partition.  Openfirmware cannot read ext4 so you need another partition to hold yaboot/yaboot.config.

> I then stuck the flash in the brain-dead G3 iBook 
That makes it sound like you installed on a different machine? 

> and followed most straightforward instructions at [https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware](https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware) 

Don't know why you didn't follow the instructions in the FAQ.

Where did the yaboot.conf come from?

If you let the 14.04 installer do everything automatically (so that it installs a bootstrap partition) then you should (if your g3 ibook supports it) be able to boot the usb by holding down the option key.

---

### Post by rsavage on 2014-06-25
> **JGreenidge said:**
> I'm starting to wonder whether anyone's actually flash-booted Lubuntu off a PPC G3 iBook or any PPC Mac in general since it seems that it's the few people who write of such in articles who have ever done it. 
Yes it is possible.

I've updated my wubi instructions for usb booting.  It is untested since I don't have a working flash drive, but based on past experience I think I've got everything covered.  If it doesn't work I'll eat my hat.

---

### Post by michiganmac on 2014-06-26
> **JGreenidge said:**
> Greetings!

An update of my struggle so far!

I successfully installed Lubuntu 14.04 via Live Installer CD to a 8gig flash drive. GPart reports that the flash is /dev/sdb1 unknown file system 31 KiB and /dev/sdb2/ ext4 7.27 GiB. I then stuck the flash in the brain-dead G3 iBook and followed most straightforward instructions at [https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware](https://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware#howto_boot_apple_powerpcs_from_a_usb_drive_in_open_firmware) 

The dev/ls came out with:  ff984730 usb@18 /disk@1

I did the boot as mentioned and I ended up on a "OF" line stating:

Specified partition is not valid. Can't OPEN: usb1/disk@1:2,\yaboot

I did try tinkering with it as usb0 and got -

MAC PARTS = Specified partition is not valid. Can't OPEN: mac 0/ata-4@f000/:10,11 tbxr@0, but isn't "ata" meant for a hard drive that's dead and which I'm trying to by-pass via booting up a flash?

My flash's yaboot config file in etc is:

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-Maxtor_2F040L0_F1HKEWEE-part2"
partition=2
root="UUID=1052cdf8-9b9f-44ab-8c0e-17e03927ce3e"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
    label=Linux
    read-only
    initrd=/boot/initrd.img
    append="quiet splash video=radeonfb:1024x768-32"

image=/boot/vmlinux.old
    label=old
    read-only
    initrd=/boot/initrd.img.old
    append="quiet splash video=radeonfb:1024x768-32"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/sda3.
image=/pci@f4000000/ata-6@d/@0:3,/boot/vmlinux
    label=Ubuntu-Linux
    root="UUID=21f027dc-44b0-4234-b45e-1916e6e55afd"
    append=" ro quiet splash video=radeonfb:1024x768-32"
    initrd=/pci@f4000000/ata-6@d/@0:3,/boot/initrd.img
```

Any tips to keep me on track would be much appreciated!

Jim in NYC

You are missing a backslash before the word yaboot in your command. On my iBook G4, to boot off the front usb port I use this:

```
boot usb0/disk@1:2,\\yaboot
```

It will not work with only one backslash in before "yaboot".

---

### Post by michiganmac on 2014-07-08
@JGreenidge (OP)

Any progress on this?

---

