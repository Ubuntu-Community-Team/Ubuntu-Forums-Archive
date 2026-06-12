---
title: "Help please!  Error loading operating system"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by retrosteve on 2008-03-12
I know this problem appears frequently and I've looked over the other threads, but I'm stuck.

When I first tried to install Ubuntu, the CD refused to boot from the USB CD Rom drive, though the drive works otherwise.  I have no built-in CD drive, it died.

So I tried running the Ubuntu installer that came on the CD drive.  That asked whether I wanted to put the loader on my C: drive (40GB) or my Y: drive (240GB) .  I chose the C: drive.

It overwrote the C: drive and installed Ubuntu.  But it won't boot from it.  Error loading operating system.

I took out my second drive (the 240GB drive) and the dead SATA CD drive I don't use, just to be sure.
No change.

I've tried booting instead from the USB CD drive but that still doesn't work either.

In BIOS (all I can reach now) I've turned on boot messages, and I see:

Attempting Boot from USB Device
Attempting Boot from USB Device
Attempting Boot from Hard Drive
Error loading operating system

I ran a disk self-check on the hard drive.  It's ok.  I assume it just has no boot loader.  But how can I put one on it now?  And why didn't installing Ubuntu do it?

I suspect I'll be carrying this paperweight into the shop, but I hope someone can help out...

Many thanks,
Steve

---

### Post by glennric on 2008-03-12
So when you try to boot from the USB CDRom what happens exactly?  Do you get to the boot menu of the CD or do you not even get there?

---

### Post by retrosteve on 2008-03-12
> **glennric said:**
> So when you try to boot from the USB CDRom what happens exactly?  Do you get to the boot menu of the CD or do you not even get there?

It skips the device (first on boot list) and tries the hard drive next, then fails.

---

### Post by glennric on 2008-03-12
Do you have an option at boot time to select boot device after post?  Perhaps try that and select the usb drive and see if it is really not even attempting the drive automatically?

---

### Post by retrosteve on 2008-03-12
> **glennric said:**
> Do you have an option at boot time to select boot device after post?  Perhaps try that and select the usb drive and see if it is really not even attempting the drive automatically?

As I said, I turned on boot messages and can see that it IS in fact attempting the USB CD drive.  

I also note that it tried and failed to boot from the USB CD drive even before I installed Ubuntu.  

I have also checked the ISO image with MD5 checksum, downloaded from ubuntu.com.  Yes it's ok.

Here's where it gets interesting.   I tried booting my other PC (the one I'm posting from) with the GG CD instead.  It too refuses to boot from it, even though the MD5 checked out.  In that case I get the same symptom -- it simply skips over the CD drive and goes straight to the hard drive, even when the boot order is changed.

---

### Post by glennric on 2008-03-12
When you burned the CD did you do so at a very slow speed?  This is recommended to avoid problems when the CD is created.  md5 sums do not tell whether or not the CD is corrupt, they only verify the iso image.  If you can't even get to the boot menu on the CD on two different computers, I would say that the image didn't get burned onto the CD properly.  Try to burn it again at the slowest possible speed.

---

### Post by retrosteve on 2008-03-12
> **glennric said:**
> When you burned the CD did you do so at a very slow speed?  This is recommended to avoid problems when the CD is created.  md5 sums do not tell whether or not the CD is corrupt, they only verify the iso image.  If you can't even get to the boot menu on the CD on two different computers, I would say that the image didn't get burned onto the CD properly.  Try to burn it again at the slowest possible speed.

I've burned another one.  Burned on a different computer, using a different burning program, with verification by sector afterward.   At 2.4x speed.

There's no change in the problem though.  I still can't get to the boot menu and that computer is a paperweight.

---

### Post by glennric on 2008-03-12
Does the new CD work on the other computer this time?

---

### Post by Chris555 on 2008-03-12
why don't you just re run the installer you used the first time?

---

### Post by retrosteve on 2008-03-12
> **Chris555 said:**
> why don't you just re run the installer you used the first time?

First, to answer the other question -- the CDs are both okay -- I can boot from either one of them from the Toshiba laptop, now that I've figured out how to fix the boot order on the Toshiba.

So it's not the media.

As for why not re-running the installer, that was run from Windows reading the CD Drive.  Now that Windows is no longer on the main hard drive, that's not an option.

Again my boot messages are

Attempting Boot from USB Device
Attempting Boot from USB Device
Attempting Boot from Hard Drive
Error loading operating system

So I don't get into Windows OR Ubuntu, not even the installers.

I just called the Geek Squad and that company promised to come over and fix my problem for just 100 pounds (200 dollars.)   Of course I could buy a new machine for that.

I'm hoping to do it cheaper...

(help)

---

### Post by Chris555 on 2008-03-12
I know you have been into bios, but in one of the forums there was a similar problem a few weeks ago. If there is an entry for usb legacy devices, check to make sure that is enabled. I know my bios has multiple usb enabling options. It would seem that your machine is not using that usb cd rom as a bootable device.

---

### Post by xravexheavenx on 2008-03-12
> **retrosteve said:**
> 
I just called the Geek Squad and that company promised to come over and fix my problem for just 100 pounds (200 dollars.)   Of course I could buy a new machine for that.

I'm hoping to do it cheaper...

(help)

Personally, I say don't call geek squad.  I don't know about in your area but in mine, both them and Circuit City's Firedog will not help at all.  They will just come, look at your computer, and say they don't know what's going on and leave or give you some reason to buy something else from them.  If you need to, take it to a local computer shop.  They typically know a bit more.  Personally, I take trips into Best Buys and Circuit Citys on a daily basis to ask them questions that they have no idea what the answers are.

---

### Post by retrosteve on 2008-03-12
> **Chris555 said:**
> I know you have been into bios, but in one of the forums there was a similar problem a few weeks ago. If there is an entry for usb legacy devices, check to make sure that is enabled. I know my bios has multiple usb enabling options. It would seem that your machine is not using that usb cd rom as a bootable device.

I tend to agree, but there's nothing I can find in the BIOS that would indicate this.  
Device Configuration finds the hard disk and the USB CD-Rom ok
Storage Options shows Removable Media Boot is Enabled.
Device Security shows all devices available
Data Execution Prevention (whatever that is) is disabled
All IRQs seem ok and usable.

nothing else in the BIOS menus looks likely to affect booting from USB device

I need an advanced geek!

---

### Post by glennric on 2008-03-12
It is also possible that the format that the cd burner you used is not readable by the usb cdrom drive.  Do you have another bootable cd that was burned by a different burner that you could test, just to see if that drive will recognize anything?  It seems unlikely, but it is a possibility.

---

### Post by retrosteve on 2008-03-12
> **glennric said:**
> It is also possible that the format that the cd burner you used is not readable by the usb cdrom drive.  Do you have another bootable cd that was burned by a different burner that you could test, just to see if that drive will recognize anything?  It seems unlikely, but it is a possibility.

I have two copies of the Gutsy Gibbon CD.  Both boot on the Toshiba (alternate).

One was burned on the Toshiba.  The other was burned on the same USB CD drive that now refuses to boot from it.

Hmmm.

---

### Post by Chris555 on 2008-03-12
can you plug the usb cdrom into the Toshiba and see if it will boot the cd on that computer? That should tell you if it is a bios problem, or if it something with the controller in the usb box

---

### Post by retrosteve on 2008-03-12
> **Chris555 said:**
> can you plug the usb cdrom into the Toshiba and see if it will boot the cd on that computer? That should tell you if it is a bios problem, or if it something with the controller in the usb box

Ok, tried that.  THe Toshiba cannot boot from the USB CD, though it can boot from its own.  The sad HP desktop also cannot boot from the USB CD, though it happily burns DVDs with it.  

In desperation I tried having the HP boot from its previous mostly-dead SATA CD-ROM, and sure enough, it managed, with lots of coughing and whirring, to throw up the Ubuntu preboot screen.  But that was as far as it went.  It hung.  Subsequent tries with that drive got nowhere.

So my conclusions are:

1.  From this experience and the several others on this site with similar subject lines, there's a serious problem installing the GRUB boot loader on the correct drive and the right part of that drive.  That's what stopped me in the first place, and it should be investigated.  It seems to happen most often with computers that have more than one hard drive.  Windows may suck in any number of ways, but it doesn't have trouble rebooting after initial installation, and that's a dealbreaker in my opinion.

2. My computer, now containing an unbootable ubuntu (say that five times fast) will not be fixable until I find another CD-ROM drive, preferably an IDE or SATA internal one, that works well.   Then I can boot ubuntu from CD (maybe) and then repair the GRUB.

3.  This was a very frustrating wasted day.

---

