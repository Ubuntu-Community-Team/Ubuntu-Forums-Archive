---
title: "Installing without a DVD drive?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by evadwolrab on 2007-07-31
I'm in a bit of a catch 22.

I have Ubuntu running nicely on my desktop, but I also have a laptop (mainly for use in university).

I've just about found all of the replacement programs I'll need for my web/graphic design work and my Windows laptop has decided it can't connect to any networks. I saw this as a good opportunity to stick Ubuntu on my laptop and really make the jump.

Unfortunately my laptop doesn't have a disc drive, so I can't install from a disc. Is there any other way to get Ubuntu on my laptop? The options I can think of are:
[LIST=1]
[*]Getting my Bios to check USB slots first on boot and somehow getting Ubuntu to run from an external hard drive.
[*]Having a virtual drive in Windows mount the Ubuntu disc. But I don't think that will work since it's all inside Windows and it would be overwriting itself... sort of.
[/LIST]

Am I missing a really obvious option? I don't own an external dvd drive but my friend owns one which I would be able to borrow in September. Will I just have to wait until then?

There have been other threads on this with no replies.

Any help greatly appreciated, as always.

---

### Post by ugm6hr on 2007-07-31
> **evadwolrab said:**
> [LIST=1]
[*]Getting my Bios to check USB slots first on boot and somehow getting Ubuntu to run from an external hard drive.
[*]Having a virtual drive in Windows mount the Ubuntu disc. But I don't think that will work since it's all inside Windows and it would be overwriting itself... sort of.
[/LIST]


I would go with Option 1: [http://ubuntuforums.org/showpost.php?p=3065206&postcount=5](http://ubuntuforums.org/showpost.php?p=3065206&postcount=5)
Sorry - not sure if this is exactly what you meant.  This option will allow you to put the LiveCD onto a USB stick and install onto the internal HD.

But I think Wubi does something like Option 2 (but I've never tried it).

---

### Post by evadwolrab on 2007-08-01
Tried running syslinux, no joy. I select 'usb storage device' from my boot options and it instantly says 'Error loading OS', as if it hasn't even really looked for it.

Before that I tried InstLux (net version) and, after it had spent hours downloading and installing ubuntu, it froze. Now of course Windows has been wiped so I can't use my laptop full stop now.

Does anyone have any other ideas? I now have a very expensive brick sitting in my room until September otherwise. :mad:

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> Tried running syslinux, no joy. I select 'usb storage device' from my boot options and it instantly says 'Error loading OS', as if it hasn't even really looked for it.


You followed instructions as described?  Bizarre... it worked OK for me.  

Maybe it's the newest version of syslinux - try the one I used: [http://www.kernel.org/pub/linux/utils/boot/syslinux/Old/syslinux-3.36.tar.gz](http://www.kernel.org/pub/linux/utils/boot/syslinux/Old/syslinux-3.36.tar.gz)

Presumably you still have a computer with XP to try copying syslinux again?

The original instructions again: [http://ubuntuforums.org/showpost.php?p=2754849](http://ubuntuforums.org/showpost.php?p=2754849)

---

### Post by evadwolrab on 2007-08-01
Yeah my desktop's still working. Dual-boot with XP and Fesity. Two things:

When I ran "syslinux f:", it just jumped to a new line. There were no errors, but then again there were no "complete" messages or anything.

Also, dyou think it matters if there are things other than the ubuntu iso contents on my USB drive? I'm using my 320 external hdd since I don't have anything else. It has music files etc which I don't want to delete.

---

### Post by Steveway on 2007-08-01
Well how about renting an external CD-drive?
Or maybe there is something like Instalinux wich creates Floppys? [www.instalinux.com](www.instalinux.com)

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> When I ran "syslinux f:", it just jumped to a new line. There were no errors, but then again there were no "complete" messages or anything.

Also, dyou think it matters if there are things other than the ubuntu iso contents on my USB drive? I'm using my 320 external hdd since I don't have anything else. It has music files etc which I don't want to delete.

From memory - I don't think it gives a "success" message.  I might give it a try later myself just to check...

Other thing - did you **extract** the Ubuntu .iso (and not just copy the .iso to the USB-drive), and then move and rename syslinux.cfg?

Doesn't matter if there are other files on the USB-drive - just make sure they are all inside another folder (i.e. not in the main directory).

---

### Post by evadwolrab on 2007-08-01
> **ugm6hr said:**
> From memory - I don't think it gives a "success" message.  I might give it a try later myself just to check...

Other thing - did you **extract** the Ubuntu .iso (and not just copy the .iso to the USB-drive), and then move and rename syslinux.cfg?

Doesn't matter if there are other files on the USB-drive - just make sure they are all inside another folder (i.e. not in the main directory).
Well I mounted in Daemon Tools and copied the contents of the "disc" on to the USB drive.

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> Well I mounted in Daemon Tools and copied the contents of the "disc" on to the USB drive.

Hmmm.... sounds like you've done the right things....

:-k

Maybe try the older syslinux (that worked for me) first.

Can't see why a USB-HD and a USB-flash should be any different, but....  :-k

Do you have any 16MB+ USB-flash sticks?

If so - you could try doing the same procedure for a minimal install iso, then add the rest via apt-get (copied from your desktop).
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by evadwolrab on 2007-08-01
I've managed to find a 1gb stick so I'm copying the iso contents across now. I've also realised that I've been using the Ubuntu Studio distro. If this doesn't work I'll download a new Feisty iso.

---

### Post by evadwolrab on 2007-08-01
Hmm... different result. I now have a blank screen with just a flashing cursor at the top.

I assume the point of this exercise is to load the Ubuntu CD from BIOS, rather that going into Windoze? Otherwise I've been going about this totally the wrong way :confused:

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> Hmm... different result. I now have a blank screen with just a flashing cursor at the top.

I assume the point of this exercise is to load the Ubuntu CD from BIOS, rather that going into Windoze? Otherwise I've been going about this totally the wrong way :confused:

Yes - this achieves booting from the USB, just as if you were booting from a LiveCD (i.e. LiveUSB).  It just needs Windows to put syslinux on the USB.

Why it's not working.... dunno.  It should at the very least get as far as the first option screen - Start or Install / Safe Mode / etc.

Try the USB in your desktop - perhaps your laptop will not cope with Grub at all?

---

### Post by ugm6hr on 2007-08-01
Another thought... maybe your laptop can't cope with the LiveCD (and therefore a LiveUSB)?

Possible solution:
Try the minimal .iso I linked to earlier.  Or the Ubuntu Alternate CD.iso with syslinux / USB.

I'm really sorry if I'm leading you down the garden path with this... but I'm sure this should work!

---

### Post by evadwolrab on 2007-08-01
Yeah just tried with the minimal, going to start downloading the alternate now.

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> Yeah just tried with the minimal, going to start downloading the alternate now.

So the minimal didn't work?  If not - then I suspect the Alternate won't either...

I don't want to be patronising - but if you want to post a nautilus / Windows File Manager image of the USB with the files on, I'll see if I recognise that anything is missing.

---

### Post by evadwolrab on 2007-08-01
> **ugm6hr said:**
> So the minimal didn't work?  If not - then I suspect the Alternate won't either...

I don't want to be patronising - but if you want to post a nautilus / Windows File Manager image of the USB with the files on, I'll see if I recognise that anything is missing.
Well now Ubuntu won't let me access USB devices "don't have privilege". So I'm going to burn the Ubuntu Studio dvd and reformat the linux partition on my desktop. Sigh... I can see this one being a saga... :popcorn:

I'll post a screenshot once the disc has stopped burning/installing.

---

### Post by ugm6hr on 2007-08-01
> **evadwolrab said:**
> Well now Ubuntu won't let me access USB devices "don't have privilege". 


How has that happened?  You've not done anything to affect your Ubuntu desktop.  Did you try booting from the LiveUSB on the desktop?

PS: If you are going to reinstall Ubuntu - I would recommend reformatting the original partition - cos sometimes it misbehaves during the installation if it finds a pre-existing Ubuntu there.

---

### Post by evadwolrab on 2007-08-01
> **ugm6hr said:**
> How has that happened?  You've not done anything to affect your Ubuntu desktop.  Did you try booting from the LiveUSB on the desktop?

PS: If you are going to reinstall Ubuntu - I would recommend reformatting the original partition - cos sometimes it misbehaves during the installation if it finds a pre-existing Ubuntu there.
I think the USB thing is something seperate. Got Studio running on desktop now (I wanted to try it out anyway so figured the USBs not working was a good excuse)

Yeah I tried the USB in my desktop and the same thing happened. Just a blinking cursor and nothing else.

[ATTACH]39500[/ATTACH]

---

### Post by ugm6hr on 2007-08-01
Screenshot seems to suggest everything should work....

I'm afraid I'm baffled.

---

### Post by ugm6hr on 2007-08-02
Still not sure why that didn't work, but I found a couple of other links that might be worth reading through for an answer:
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick?](https://help.ubuntu.com/community/Installation/FromUSBStick?)

The first one seems to give a dead easy solution - all the required files are provided for you.

---

