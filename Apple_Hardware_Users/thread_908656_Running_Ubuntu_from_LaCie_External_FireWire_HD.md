---
title: "Running Ubuntu from LaCie External FireWire HD"
date: 2008-09-02
forum: Apple Hardware Users
---

### Post by mac-wilson on 2008-09-02
Hey guys, so Ubuntu installed.  I restarted the computer, held option key down on boot.  Ubuntu wasn't there.  I need something that lets me boot into Ubuntu.

Anyway I logged into Mac OS X.  My LaCie HD was already on, and when the desktop loaded an error happened:
[IMG]http://i36.tinypic.com/jv6b9f.jpg[/IMG]

I clicked Initialize...

The disk1s1 is grey, and I looked at the LaCie disk, etc:
[IMG]http://i33.tinypic.com/34ngkzk.png[/IMG]
[IMG]http://i36.tinypic.com/2cysdjb.png[/IMG]
[IMG]http://i34.tinypic.com/2w71og3.png[/IMG]

I don't know what to do, or how to do it.  I don't really feel comfortable working with this right now without help.

I need the 464.8 GB partition to back up my MacOS with Time Machine.  However, my External HD doesn't mount when I turn it on!

I downloaded and installed rEFIt to see if I could boot into Ubuntu (disk1s1).  However, when I restart it boots straight into Mac OS X.  I'm almost positive I installed it correctly.  I follow the Automatic Installation with Installer Package - [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html).

Any help would be greatly appreciated!

Thanks,
Wilson

---

### Post by cyberdork33 on 2008-09-03
Ok, running Ubuntu from an external drive will not work. See the FAQ. There is a LONG LONG thread in this.

You don't need to post a screenshot of everything, and if you do post a screenshot, you need to describe exactly what you are trying to show as I don't see anything wrong with what you are showing.

You probably should not have click Initialize. That probably messed something up. If you need the drive for Time Machine, and it is currently not working correctly, then I would just repartition / reformat the entire thing and start over. Make one partition a normal Mac partition (HFS+) and make a second 'unformatted' partition. You can then reformat that second partition to whatever you like.

If rEFIt is not showing up, then there was a problem with the install. You might need to use the manual install method.
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by mac-wilson on 2008-09-03
I figured everything out.  rEFIt now works.  I repartitioned my external drive.  its now backing up my MacOS.  I made 2 partitions.  One for MacOS backup and on for my future Linux install.  The Linux install partition is saved as Free Space. Supposedly Ubuntu will know what to do with a "Free Space" partition when you do Automatic install.  If it works I'll come back with how i got it to work on an External Drive :guitar:.

---

### Post by cyberdork33 on 2008-09-03
> **mac-wilson said:**
> I figured everything out.  rEFIt now works.  I repartitioned my external drive.  its now backing up my MacOS.  I made 2 partitions.  One for MacOS backup and on for my future Linux install.  The Linux install partition is saved as Free Space. Supposedly Ubuntu will know what to do with a "Free Space" partition when you do Automatic install.  If it works I'll come back with how i got it to work on an External Drive :guitar:.yes, during the install choose to install to the "largest free space".

---

### Post by Dj TweeX on 2008-09-04
You can in fact run Ubuntu, Fedora, & almost any Linux distro from an external. i loaded my Ubuntu onto my LaCie 300 gb & take it to & from school & boot it up constantly in different places

---

### Post by cyberdork33 on 2008-09-04
> **Dj TweeX said:**
> You can in fact run Ubuntu, Fedora, & almost any Linux distro from an external. i loaded my Ubuntu onto my LaCie 300 gb & take it to & from school & boot it up constantly in different places
And you do this on an intel mac?

---

### Post by jflaker on 2008-09-04
installing to USB hard disk works as I had it on a 30GB USB drive and dual boot, before I decided to go 100% into Ubuntu

---

### Post by cyberdork33 on 2008-09-04
> **jflaker said:**
> installing to USB hard disk works as I had it on a 30GB USB drive and dual boot, before I decided to go 100% into Ubuntu
Please understand that the boot from USB disk problem is a limitation of the Mac. You are in an Apple Users forum.

---

### Post by Dj TweeX on 2008-09-05
> **cyberdork33 said:**
> And you do this on an intel mac?

I Do it on an Intel Dell, Intel HP, Intel eMachines.
you just have to set up the Bios to boot from usb.
although some older motherboards do not support this feature.
but yes. i will even attempt to boot it on my teachers iMac to confirm this.

---

### Post by Dj TweeX on 2008-09-05
> **cyberdork33 said:**
> Please understand that the boot from USB disk problem is a limitation of the Mac. You are in an Apple Users forum.

Apologies.
but i will try hard to remedy this situation.

---

### Post by Dj TweeX on 2008-09-05
> **jflaker said:**
> installing to USB hard disk works as I had it on a 30GB USB drive and dual boot, before I decided to go 100% into Ubuntu

Wait. they make ones that small still??
or was it an ipod lol. Cause i kno you can partition an ipod to boot usb into ubuntu on a pc. but again with the boot problem

---

### Post by jflaker on 2008-09-05
> **Dj TweeX said:**
> Wait. they make ones that small still??
or was it an ipod lol. Cause i kno you can partition an ipod to boot usb into ubuntu on a pc. but again with the boot problem

They don't make them that small anymore, but when you have a spare USB to IDE enclosure and a laptop computer that is being thrown away, I took the opportunity to remove the drive and have a FREE portable storage unit...

---

### Post by jflaker on 2008-09-05
> **cyberdork33 said:**
> Please understand that the boot from USB disk problem is a limitation of the Mac. You are in an Apple Users forum.

I understand and noted.

---

### Post by mac-wilson on 2008-09-07
Do you guys know if it works on a **FireWire** External HD?  How did you guys get it to work for USB?

---

### Post by hajk on 2008-09-07
> **mac-wilson said:**
> Do you guys know if it works on a **FireWire** External HD?  How did you guys get it to work for USB?No "legacy" OS (like Windows or GNU/Linux) can boot a Mac-Intel computer from an external HD, whether USB or FireWire. That's just the way Apple have implemented the EFI replacement for BIOS. 

Note that this restriction does not apply to Mac OS X. Also, a legacy OS (once booted) can use any partitions on an external or internal drive. 

So, how then can GNU/Linux boot a Mac-Intel machine? The boot partition (the /boot directory, really) must be one of the internal HD partitions numbered 1 - 4 ("primary"), or the /boot directory must be on a bootable CD or DVD in the internal drive.

---

