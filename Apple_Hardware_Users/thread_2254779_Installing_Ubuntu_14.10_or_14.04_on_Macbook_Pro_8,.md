---
title: "Installing Ubuntu 14.10 or 14.04 on Macbook Pro 8,2 w/ 2 internal SSDs"
date: 2014-11-29
forum: Apple Hardware Users
---

### Post by drew28 on 2014-11-29
Hello!

I've been trying to find guidance/help/instructions on how I can go about installing ubuntu on a secondary drive and leaving the main drive as is (running OS X yosemite).. and the only documentation I've found is for partitioning the main boot drive.

I've upgraded my hardware extensively since my macbook pro's release in early 2011 by swapping out the 750GB HDD for a 1TB SSD, replacing the optical drive with an additional 480GB SSD (SATA connection), and doubling the ram from 8GB to 16GB. However, the processor remains the original Intel Core i7 2630QM (quad-core 2.0gHz)..so I would like to think running ubuntu will be possible with a little configuring.

But I've only been able to find documentation for installing any linux on the macbook pro 8,2 revolving around partitioning and installing the linux distro on the same boot drive as os x :/

Any insight, help, or comments that could point me in the right direction would be appreciated greatly!!
..and I tried to make sure to describe all necessary hardware specs..but definitely ask away if more info is needed.

Thanks in advance,
Drew

---

### Post by este.el.paz on 2014-12-02
@drew:

Looked over this question yesterday, as I have no direct experience with multi HD installs, I waited . . . but, as no other takers have shown up . . . my suggestion is "Try it" . . . .  From OSX Disk Utility format the selected HD as "FAT" or as "Free space" . . . then boot the install disk and see if it shows the HD you want . . . it might show it as "sda" . . . and the key point will be the size of it . . . give or take . . . .  Then try to let the installer run "automatic, install into largest free space" . . . if it looks like that HD is not showing, you could try to use "manual" and then get to the GParted disk partition window and see if your drive shows up there . . . once you see the ID number "sda4" or whatever you could try the automatic again . . . otherwise, you would follow the other data about how to partition and install, etc.  The installer is "fairly smart" about its "Install alongside OSX" . . . but, like I said, I haven't done this yet, although there is such an idea in mind.  Probably a good idea to back up your OSX system **before*** playing around with it . . . and even try to boot the LiveDVD system and test it out before doing an install . . . .  These days I'm leaning more toward the "virtualbox" idea, an app to select and run OSs inside OSX rather than hassling the install process, or seems like you can make a USB bootable drive and boot from there . . . .  Read the Mactel FAQ sticky at the top of the sub-forum page . . . to get into the "issues" . . . like fan control and so forth . . . that come from running the apple unit in linux . . . .  Having said that, I'm typing this in LM17 MATE . . . in my MBPro . . . boys will be boys . . . not always "sensible" . . . .  I have rEFInd installed in the OSX system . . . some people seem to think it's not needed, but, after install, shut down the computer . . . on reboot hold "alt/option" key and the various OS choice disks should show up . . . use arrow keys to move and select your boot drive.

Enjoy the process . . . probably should be 14.04 LTS 64 bit for your first run at an install--don't be fraid to make a mistake, that's the whole point of it.

e.e.p.

---

