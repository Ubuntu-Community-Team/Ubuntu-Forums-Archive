---
title: "How to install Ubunto onto a PC with no CD drive"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by kejaba on 2007-03-01
Hi all..

At home I have a Laptop - an old Toshiba Satellite A10 Pro.  The CD drive does not work and it has Windows XP on it which will not boot.

I'd like to install Ubuntu on it.  However, I can't find a way to do it without using a CD.  I've searched Google and these forums, and probably I am searching on the wrong terms as I can't find anything.  All I can find is how to get a PC to boot from a CD.  But, like I say, I can't do this as the CD drive is defective.

If anyone could provide a link to an article talking about how to do this for ubuntu, that would be peachy.

Thanks.
PS.  I should also say I know very little about linux / PCs etc.

---

### Post by kejaba on 2007-03-01
oops.  about fifth link in google describes this
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
sorry!

---

### Post by desheikh on 2007-03-01
I guess the easiest solution would be to take the hdd out, put it in an external casing, connect to a pc with a cdrom, and install from there

Note since there will be multiple hard drives youll need to make sure the grub bootloader is installed in your laptops hdd and not one of the others. I believe a button appears in that case at the ready to install page [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) [scroll way down])

Just did a google search and apparently there are quite a number of ways to achieve what your aiming for (searched for "ubuntu install without cd") some require you to have windows working but this one seems like it might work for you though

[http://blog.bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle](http://blog.bergcube.net/post/2007/01/08/Ubuntu-laptop-struggle)


Ali

---

### Post by webofunni on 2007-03-01
Yes get your harddisk unpluged and get installed from another system is a solution

---

### Post by NCStone on 2007-03-01
Carefull with this last idea.

I have just completed this type of setup and can not get the OS to boot.

See my post.

[http://www.ubuntuforums.org/showthread.php?p=2231960#post2231960]("http://www.ubuntuforums.org/showthread.php?p=2231960#post2231960")

---

### Post by Neobuntu on 2007-03-01
...many ways to skin a cat.

The fastest way is to put the laptop HD into another (hopefully fast) laptop and install it there. Then move it back and tweak it. You don't have the road blocks that you might encounter doing this with Windows.

If you're not comfortable removing and installiing a laptop hard drive, have some who can, do it.

The more similar the laptops the better, but they don't have to be exact.

It may be a fun exercise to think about floppy's, zips, USB, parallel or serial ports and drives that may work with them but it's just not worth the time. Trust me. I've done it. You don't want to.

Of course, you can get an adapter for laptop drive to desktops IDE but thats an extra step(s). You may also have to deal with various jumper(set to master), cable and position standards if you don't go laptop to laptop.

Remember to set your BIOS(s) to AUTO for the hard drives and let them recognize. Obviously, if you connect the temp notebooks hard drive back in the way it came (being static grounded) it should not be changed.

If you don't know, the reason is, you need native (from BIOS) booting without any other system yet installed. The CD is the easiest new drive to boot (and have Kubuntu Dapper 32bit on.) Use the alternate installer CD for 128MB to about 256MB RAM.) 64 to 128MB RAM use Puppy Linux instead. Less than 64MB and you are playing. You can get by (arguably) with 32MB but it's no fun. Up your memory to it's max. Use the fastest hard drive you can.

---

### Post by bodhi.zazen on 2007-03-01
You can install from the iso file without burning to or booting from a CD :

Install from .iso: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by Neobuntu on 2007-03-01
Perhaps you should look into cleaning or replacing the failed CDROM drive first. Maybe the laser is dusty (make sure it is OFF!) Be gentle. Hey it's broke now right. Give it a try(if you haven't).

---

### Post by Neobuntu on 2007-03-01
> **bodhi.zazen said:**
> You can install from the iso file without burning to or booting from a CD :

Install from .iso: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

True that too but where are you going to put the iso? Let the CD install do the partitioning instead. Better (fewer steps, less time) to boot it in a CD drive. Thus move it (if you can't fix your CD).

Trust me, the screw driver is faster.

---

### Post by bodhi.zazen on 2007-03-01
> **Neobuntu said:**
> True that too but where are you going to put the iso? Better (fewer steps, less time) to boot it in a CD drive. Thus move it (if you can't fix your CD).

Trust me, the screw driver is faster.

LOL, check it out. You partition the HD, install grub, and copy the iso to a new partition.

It is slick ;)

---

### Post by Neobuntu on 2007-03-01
Also given your:
Processor manufacturer:  	Intel
Processor model: 	Mobile Celeron
Clock speed: 	2 GHz
RAM installed: 	256 MB
Hard drive size: 	30 GB
Graphics processor: 	Intel Extreme Graphics 2
Graphics RAM: 	96 MB

The shared graphics RAM may tax your good 256MB if you run too much at once. Kubuntu may be a bit better for memory saving. Browsing with Konqueror and Kubuntu's KDE will reduce memory usage too, BTW. The "Extream Graphics" is known to work (direct 3D aka DRI even). Other than a somewhat slower notebook HD speed, you look good to go.

Get more memory if you haven't. Yes, your max is 1GB RAM.

You can do Gnome too but having one is faster for on-line upgrades. 

Remember, Kubuntu (and Dapper 6.06.1 LTS 32bit - Live CD OK I think).

Also, if you want WiFi, research the card first (good chipset known to work NATIVELY/AUTOMATICALLY with *ubuntu). $10 bucks or so.

---

### Post by Neobuntu on 2007-03-01
Given your model has USB with 2.0 (which is somewhat rare on older computers) it MAY/SHOULD boot from USB from the BIOS so given the extra steps to set up a flash drive, you might go that route(and you'll probably have to play with BIOS settings to boot - more time). It depends though. Where as, installing in another notebook doesn't depend(so much). 

You may be able to install and reinstall the hard drive before you can get a USB stick installed for booting.

I have decided (personally) USB drive booting isn't their strength(best use), but it might work for you.

Also, an iso file install is slick, cool and interesting but in the end you'll have an extra partition to deal with, that you have to make in the first place. The best way to do that may be to burn a Gparted live CD (That's nice to have but without CD a drive you'll need to make a floppy partitioner and boot disk)  a lot more work/time!

...been there. Screw it! Some laptops are really easy to get the hard drive in and out. Others just take more screws.

Hours upon hours, I have spent playing with "alternatives". The fastest has been pulling the drive, by far.

Can of worms vs. screw driver. :)

FYI

---

### Post by webofunni on 2007-03-02
Is your are connected to internet then try the online installation project at [https://wiki.ubuntu.com/install.exe]("https://wiki.ubuntu.com/install.exe")

---

