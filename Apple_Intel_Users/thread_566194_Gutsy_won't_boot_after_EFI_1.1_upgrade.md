---
title: "Gutsy won't boot after EFI 1.1 upgrade"
date: 2007-10-03
forum: Apple Intel Users
---

### Post by widemos on 2007-10-03
I've just installed macbook efi update 1.1 and my system doesn't boot. It's a C2D macbook with gutsy updated today.

It boots until the splash screen but stalls just after showing the splash.

Any suggestions? Is there any way to downgrade the firmware?

---

### Post by mcdull2k on 2007-10-03
> **widemos said:**
> I've just installed macbook efi update 1.1 and my system doesn't boot. It's a C2D macbook with gutsy updated today.

It boots until the splash screen but stalls just after showing the splash.

Any suggestions? Is there any way to downgrade the firmware?

Have you tried rEFIt?

---

### Post by widemos on 2007-10-03
Refit works fine, shows the menu (osx and linux) and starts to boot any of them.

OSX starts well, but linux stalls after showing the splash screen.

---

### Post by pxwpxw on 2007-10-03
What partitions have you got and what is on them?
Did it break after the EFI firmware 1.1 upgrade or after the gutsy update?

---

### Post by widemos on 2007-10-03
There seems to be a compatibility problem, Gutsy nor Feisty Live-CDs won't boot. They fall to a recovery shell also.

Gutsy was working in this laptop from June without any major problem.

---

### Post by pxwpxw on 2007-10-03
I have  a MacBook C2d,  EFI 1.1 firmware upgrade 2 days ago,  I just loaded Feisty Live CD i386, all goes. 
Dont have gutsy to try. 
Did you have anything on Partition #1, the EFI partition?

---

### Post by widemos on 2007-10-03
I have refit installed, I think don't have anything else.

---

### Post by bsantos on 2007-10-03
That's sad to know. Inconsistent issues suck. I updated on a C2D and had no problem. You did the whole update? Holding the power button when turning the MB on?

PS: Gutsy is so sweet on the MacBook... :o it just lacks gst support for iSight and an updated madwifi module, lets hope 15 days is enough to get this fixed. I also have keyboard mapping issues on the Portuguese layout (<> on the wrong key and ' ` instead of § ± on the other key).

---

### Post by widemos on 2007-10-03
The update went fine, the system info on osx shows the correct version of the firmware.

I also tried to gptsync the partitions, but no luck. Will keep trying or will try to restore from mac os cds and reinstalling everiything. :-(

---

### Post by bsantos on 2007-10-03
But do you get any error? Does it drop to a console? Is there any error shown?

---

### Post by nicfagn on 2007-10-03
Try to boot in recovery mode so you can see the last kernel message before hang.

---

### Post by widemos on 2007-10-03
Let's go step by step:

1. Here is a "screenshot" of what my macbook says:

[http://picasaweb.google.com/widemos/Misc/photo#5117127618919267938]("http://picasaweb.google.com/widemos/Misc/photo#5117127618919267938")

2. I can't boot into safe mode because the keyboard doesn't work at all. Also, in emergency shell, the keys give me two characters per keystroke, no matter how slow I type. Nice, isn't it?

3. I've tried to boot a livecd to manually edit /boot/grub/menu.lst but no success, livecd doesn't boot.

4. I've used ext2fsx to mount the Ubuntu partition under OSX. I can see the data but can't touch it, perhaps because it's not cleanly unmounted.

Thank you for your help.

---

### Post by bsantos on 2007-10-03
It seemed the update fixed keyboard issues on grub... are you sure the update applied successfully?

That message is because the uuid of the root partition changed, or the partition table changed. How was your partition table before? Did you erase the efi partition?

---

### Post by widemos on 2007-10-03
I didn't erase the EFI partition. At least not conciously.

Grub does have the same or worse problems than before. I was able to boot under knoppix 5.0.1 but the keyboard runs very badly (repeated keystrokes and erratic speed).

Is there any way I could repatch it?

---

### Post by nicfagn on 2007-10-03
To restore the firmware read  [here]("http://www.apple.com/support/downloads/firmwarerestorationcd14.html").

---

### Post by cyberdork33 on 2007-10-03
I would guess the kernel line is incorrect in your menu.lst from that error. Note that you do not have to use an Ubuntu live cd to mount your parition to edit files. It can be any live cd. 

Where is your Live CD failing? Can you get an error message for that?

Also, your keyboard seems to be acting very odd. I have not heard of these problems before. You might try the Firmware Restore CD from Apple
[http://www.apple.com/support/downloads/firmwarerestorationcd14.html](http://www.apple.com/support/downloads/firmwarerestorationcd14.html)

EDIT: Someone beat me to it.

---

### Post by widemos on 2007-10-03
The live cd doesn't give any error, and can't switch consoles.

I give up, will try to reinstall everything.

---

### Post by widemos on 2007-10-03
Reinstalling OSX didn't make any difference.

Here's a screenshot of what the livecd of ubuntu feisty says after a few seconds after the ubuntu splash screen logo:

[http://picasaweb.google.com/widemos/Misc/photo?authkey=enHypeLwFF4#5117230745379012210]("http://picasaweb.google.com/widemos/Misc/photo?authkey=enHypeLwFF4#5117230745379012210")

I'm desperate, this computer is my worktool :-(

---

### Post by cyberdork33 on 2007-10-03
> **widemos said:**
> Reinstalling OSX didn't make any difference.

Here's a screenshot of what the livecd of ubuntu feisty says after a few seconds after the ubuntu splash screen logo:

[http://picasaweb.google.es/widemos/Misc/photo#5117230745379012210](http://picasaweb.google.es/widemos/Misc/photo#5117230745379012210)

I'm desperate, this computer is my worktool :-(

did you try the firmware restore?

---

### Post by widemos on 2007-10-04
Yes I did, got the leds flashing, inserted the CD and... nothing!!! the computer continues booting normally after a long beep. Also tried with the CD already in the drive.

(I downloaded and burned the CD two times if you are going to ask that) ;-)

Thanks for your support.

---

### Post by nicfagn on 2007-10-04
The 'can't acces tty' is a busybox misleading message see [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129612").
For the USB error I would try to disconnect every external device, if you have it, see [here.]("https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54273").
For the ata problem you can try to add the **irqpoll** boot option to the kernel command line, see [here]("http://ubuntuforums.org/showthread.php?t=440122").
Hope it helps in some way.

---

### Post by cyberdork33 on 2007-10-04
> **widemos said:**
> Yes I did, got the leds flashing, inserted the CD and... nothing!!! the computer continues booting normally after a long beep. Also tried with the CD already in the drive.

(I downloaded and burned the CD two times if you are going to ask that) ;-)

Thanks for your support.

How are you burning these CD's? I know you said they were working before, but something may have changed in the firmware that is giving you quirks. I have always had trouble burning bootable discs from within OSX (especially BSD). I have to burn them very slow, and even then they do not work all the time. I have seen people post about the error you are getting on the Live CD before, i don't know that anyone got a fix though. I have also seen some issues with USB on these updates. Do you have a lot of USB devices connected?

[http://ubuntuforums.org/showthread.php?t=543263](http://ubuntuforums.org/showthread.php?t=543263)
[http://ubuntuforums.org/showthread.php?t=499677](http://ubuntuforums.org/showthread.php?t=499677)
[http://ubuntuforums.org/showthread.php?t=490385](http://ubuntuforums.org/showthread.php?t=490385)

---

### Post by widemos on 2007-10-04
I don't have any usb device connected. Ubuntu CDs I'm using are original CDs from canonical. I've tried both Feisty 7.04 32 and 64 bit CDs and nothing. THEY BOOT but hang after a short while.

Also, my keyboard is completely frozen within ubuntu, so I can't choose any boot option nor pass any parameter to the kernel. It used to work sometimes but since the upgrade, the keyboard has stopped to work completely under anythind different to osx.

---

### Post by cyberdork33 on 2007-10-04
> **widemos said:**
> Also, my keyboard is completely frozen within ubuntu, so I can't choose any boot option nor pass any parameter to the kernel. It used to work sometimes but since the upgrade, the keyboard has stopped to work completely under anythind different to osx.

This is the biggest reason I think there is an issue with your firmware update because, for most, the firmware updates fixed the keyboard problems. Now my keyboard works EVERYTIME in grub and other bootloaders, whereas, it did not before.

---

### Post by nicfagn on 2007-10-04
I missed this note from the [Firmware Restoration CD 1.4]("http://www.apple.com/support/downloads/firmwarerestorationcd14.html") page:
[INDENT]**Note**: This CD cannot be used to return an Intel-based Macintosh 
computer's firmware to a previous version if a successful update has 
already been performed.
[/INDENT]
So it seems you are stuck with it :-(
Perhaps you can borrow an external usb or bluetooth keyboard, and see if they work.
In a previous post you mentioned an emergency shell where the keystrokes were doubled. How did you access this emergency shell?

---

### Post by cyberdork33 on 2007-10-04
> **nicfagn said:**
> Perhaps you can borrow an external usb or bluetooth keyboard, and see if they work.
Yea I used to have to replug a usb keyboard when the bootloader was up in order to get the keyboard working (before the firmware update).

---

### Post by widemos on 2007-10-04
I've tried already with a PC keyboard and it dowsn't even detect it. Under osx it runs, but not in the bootloader or in the emergency shell after the failed ubuntu boot. This is amazing.

Tomorrow I'll go to an apple store to ask for help. I will post my findings.

---

### Post by widemos on 2007-10-04
> **nicfagn said:**
> I missed this note from the [Firmware Restoration CD 1.4]("http://www.apple.com/support/downloads/firmwarerestorationcd14.html") page:
[INDENT]**Note**: This CD cannot be used to return an Intel-based Macintosh 
computer's firmware to a previous version if a successful update has 
already been performed.
[/INDENT]
So it seems you are stuck with it :-(
Perhaps you can borrow an external usb or bluetooth keyboard, and see if they work.
In a previous post you mentioned an emergency shell where the keystrokes were doubled. How did you access this emergency shell?

I managed to boot knoppix 5.1.1 with a kernel 2.6.17. It boots and can type, but doesn't see any hard disk and the keystrokes are duplicated. In the emergency shell I can't type anything (it pops automatically when ubuntu fails to load the kernel).

---

### Post by bsantos on 2007-10-04
> **widemos said:**
> I managed to boot knoppix 5.1.1 with a kernel 2.6.17. It boots and can type, but doesn't see any hard disk and the keystrokes are duplicated. In the emergency shell I can't type anything (it pops automatically when ubuntu fails to load the kernel).

That doesn't look good... :-( I don't think you'll get help to third party OSs from Apple, but I might be wrong since I don't have any experience on that. :)

Just noticed the efi partition is used to hold the updates (I just mounted it and it only contains the firmware update).

Good luck!

PS: When I installed Ubuntu for the first time on the MB, I tried to use Bootcamp, etc. The next time I partitioned the disk on the OSX boot cd, installed OSX then installed refit and Ubuntu from the livecd.

---

### Post by nicfagn on 2007-10-04
> **widemos said:**
> I managed to boot knoppix 5.1.1 with a kernel 2.6.17. It boots and can type, but doesn't see any hard disk and the keystrokes are duplicated. In the emergency shell I can't type anything (it pops automatically when ubuntu fails to load the kernel).

 If you don't mind losing some settings persisted between reboots like sound volume and others, you can try [resetting the PRAM]("http://docs.info.apple.com/article.html?artnum=2238").
You can also try to use the **irqpoll** boot option with knoppix, to see if the hard disk is detected.

Good luck

---

