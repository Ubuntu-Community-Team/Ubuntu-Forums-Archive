---
title: "Xubuntu on iMac G3"
date: 2008-12-18
forum: Apple Hardware Users
---

### Post by Roxas-X2 on 2008-12-18
Hey, I'm new to both Linux and Macs so I'm looking for some help. I recently bought a slot loading iMac G3. Can't remember the specs off hand but as far as I know it has 256mb ram. Also the power light lights up white instead of green which I thought was a bit weird. 

Anyway, I'm wondering if it would be possible to do a fresh install of Xubuntu if I replace the hard drive, rom drive and ram or will I have to go through all the crap with updating the firmware? I just want to know if it would be worth it because if it doesn't work I don't really want to go forking out for fresh copies of OS9 and OSX Panther (which is what it's running at the moment). 

Any help would be much appreciated. Thanks :)

---

### Post by mkvnmtr on 2008-12-18
If there is any firmware update you should get that of the internet from Apple automatically. Then with 256MB of ram you should probably use the alt. disk to install. More ram will of course help. I can think of no reason to change anything else.

---

### Post by Roxas-X2 on 2008-12-19
Well I'm planning on maxing it out as soon as possible. I was just wondering if I would encouter any problems installing to a formatted hard drive

---

### Post by stream303 on 2008-12-19
Without any installation disks, I'd be tempted to run Carbon Copy Cloner on it to an external usb disk just in case for a backup.

I'm not exactly sure that you absolutely *need* to do a firmware update before loading Ubuntu (or any other Linux for that matter).  At any rate, you can only do so from a hard disk that is currently running the older Mac-os.

I guess you'll have to wait for any sort of definite answer.  I know quite a few early Macs out there got bricked by those trying to install OSX or using OSX utilities on them, when the installer would alter the video freqs in nvram, and then the older mac-os would not recognize the change without the firmware update, and shut off the monitor.

In Ubuntu's case, one has to go in and manually editi the xorg.conf file anyway, so this means that one HAS to use the "alternate" text-based installer, and possibly use a "rescue" mode, to edit the xorg.conf file before the screen shuts down until configured properly.

If you do decide to start upgrading the hardware, be sure to do a pmu/smu reset - anytime you change Apple hardware, this should be performed - not to be confused with resetting the pram - although that too is a good idea, but smu/pmu resets are nearly mandatory when adding/removing hardware.  If you do go in there, you may want to treat yourself to a new motherboard battery - typically a Tadiran I believe.

You may want to look at your specific model to get more familiar with it:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

To see what you might be getting into:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

Also note that if you install a hard drive larger than oem size on those early imacs, you'll need to manually partition your disk during install to keep the root / partition under 8gb, typically 7.5gb or so since you don't want to be right on the edge of the partition, or if manufacturer's don't report the way they calculate the exact size.

---

### Post by Roxas-X2 on 2008-12-19
I'll boot it up when I get the chance and list all the specs. It's an indigo iMac G3 at any rate. Another thing I was wondering is it possible for the G3 to take PC 133 ram or is it just PC 100 that is compatible?

---

