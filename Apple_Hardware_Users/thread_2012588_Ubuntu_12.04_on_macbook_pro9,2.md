---
title: "Ubuntu 12.04 on macbook pro9,2"
date: 2012-06-29
forum: Apple Hardware Users
---

### Post by sodaa on 2012-06-29
I seem to have tried all the various suggested methods for installing ubuntu on a mbp, but can't seem to get anything that works and was wondering if anyone has run into any new problems with the latest non-retina models?

I have a core i7 in my macbook, and model identifier is MacBookPro9,2. I have partitioned my HD using disk utility and have 700gig free space ready for the install (I haven't removed OSX Lion, it is still there in a 50gig partition).

**Problem:**

I am just getting a blank screen with a blinking cursor (unresponsive) in the top left whenever I boot from the disk. I left it for 20 minutes and nothing ever happened. This was without any boot manager, just holding "c" on startup.

**Attempted remedies:**

I have downloaded the 64 ubuntu iso from their site 3 times now and burned 4 separate discs to rule out some kind of corruption or burn error. I burned one in OSX Lion 10.7.4 and 3 on my windows 7 pc.

I tried holding "alt" instead and then navigating to the windows disc to boot. Same thing happens, blank blinking unresponsive cursor. I also tried going to the EFI disc which actually brings up a menu (after saying "error prefix is not set") asking if I want to install ubuntu, test for errors or partition. All three options lead me to an unresponsive blank screen (some without cursors).

I downloaded and installed rEFIt and if I hold "alt" on startup a linux penguin (Boot Linux from CD) appears in my boot options, along with the apple boot, and two others that I'm not sure of: "Boot EFI\boto\bootx64.efi from" and "Boot Legacy OS from". The "Boot Linux from CD" just takes me to the blank blinking cursor screen; again, I left if for 10+ minutes and nothing.

I heard that the detection of the graphics card might be a problem and that I need change to nomodeset, but I have tried pressing F6 in all of the boot menus listed above and no options appear.

Does anyone have any other suggested routes or can you see what I might have done wrong?

---

### Post by davidryderuk on 2012-06-29
When you boot in EFI mode a Grub 2 menu appears. The method for adding boot parameters (such as nomodeset) is different in Grub 2. See this post:

[http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter](http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter)

In step 2 you can select 'Install Ubuntu', since there's only one kernel on the CD.

---

### Post by lael on 2012-06-29
I couldn't get the stock 12.04 iso to boot on my MacBookPro6,1  I had to use the amd64+mac iso from the day just before launch. I think you can still find links to it in the forums.  I'm still seeding :-)

---

### Post by sodaa on 2012-06-30
> **davidryderuk said:**
> When you boot in EFI mode a Grub 2 menu appears. The method for adding boot parameters (such as nomodeset) is different in Grub 2. See this post:

[http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter](http://askubuntu.com/questions/19486/how-do-i-add-a-boot-parameter)

In step 2 you can select 'Install Ubuntu', since there's only one kernel on the CD.

Ok, so now I am at a screen entitled "GNU GRUB version 1.99-21ubuntu3" and commands:

> setparams "Install Ubuntu'

set gfxpayload-keep
linux /casper/vmlinuz file=/cdrom/preseed\ubuntu.seed boot=casper only-ubiquity quiet splash --
initrd /casper/intird.lz


where should I put the nomodeset parameter? I tried typing it immediately before and after "quiet splash", and at the end of the line, and hit F10 and each time the screen went blank and nothing happened (left it for approx 5 mins each time).

---

### Post by davidryderuk on 2012-06-30
You can add the kernel parameter after "quiet splash". 

If that doesn't work you might want to try removing "quiet splash" from the list of parameters. That should cause Ubuntu to boot in text mode. It might help to see the last few lines printed off before the crash. 

Splash Screen + nomodeset:

```
linux /casper/vmlinuz file=/cdrom/preseed\ubuntu.seed boot=casper only-ubiquity quiet splash nomodeset --
```

Text Mode + nomodeset:

```
linux /casper/vmlinuz file=/cdrom/preseed\ubuntu.seed boot=casper only-ubiquity nomodeset --
```

---

### Post by sodaa on 2012-06-30
Still just goes straight to a blank screen, nothing is printed on screen after I hit F10, with both methods (I actually tried these by accident before; I was trying all kinds of combinations).

If I tried installing an earlier version of ubuntu like lael said, can I just upgrade to 12.04 from within ubuntu and have exactly the same OS?

---

### Post by davidryderuk on 2012-06-30
You could upgrade from an earlier version of Ubuntu, although you might have problems with individual applications. It sounded like lael was suggesting installing from the amd64+mac variant of Ubuntu though. I'm not sure why it has to be from the day before Ubuntu's release.

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

Have you tried booting from USB? You can install Unetbootin in OS X, and use it to create a USB version of the install disk. You have to use the 64-bit version of Ubuntu. It won't work with the 32-bit or the amd64+mac version.

I found link describing some of the differences between booting in EFI mode (Selecting EFI Disk) and BIOS emulation mode (Selecting Windows Disk). 

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by davidryderuk on 2012-06-30
I guess when installing with EFI mode (from the CD or using USB), you have to be aware of possible firmware corruption.

> Caution for Mac owners

From Ubuntu 11.04 onwards (x86_64 only), the ISO CD supports UEFI booting and the Ubuntu installer will try to set up the bootloader for (U)EFI boot. But the installer formats the EFI System Partition to FAT16 (even if the filesystem is non-empty) and also uses efibootmgr, therefore Intel Macs may fail to boot due to corrupted firmware. This feature is not recommended on Mac models because it can corrupt the firmware. You will need to reflash the firmware to repair it.

On Macs use only the Mac alternate ISO CD

---

### Post by sodaa on 2012-06-30
The desktop amd64 + mac iso doesn't seem bring up an EFI boot option when I hold "alt" on boot, just the windows boot which leads me to the blank page/blinking cursor. The standard version I downloaded from the ubuntu site, brings up both the windows and EFI boot options. Really not sure what to do at this stage.

---

### Post by davidryderuk on 2012-06-30
> 
The desktop amd64 + mac iso doesn't seem bring up an EFI boot option when I hold "alt" on boot, just the windows boot which leads me to the blank page/blinking cursor.

That sounds about right. The amd64+mac CD is just like the normal CD, except that it only supports BIOS booting (Windows Boot). 

[http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image)

Have you tried USB booting, with Unetbootin and the amd64.iso?

I found the following threads about your computer (or similar).

[https://bugzilla.redhat.com/show_bug.cgi?id=834076](https://bugzilla.redhat.com/show_bug.cgi?id=834076)
[http://forums.fedoraforum.org/showthread.php?t=281038](http://forums.fedoraforum.org/showthread.php?t=281038)
[https://bbs.archlinux.org/viewtopic.php?id=144089](https://bbs.archlinux.org/viewtopic.php?id=144089)
[http://ubuntuforums.org/showthread.php?t=2007444](http://ubuntuforums.org/showthread.php?t=2007444)

A lot of the solutions seem a bit messy. The most general fix is probably adding the noapic parameter. Being quite a general fix it'll probably have some undesirable side effects. You might see a better solution come along if you watch the bug report.

---

### Post by philcolbourn on 2012-07-01
I have Mint 13 working on 15" MacBook Pro9,1.

See details [here]("http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html").

---

### Post by omegajune on 2012-07-02
I have Ubuntu 12.04 running on my new 13-inch MacBook Pro 9,2 as a dual boot setup. How well it runs, we have yet to see.

I had no luck trying to boot with a CD, so I used a USB drive.

Here's what I did:


[LIST=1]
[*]Created partition with the Mac OS disk utility as free space
[*]Installed rEFIt.
[*]I created a USB boot image using the directions here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) .  I used the amd64+mac file from this thread, but I'm not sure if that made a difference or not.
[*]Reboot to rEFIt and selected USB stick. I think it said something like "Legacy OS"
[*]When the purple screen comes up with the keyboard and man icons, I hit F6. This brings up a menu where I select the language. Then I press F6 again for other options and select "noapic" from the menu
[*]From there, I selected install ubuntu and let it run. I asked it to install ubuntu along side of MacOS and it automatically put it in the empty partition.
[*]After rebooting, when it gets to the GRUB screen, highlight the correct kernel and press "e" and on the kernel line, add "noapic" after "quiet splash." Then press F10 to continue to boot. Here's the thread to make this permanent: [http://ubuntuforums.org/showthread.php?t=1376547](http://ubuntuforums.org/showthread.php?t=1376547)
[/LIST]
Right now I have the system up an running for now. I'm still working on finding out if all the hardware works.

---

### Post by minsf on 2012-07-03
> **omegajune said:**
> I have Ubuntu 12.04 running on my new 13-inch MacBook Pro 9,2 as a dual boot setup.

note that the 13" MBP has no Nvidia card, so it may be a bit different than the 15" and 17" models (as in OP's situation). in that respect, it is probably more similar to my new MBA 5,2 (13", 2012). indeed, i followed almost the same steps as you describe. we probably do not need the nomodeset parameter (i think it is meant to fight something with the nvidia card). have you been able to get the keyboard lights to work? is your mouse/trackpad misbehaving after suspend? i was also able to boot with nointremap parameter instead of the noapic - i have not noticed a difference between the two boots yet.

---

### Post by Anon7-2521 on 2012-07-05
Basically the problem is with the DVD drive. For some reason, GRUB can't read directly from the drive. I had the same problem installing on my MBP 8,1. The way to solve it is like this: dd the .img onto a USB drive, and burn the same image onto a DVD/CD. Place the DVD/CD into the drive, and plug in the USB drive. Hit C or alt on boot, and select the disc. Once it realizes it can't read the disc, it'll read from the USB drive.

---

### Post by sodaa on 2012-07-18
> **omegajune said:**
> I have Ubuntu 12.04 running on my new 13-inch MacBook Pro 9,2 as a dual boot setup. How well it runs, we have yet to see.

I had no luck trying to boot with a CD, so I used a USB drive.

Here's what I did:


[LIST=1]
[*]Created partition with the Mac OS disk utility as free space
[*]Installed rEFIt.
[*]I created a USB boot image using the directions here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) .  I used the amd64+mac file from this thread, but I'm not sure if that made a difference or not.
[*]Reboot to rEFIt and selected USB stick. I think it said something like "Legacy OS"
[*]When the purple screen comes up with the keyboard and man icons, I hit F6. This brings up a menu where I select the language. Then I press F6 again for other options and select "noapic" from the menu
[*]From there, I selected install ubuntu and let it run. I asked it to install ubuntu along side of MacOS and it automatically put it in the empty partition.
[*]After rebooting, when it gets to the GRUB screen, highlight the correct kernel and press "e" and on the kernel line, add "noapic" after "quiet splash." Then press F10 to continue to boot. Here's the thread to make this permanent: [http://ubuntuforums.org/showthread.php?t=1376547](http://ubuntuforums.org/showthread.php?t=1376547)
[/LIST]
Right now I have the system up an running for now. I'm still working on finding out if all the hardware works.

/salute This did the trick for me.

An additional note that might help someone: I'm not sure if this was a result of other factors; however, I made two two ubuntu boot usb sticks on two seperate usb's. The one that I erased and formatted in OS X as OS (journalled) worked and is what I used, and the other one was not recognised.

I erase/partitioned it in os x and then followed the above steps successfully.

---

