---
title: "Where to find eeexubuntu"
date: 2011-11-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bkline on 2011-11-10
The site which normally hosts the customized version of xubuntu for eee machines has been down for quite a few days.  Anyone know of an alternate site where the .iso might be available?

---

### Post by TenPlus1 on 2011-11-10
Why not just install Xubuntu and download this program:

[https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb](https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb)

This lets you use the features on Asus Eee Pc's

---

### Post by bkline on 2011-11-10
> **TenPlus1 said:**
> Why not just install Xubuntu and download this program:

[https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb](https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb)

This lets you use the features on Asus Eee Pc's

Thanks for the suggestion.  Does this package also include the optimizations to customize the window manager settings for the smaller screen, as well as the utility to create the bootable USB memory stick?

---

### Post by bkline on 2011-11-11
Does anyone know if eeeuser.com is gone forever?  Or is the server just down temporarily?

---

### Post by Digger109 on 2011-11-11
> **bkline said:**
> Does anyone know if eeeuser.com is gone forever? Or is the server just down temporarily?
 
 
I second that request.....I've been unable to find the eeepc forums for several days now.

---

### Post by bkline on 2011-11-12
> **TenPlus1 said:**
> Why not just install Xubuntu and download this program:

[https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb](https://launchpad.net/~eee-control/+archive/eee-control/+files/eee-control_0.9.7.0_all.deb)

This lets you use the features on Asus Eee Pc's

Since I didn't get answers to my questions, I went ahead and tried it myself to find out empirically.  I pulled down Xubuntu 11.10, used usb-creator-gtk to create a bootable 4GB USB memory stick, booted from it on my eee, downloaded and installed the eee-control package, and tried some web browsing to test the responsiveness of the installation.  The machine hung (wouldn't even boot into a text console).  So I installed the unetbootin package, and created another Xubuntu image on another USB stick using that utility.  Downloaded the eee-control package, and it wouldn't even install.  The error message said "/usr/sbin/grub-probe: error: cannot find a device for /".

Once again, has everyone connected with eeeuser.com really evaporated?  Does no one have a copy of the latest eeexubuntu?

---

### Post by snowpine on 2011-11-12
eeeXubuntu was never an "official" Buntu and is quite a dead & obsolete project as far as I know. 

Ubuntu and its variants (including Xubuntu) should have excellent support for the Asus EEE "out of the box" with no tweaks. If you need help running Xubuntu on your EEE, a good first step is to tell us which model number you have.

---

### Post by bkline on 2011-11-12
> **snowpine said:**
> eeeXubuntu was never an "official" Buntu and is quite a dead & obsolete project as far as I know. 

Ubuntu and its variants (including Xubuntu) should have excellent support for the Asus EEE "out of the box" with no tweaks. If you need help running Xubuntu on your EEE, a good first step is to tell us which model number you have.

This is an Eee PC 1000.  So far I've been booting from USB memory sticks for my tests.  At this point it may be useful to test Xubuntu by actually installing it on the system.  There are two disks in the machine.  The first is 8GB, divided roughly in half between /dev/sda1 (a Linux 3GB+ partition) and /dev/sda2 (a Linux 4GB+ partition) with two more tiny partitions (/dev/sda3 an 8MB W95 partition and /dev/sda4, 8MB EFI).  The other device is 32GB in a single partition on /dev/sdb1, given over to the user's home directory.  My plan is to back these up, using dd for the 8GB disk, and dump or tar for the larger user partition, in case the Xubuntu option doesn't work out, so I can restore back to Xandros.  Then I'll install Xubuntu on /dev/sdb1 in a single partition, leaving the partition tables intact (but modifying the /dev/sdb1 MBR to boot /dev/sdb1), and actually giving myself two paths back to restoration in case that turns out to be necessary: the first being the restore partition on /dev/sda, and the other being my dd backup of /dev/sda (I'd need my backup of /dev/sdb on either path).

Then I'll install the package with the eee utilities.

Does this seem like a reasonable approach?

---

### Post by snowpine on 2011-11-13
I have not used a 1000 model personally but I remember reading that one drive is faster than the other. You might want to research that and install Xubuntu on the faster of the two drives (using the slower drive for data/backup). It's an older model so hardware support should be excellent.

I think Xubuntu is a big step up from Xandros. If you are happy with your Live USB test drive then go for it!

---

### Post by bkline on 2011-11-13
> **snowpine said:**
> I have not used a 1000 model personally but I remember reading that one drive is faster than the other. You might want to research that and install Xubuntu on the faster of the two drives (using the slower drive for data/backup).

Good suggestion; it hadn't occurred to me that the two drives might have different performance characteristics.  Clearly writing to /dev/sda is faster (by an order of magnitude) than writing to /dev/sdb.  One thing I'll have to watch out for is running out of space for the OS if I leave the rescue partition intact, installing Xubuntu to /dev/sda2 (where Xandros lives right now).  I'm sure Asus was working with a more pared-down distro than I'll get from Xubuntu by default.  If /dev/sda2 is too tight I'll have to decide whether to go with /dev/sdb (accepting the slower performance) or merge /dev/sda1 and /dev/sda2 (keeping the better performance but losing one of my two restoration paths).

I'll report back on how things turn out; perhaps others might benefit from these experiments.

---

### Post by snowpine on 2011-11-13
From what I've heard about Xandros it is quite obsolete and not really worth saving... personally I would wipe the restore partition and commit fully to the new distro. :)

If you want a backup of the restore partition then I believe you can use a utility such as Clonezilla (or maybe even Gparted?) to copy it to another drive.

---

### Post by bkline on 2011-11-13
> **snowpine said:**
> From what I've heard about Xandros it is quite obsolete and not really worth saving... personally I would wipe the restore partition and commit fully to the new distro. :)

If you want a backup of the restore partition then I believe you can use a utility such as Clonezilla (or maybe even Gparted?) to copy it to another drive.

Well, I've got the entire drive cloned (twice) with dd, so I should be safe.  As for Xandros, I agree that it's not aging well (the update repository hasn't had anything new for years), but it does work, and if I run into an unexpected brick wall with Ubuntu it will be good to be able to roll back.

I did notice one other bizarre thing as I was preparing for the switch.  All of my descriptions of the disks so far have been based on what I see booted from the Xubuntu USB disk.  However, when I boot into the installed Xandros, both the live root partition as well as the rescue partition are listed by df and mount as /dev/sda1 (with different sizes!).  No idea what that could mean. :-)

---

### Post by bkline on 2011-11-13
Well, that was smooth and painless.  So far Xubuntu on my eee netbook has substantially exceeded my expectations.  Of course, this is very early in the process, but I'm afraid anyone hoping for feedback on the restore of Xandros from my careful backups went is likely to be disappointed, as I'm not likely to turn back if things go as well as they have so far.

Thanks for the tips and suggestions!

---

### Post by bkline on 2011-11-15
> **bkline said:**
> Does anyone know if eeeuser.com is gone forever?  Or is the server just down temporarily?

Looks like they're coming back to life, just slowly.  The site now has a message saying "Maintenance: Switching to new forum software, new infrastructure, etc."

---

### Post by bkline on 2011-11-18
One residual problem: the icon in the tray for eee-control displays an error message saying "Error while communicating with eee-control-daemon!  Make sure it is running."  I confirmed that the service is in fact in the process list.  Googling this error message was fruitless (partly because the eeeuser site is still down).  Anyone know what to do in response to this error message?

---

### Post by Plumtreed on 2011-11-18
....xandros is a dead duck........and those previously wonderful special OSs designed for EEEs are pretty much unnecessary a thing of the past as well.

About the only extra you may want to consider is Jupiter which may extend battery life and add a few extras features to your EEE.

When considering a new OS for your Asus you should consider Fuduntu which includes this Jupiter and is well suited for netbooks.....the install size is under 4GB so will leave you plenty of room to add any extras!

---

### Post by bkline on 2011-11-18
> **Plumtreed said:**
> When considering a new OS for your Asus you should consider Fuduntu which includes this Jupiter and is well suited for netbooks.....the install size is under 4GB so will leave you plenty of room to add any extras!

Thanks for the tip.  Never heard of Fuduntu; I'll take a look.  Linux users certainly can't complain that they have no choices. :-)

---

