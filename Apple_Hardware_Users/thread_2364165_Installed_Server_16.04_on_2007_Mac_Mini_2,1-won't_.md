---
title: "Installed Server 16.04 on 2007 Mac Mini 2,1-won't boot if display not connected, fix?"
date: 2017-06-19
forum: Apple Hardware Users
---

### Post by Mythological on 2017-06-19
We installed Ubuntu Server 16.04 on a Mac Mini today that had previously only had OS X on it.   The install went fine and it runs great but the only problem is that it simply will not boot unless a display is connected, and we wanted to run it headless.  The resistor trick on the video output doesn't seem to work on this one, though it does on a different Mac Mini of the same model that's running 14.04.  I can take the display port adapter with the resistor that works perfectly on the other one and bring it to this one and it still won't boot, I even tried three resistors as some have suggested.

When it boots with a display connected it stays on a white screen for what seems like about half a minute, the the Ubuntu boot process starts, but it changes the resolution of the display a few times before settling down on 1920x1080.  But it will boot with the display connected.  With no display or with the resistor trick, no luck at all.  I really can't use the system for the purpose I had in mind if I have to leave a monitor connected all the time.  Has anyone else experienced this and found a way around it?

---

### Post by kevin160 on 2017-06-20
> **Mythological said:**
> When it boots with a display connected it stays on a white screen for what seems like about half a minute, the the Ubuntu boot process starts, but it changes the resolution of the display a few times before settling down on 1920x1080.  But it will boot with the display connected.  With no display or with the resistor trick, no luck at all.  I really can't use the system for the purpose I had in mind if I have to leave a monitor connected all the time.  Has anyone else experienced this and found a way around it?

My mini is a 6,2, so my issues can't definitely be related, but it is definitely fussy about video and it doesn't like certain cables.  It boots headless with 17.4 no problem though. 

Are you using one of the commercial video dongles (fit-Headless etc), or are you just putting resistors into an adapter?  I've never used one so I don't know if it's all really the same thing.  

Have you tried resetting PRAM?  

Stuff that may or may not be related, but macs are pretty weird, so worth maybe looking at:  Are you installing in pure EFI mode or in Bootcamp/BIOS mode?  You mention quite a long wait to boot.  Is your boot manager properly "blessed"?

---

### Post by Mythological on 2017-06-20
Not a commercial dongle, just the resistor in an adapter trick shown on several sites, which works great on my other Mac Mini.

Resetting PRAM had no effect.

I have no idea what you mean by this:  Is your boot manager properly "blessed"?  EDIT:  I found a page explaining this, and blessed the partition, and now it spends almost no time on the blank white screen compared to how long it used to linger there, but it still won't boot if no display is connected.

The way I installed Ubuntu server was to burn image to a CD after using the program at [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16) to make it bootable, stick the CD in the slot, and restart the machine and boot from the CD.  Then it just did a straight install of Ubuntu 16.04.

The crazy part is that if I connect a very ancient flat screen monitor to the adapter output rather than a resistor, it works even though the monitor hasn't been connected to power in MANY months.  So apparently having some form of electronics connected to that port is enough to make it boot, but one or even three resistors between one or all three of the RGB outputs and signal ground isn't sufficient now.  And we don't know if that's because something changed in Ubuntu 16.04, or if the hardware in the Mac Minis are slightly different, or what.  That's why I wondered if anyone else has experienced this.

---

### Post by kevin160 on 2017-06-22
Some searching led me to [https://ubuntuforums.org/archive/index.php/t-272967.html](https://ubuntuforums.org/archive/index.php/t-272967.html) which suggests that enabling remote access in MacOS might set the nvram to allow headless boot.  You should be able to install MacOS on an external drive if you don't want it on the internal HD.  Try with and without the video dongle.  That thread also suggests that you must be in EFI mode, so...

> **Mythological said:**
> The way I installed Ubuntu server was to burn image to a CD after using the program at [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1298894/comments/16) to make it bootable, stick the CD in the slot, and restart the machine and boot from the CD.  Then it just did a straight install of Ubuntu 16.04.

This means you have installed in Bootcamp aka BIOS mode instead of EFI mode.  The install is easier but many have found that hardware behaves differently.  

Unfortunately, installing 64-bit ubuntu on 32-bit efi macs can be frustrating and and time consuming.  There's  [a forum thread]("https://ubuntuforums.org/showthread.php?t=2287767")  for 32-bit efi macs if you want to try.  As I mention in that thread, in order to boot with kernels after 4.4 on my macpro 1,1, I needed to add the "noefi" (turns off Windows Secure UEFI) option to my grub string.  This should not be necessary if you are using the 16.04 *server* install iso since that image still uses the 4.4 kernel.   I've found a [Super Grub 2]("http://www.supergrubdisk.org/super-grub2-disk/") usb stick to be quite helpful during install and for rescue because it can automagically scan and boot Linux kernels it finds.

---

### Post by Mythological on 2017-06-23
Well try as I might I could not get this thing to boot with no display attached.  We ordered one of these just in case, and it arrived today and does the trick:

[1920x1200 DVI-D EDlD Emulator/ Dummy Plug, VR, Headless, Ghost (1 piece)]("https://www.amazon.com/1920x1200-DVI-D-Emulator-Dummy-Headless/dp/B01EISICO0/ref=sr_1_3?ie=UTF8&qid=1497927367&sr=8-3&keywords=DVI-D+EDID")

There are less expensive ones on eBay, but we wanted to be able to return it if it didn't solve the problem, so we bought it through Amazon.  Note that is NOT an Amazon affiliate link; I'm not shilling for those things, just wanted to let anyone that finds this thread in a search know that's a solution.  I would have liked to have found a free solution, but it apparently was not to be in this case.  I still cannot understand why the resistor trick worked on my other Mac Mini and not on this one, unless something has changed in the way 16.04 detects the display or something.

---

### Post by Mythological on 2017-06-23
> **kevin160 said:**
> Some searching led me to [https://ubuntuforums.org/archive/index.php/t-272967.html](https://ubuntuforums.org/archive/index.php/t-272967.html) which suggests that enabling remote access in MacOS might set the nvram to allow headless boot.  You should be able to install MacOS on an external drive if you don't want it on the internal HD.  Try with and without the video dongle.  That thread also suggests that you must be in EFI mode, so...



This means you have installed in Bootcamp aka BIOS mode instead of EFI mode.  The install is easier but many have found that hardware behaves differently.  

Unfortunately, installing 64-bit ubuntu on 32-bit efi macs can be frustrating and and time consuming.  There's  [a forum thread]("https://ubuntuforums.org/showthread.php?t=2287767")  for 32-bit efi macs if you want to try.  As I mention in that thread, in order to boot with kernels after 4.4 on my macpro 1,1, I needed to add the "noefi" (turns off Windows Secure UEFI) option to my grub string.  This should not be necessary if you are using the 16.04 *server* install iso since that image still uses the 4.4 kernel.   I've found a [Super Grub 2]("http://www.supergrubdisk.org/super-grub2-disk/") usb stick to be quite helpful during install and for rescue because it can automagically scan and boot Linux kernels it finds.

Thanks for trying to help!  Unfortunately I don't really understand the internals of Linux OR OS X to fully understand what you are saying here, but I will note that my other Mac Mini is running a 64 bit version of Ubuntu Server 14.04 with no issues using the resistor trick.  And I am running 16.04 server on this new (new to us, that is) machine.  I have never used "Super Grub 2", looks interesting but in this application I need to be able to reboot the system remotely and have it just come up, without having anyone present to select anything from a menu.  Also you'd need a monitor connected to see what you're picking, which kind of defeats the purpose.

I am only willing to bat my head against the complexities of Linux for so long before I give up and take the easy way out, which would have meant giving up on the Mac Mini and using other hardware if it had come to that.  Fortunately the emulator plug solves the problem.

Also, in case anyone else is reading this thread, don't forget to install macfanctld (it's in the Ubuntu repository, so just do **sudo apt install macfanctld**) or your Mac Mini will run HOT.  You can use the defaults or read the man page to see how to configure it.

---

