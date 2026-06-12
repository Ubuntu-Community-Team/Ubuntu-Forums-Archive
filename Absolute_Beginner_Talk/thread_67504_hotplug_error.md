---
title: "hotplug error"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by arnath on 2005-09-20
I'm new to Linux and a friend suggested trying out Ubuntu. I repartitioned my hard drive and installed it fine and everything. However, when I try to boot into Ubuntu now, it gets to the line

* Starting hotplub subsystem

and then hangs. At first I thought it was just taking a long time, but I had to go and left my computer on that screen for a full 3 hours. When I came back it was still sitting there. How do I fix this?

---

### Post by mlomker on 2005-09-20
Have you tried unplugging all of your unecessary USB devices?  This seems to be a common problem...there are a lot of threads on this.

---

### Post by Mnemonicman on 2005-09-23
I am also having the same problem. I tried removing any usb devices but it would still lockup on "Starting hotplug subsystem".

---

### Post by mlomker on 2005-09-23
[QUOTE=Mnemonicman]I am also having the same problem. I tried removing any usb devices but it would still lockup on "Starting hotplug subsystem".[/QUOTE]

Try disabling USB in your BIOS once.  It might not be hanging at USB...perhaps it's the next step that it's never getting to, I'm not sure.

---

### Post by Dain Bramaged on 2005-09-23
Hi All

Problems ! Just downloaded and tried to install this : ubuntu-5.10-preview-install-i386

All went well till it asked me to remove cd and reboot.

ubuntu with black back ground 


Starting Raid devices  etc etc etc then Starting Hot Plug Systems HANG !!

Google . Join , Read post 

Removed USB mouse find old grubby PS2 mouse

Disable all USB in BIOS didnt help either

Dual booting with XP SPK 2  P4 

Any more thoughts on what could be wrong  

Laterz T

---

### Post by Dain Bramaged on 2005-09-24
Come On guys I NEED HELP HERE !


Never mind, just typical of anything that comes out of South Africa .

/me nukes ubuntu.... and grabs something that works ..

---

### Post by mlomker on 2005-09-24
> /me nukes ubuntu.... and grabs something that works ..

5.10 is still a beta.  You'd be better off trying Hoary, but this hotplug hang is very common and trying another distro is a good solution.  I would.  I run Ubuntu because it runs best on my laptop...Gentoo wouldn't boot and Linspire couldn't network.

---

### Post by Mnemonicman on 2005-09-24
Even if 5.10 is a beta I still get the same problem with 5.04. But I tried it on my laptop and it did work then. So maybe it's not the usb. I disabled all usb on my NF4-Ultra-D and still it would lockup at "starting hotplug subsystem".

---

### Post by mlomker on 2005-09-24
[QUOTE=Mnemonicman]Even if 5.10 is a beta I still get the same problem with 5.04. But I tried it on my laptop and it did work then. So maybe it's not the usb. I disabled all usb on my NF4-Ultra-D and still it would lockup at "starting hotplug subsystem".[/QUOTE]

Hotplug autodetects/loads the modules for everything in your box.  It could be any one module that is causing the hang.

You could boot a liveCD (knoppix or whatever) and **chmod 600 /etc/init.d/hotplug** or remove the links from /etc/rcS.d and /etc/rc2.d for hotplug but then you'll have to figure out what modules to load and load them all by hand in /etc/modules.  That'd be a pain.

I had another guy tell me that his problem was caused by a TV card in his box.  Have any add-on cards in the box that you could pull as a test?

---

### Post by Mnemonicman on 2005-09-24
Probably not.
Here's the specs of my pc
Athlon64 3000+ venice
2GB DDR400
DFI NF4-Ultra-D
Powercolor X800XL
Audigy2
250GB Sata + 40GB Pata
DVD Writer

That's all I got. The only things I could pull out would be the 40GB HD and the Audigy.

---

### Post by TristanMike on 2005-09-24
[QUOTE=Dain Bramaged]Never mind, just typical of anything that comes out of South Africa .[/QUOTE]I don't think this is very constructive.

---

### Post by mlomker on 2005-09-24
> That's all I got. The only things I could pull out would be the 40GB HD and the Audigy.

I'd unplug them as a test.  It should only take a couple minutes to do.  I assume you're already running the latest system BIOS?

---

### Post by Mnemonicman on 2005-09-24
Of course. 

It's something I'll have to do tomorrow. Hopefully then it will work. Besides the 40GB is probably near to failure. It had been complaining of possible failure in the past. It'd be nice to replace xp with something else. Perhaps it might help to set it back to stock settings. I may have tried it that way the last time I used the live cd but I'm not sure. Probably would help anyways.

---

### Post by Mnemonicman on 2005-09-25
Ok so it was the soundcard that was causing the lockup. Now the next problem is the video. For whatever reason it complains about something to do with xorg. There may be a setting that needs to be changed.

---

### Post by mcruser on 2005-09-30
Hi -

I've been having a similar problem. I'm installing my first Linux onto a B&W G3 PowerPC onto a new HD. Release 5.04. Originally, I tried saving some Mac partitions, but this never worked, and after a week waiting for a post-back over here, I just trashed the Mac partitions. Now it runs through the first CD-based installation phase, then hangs when rebooting with "Starting hotplug subsystem..."

Via Google and this forum, I've tried a few things:
 - reboot with "linux=noprobe" just results in this response -
   Please wait, loading kernel...
   /pci@80000000/pci-bridge@d/pci-ata@1//@0/disk@0:3,\\linux=no probe no such file or directory
 - reboot with ctrl-C or apple-C - no effect.
 - disconnected USB and Firewire devices (except mouse & keyboard): no effect.
 - reinstall with repartition: no effect.

This system is a G3 that is same as from factory except original hard drive was disconnected and replaced with new large one, and addition of RAM a month ago, now at 384MB. It came with factory SCSI, but no devices in use.

I heard that Ubuntu support forums are quite helpful, and I've seen some tips to other posters, but my original post yielded nothing (except a kind moderator who tried moving it to a different forum). Anyone out there got some ideas?

Thanks for any tips!

- Marc

---

### Post by WolfJay_83 on 2005-10-26
Can someone explain exactly how to disable hotplug on boot and then load each module one at a time from the terminal?  This would allow us to figure out exactly what  device is causing this lock, so it can be blacklisted.

---

