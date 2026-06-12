---
title: "Install Feisty on external USB Drive???"
date: 2007-04-22
forum: Apple Intel Users
---

### Post by koni2005 on 2007-04-22
Has anyone managed to install Feisty onto an external USB drive? I was succesful - without the slightest problems - doing it out of the box with openSUSE 10.2 using rEFIt and GRUB. So it should be possible...

Does the GRUB bootloader in Feisty support booting from USB Drives?

Thanks...

---

### Post by H264 on 2007-04-22
I would like to hear what somebody has to say about this too, I almost bought a 4gig flash drive just for a ultra portable linux (Ubuntu) install.

---

### Post by lightbulb on 2007-04-23
Having just formatted the U3 junk from my USB flash drive, I too am on the search for a way of running the latest release of Ubuntu on a portable device.

I had a bit of a search around and found this:
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

there is an update to the article, intended for ubuntu 6.10, where the author has been informed that the tutorial works for 7.04 also.

I'll be giving this a try once I have the files downloaded. If anyone tries this, let us know of your progress :)

---

### Post by ronocdh on 2007-04-23
> **lightbulb said:**
> Having just formatted the U3 junk from my USB flash drive, I too am on the search for a way of running the latest release of Ubuntu on a portable device.

I had a bit of a search around and found this:
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

there is an update to the article, intended for ubuntu 6.10, where the author has been informed that the tutorial works for 7.04 also.

I'll be giving this a try once I have the files downloaded. If anyone tries this, let us know of your progress :)
How did you purge that U3 stuff, may I ask? I recently was annoyed by it on a friend's drive, and I thought a simple reformat (FAT32 I think I chose) would burn it out. Well, it didn't! So I assumed it was inside the firmware of the drive or something. Must kill....

---

### Post by NeoTaoistTechnoPagan on 2007-04-23
I have to admit I cheated - I had an extra HDD lying around and an older USB CDROM - tore out the CD drive and put in the HD. I attached it to a Windoze system that has VirtualPC on it and installed Kubuntu on the external HD.

Next step was connecting it to my Compaq Presario C304NR laptop. I was not expecting it to work, but everything works well. I had to use ndiswrapper for the wifi card (bcm45xxx) and I got the Intel 945G video card configured for 1280x800. Next step is getting Beryl working.


Hail the Holy Motherboard!

Polk Linux Users Group
mypc.is-a-geek.com

---

### Post by xGuse on 2007-04-24
> **NeoTaoistTechnoPagan said:**
> I have to admit I cheated - I had an extra HDD lying around and an older USB CDROM - tore out the CD drive and put in the HD. I attached it to a Windoze system that has VirtualPC on it and installed Kubuntu on the external HD.

Next step was connecting it to my Compaq Presario C304NR laptop. I was not expecting it to work, but everything works well. I had to use ndiswrapper for the wifi card (bcm45xxx) and I got the Intel 945G video card configured for 1280x800. Next step is getting Beryl working.


Hail the Holy Motherboard!

Polk Linux Users Group
mypc.is-a-geek.com


Where is the part that pertains to mac intel machines?

---

### Post by beefcurry on 2007-04-24
It has been done with dapper a long time ago, but it is far from complete. And it is quite hard, involves changing quite a few things. Check out [http://ubuntuforums.org/showthread.php?p=2516956#post2516956](http://ubuntuforums.org/showthread.php?p=2516956#post2516956)

---

### Post by slythfox on 2007-04-24
How annoying. I get "Could not find kernel image: vmlinuz" when I try to load it. :(

---

### Post by lightbulb on 2007-04-24
> **ronocdh said:**
> How did you purge that U3 stuff, may I ask? I recently was annoyed by it on a friend's drive, and I thought a simple reformat (FAT32 I think I chose) would burn it out. Well, it didn't! So I assumed it was inside the firmware of the drive or something. Must kill....

I have a SanDisk Cruzer flash drive so I popped over to SanDisk's site which mentioned being able to remove and restore the U3 feature:
[http://www.sandisk.com/Retail/Default.aspx?CatID=1450](http://www.sandisk.com/Retail/Default.aspx?CatID=1450)

The U3 Launchpad Removal Tool is what I used, worked nicely on my drive...REMEMBER TO BACKUP just incase, even though the uninstaller says it will restore your data after removal of U3! I had no data on the drive to test  this. :)
[http://www.sandisk.com/Retail/DriverDownloads.aspx](http://www.sandisk.com/Retail/DriverDownloads.aspx)

I've just finished the process of preparing the flash drive and I'm waiting for the iso files to copy over to the flash drive before I test it.

[UPDATE] It didnt't work and I'm not too clued up to know what is going on.

The Ubuntu boot menu offering boot from USB appears, I go ahead, and it fails to leave the black screen and load Ubuntu.
Instead I get a CLI:

```

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty: job control turned off

(initramfs)
303.575502 usb 3-6: device decriptor read /64 error-71
303.795317 usb 3-6: device decriptor read /64 error-71
304.127038 usb 3-6: device decriptor read /64 error-71
304.346853 usb 3-6: device decriptor read /64 error-71
304.970328 usb 3-6 device not accepting address 13, error-17
305.489889 usb 3-6 device not accepting address 14, error-17

```

Once this process is complete the light on the flash drive goes out, meaning it got disconnected or turned off or went undetected.
Plugging it back in results in the flash drive light coming back on, showing the same errors but with a different number at the start of each line (the 303.575502 bit) and then once the errors have been listed, the drive light goes out.

Now, on my PC the front two USB drives are a bit funny, my scanner doesn't work through them and at one point during the flash drive prep process in ubuntu, the flash drive switched off so I had to plug it into one of the main USB ports on the back of the pc. Anyway, thinking this was the problem, I plugged the drive into a rear USB port, this time I get the following two lines:

```

457.764119 sdb: assuming drive cache: write through
456.766615 sdb: assuming drive cache: write through

```

Then the computer just sits there with a flashing underscore on an empty line below _
Pressing enter brings up the (initramfs) prompt.

No idea what to do from here, any ideas? :)

---

### Post by lightbulb on 2007-04-25
Incase anyone was wondering, using the method at pendrivelinux,com, I have managed to get Ubuntu running from my USB flash drive. 

I must have messed something up the first time, the second time around I made the first partition 800Mb rather than 750Mb as in the tutorial. Also I used one of the main USB ports on the rear of the PC throughout the process, including boot-up. 

Now begins my quest to learn more and customise it :)

[edit] Bah, just realised that effectively, I have an Ubuntu Live CD on a flash drive :/

---

### Post by xGuse on 2007-04-25
PLEASE you guys, this is in the APPLE forum!!!!  Please make sure that your replies pertain to the APPLE machines!!!

Unless everyone thinks i am being a prick but it seems pretty aggravating to me as a Mac user that the majority of these posts helps me VERY little.

Gus

---

### Post by NeoTaoistTechnoPagan on 2007-04-25
> **xGuse said:**
> PLEASE you guys, this is in the APPLE forum!!!!  Please make sure that your replies pertain to the APPLE machines!!!

Unless everyone thinks i am being a prick but it seems pretty aggravating to me as a Mac user that the majority of these posts helps me VERY little.

Gus

Sorry about that - the topic itself came up in a search and I did not notice that the forum was for "Apple Intel Users".

IMHO this could apply to both Mac, x86, or AMD64. It all depends on if your system can boot from USB to begin with.

My .03

---

### Post by beefcurry on 2007-04-26
I would think installing Ubuntu to USB is in quite high demand, its a shame Canonical dosn't see the importance of this >.<

---

### Post by ronocdh on 2007-04-26
> **beefcurry said:**
> I would think installing Ubuntu to USB is in quite high demand, its a shame Canonical dosn't see the importance of this >.<
Well there's not too much Canonical has to do about this; most modern computers have motherboards (and BIOS) which support booting into USB, so it works fine for most people. It's these tricksy Macs with their EFI that are making things difficult. I think we'll have a coherent answer sooner rather than later, but we'll see.

Keep eyes and ears open, and make sure to post back and indications of progress. =) We'll have a solution soon enough!

---

### Post by HuXu on 2007-04-27
> **lightbulb said:**
> Having just formatted the U3 junk from my USB flash drive, I too am on the search for a way of running the latest release of Ubuntu on a portable device.

I had a bit of a search around and found this:
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

there is an update to the article, intended for ubuntu 6.10, where the author has been informed that the tutorial works for 7.04 also.

I'll be giving this a try once I have the files downloaded. If anyone tries this, let us know of your progress :)

Ok so I have a USB Maxtor External Hard Drive (300 GB), will this tutorial work the same?

---

### Post by JA2 on 2007-04-29
> **lightbulb said:**
> Bah, just realised that effectively, I have an Ubuntu Live CD on a flash drive :/
That's correct, however in my case, I used the second partition I created (ext3) to store a copy of the home directory for the default 'ubuntu' user account. Once the OS has booted fully, I just remount the ext3 partition over /home, log back into the GUI and I'm good to go. :-)

---

### Post by mscman on 2007-04-30
> **ronocdh said:**
> Well there's not too much Canonical has to do about this; most modern computers have motherboards (and BIOS) which support booting into USB, so it works fine for most people. It's these tricksy Macs with their EFI that are making things difficult. I think we'll have a coherent answer sooner rather than later, but we'll see.

Keep eyes and ears open, and make sure to post back and indications of progress. =) We'll have a solution soon enough!

That's an interesting take on the problem, but EFI does support booting to USB, at least on the Intel machines. It is entirely possible (and amazingly easy) to install OS X to an external USB drive and boot to it. The older PPC machines only supported booting from firewire; now that has reversed itself.

This is the same issue that we have when trying to boot Windows from an external drive on an Apple machine. I haven't looked into this too much, but the problem with booting Windows is that it reloads the USB drivers during its boot sequence, leading to a catastrophic (yeah, a little dramatic, but you know...) lock-up.

The question I have is: when Ubuntu is loading USB drivers, does it power cycle the USB ports, or does it simply mount them?

---

### Post by alan_daniel on 2007-05-06
> **mscman said:**
> That's an interesting take on the problem, but EFI does support booting to USB, at least on the Intel machines. It is entirely possible (and amazingly easy) to install OS X to an external USB drive and boot to it. The older PPC machines only supported booting from firewire; now that has reversed itself.

This is the same issue that we have when trying to boot Windows from an external drive on an Apple machine. I haven't looked into this too much, but the problem with booting Windows is that it reloads the USB drivers during its boot sequence, leading to a catastrophic (yeah, a little dramatic, but you know...) lock-up.

The question I have is: when Ubuntu is loading USB drivers, does it power cycle the USB ports, or does it simply mount them?

Based on past experiences installing older versions of Ubuntu on an external USB hard drive, I would guess that it power cycles through the ports before mounting them to see if any are already in use. I say that because I've never had to change many things like that to get it to work.

---

