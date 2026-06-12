---
title: "Problem with making USB bootable on Mac"
date: 2012-04-26
forum: Apple Hardware Users
---

### Post by Wheels2050 on 2012-04-26
I'm attempting to make a USB that contains a full install of Ubuntu (i.e. NOT just a Live CD) that will boot on PCs or Macs. Making it bootable on PCs is fine, and I've successfully achieved that.

However, making a Mac-bootable USB is proving difficult. I followed (with some modifications, due to what I'm trying to do) the steps shown here:

[http://ubuntuforums.org/showthread.php?t=1065670](http://ubuntuforums.org/showthread.php?t=1065670)

Following that, I have a USB that can boot on a PC as well as a Mac laptop from a couple of years ago (although I'm not entirely sure what model it is).

However, upon trying the same USB on a newer Macbook Pro (from late 2011) the GRUB menu was not shown. After selecting rEFIt from the MAC boot menu and selecting Linux, the error about not being able to find any bootable devices is shown and Ubuntu is not accessible.

Does anyone know what might have changed with the newer Mac that does not allow one to access GRUB?

---

### Post by ts3 on 2012-04-28
I made a bootable USB with 12.04 fairly recently, post on the last page here: [http://ubuntuforums.org/showthread.php?t=1261747&page=4](http://ubuntuforums.org/showthread.php?t=1261747&page=4)

Used dd on a mac and one of the 12.04 daily builds which had "+mac" in the iso name.  The precise-desktop-amd+mac.iso from here should work [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) It's dated April 25 so it's probably the last daily build before the final release.

Hope it works for you, the macs seem fairly temperamental when it comes to booting off USBs, I was thrilled to bits when it finally worked on my laptop.

---

### Post by pnneves on 2012-04-28
I tried to access the image u mention, but got an "access denied" error...do u know how to circumvent this in order to download the iso file?
Thx!

note- from another guy desperate to be able to boot ubuntu from a usb pen drive :P

---

### Post by lael on 2012-04-29
> **pnneves said:**
> I tried to access the image u mention, but got an "access denied" error...do u know how to circumvent this in order to download the iso file?
Thx!

note- from another guy desperate to be able to boot ubuntu from a usb pen drive :P

Same here.

---

### Post by mode7 on 2012-04-29
I don't know why the access is denied to the ISOs, but FWIW, the torrent for Mac image in the Precise release folder does download. (Looks like it only has 1 seed, though)
[http://cdimage.ubuntu.com/releases/precise/release/]("http://cdimage.ubuntu.com/releases/precise/release/")

If you really are desperate, you may want to try using a standard image (Not "Mac adjusted").
I really have no clue what changes they make to the Mac images, but I've been using standard images for a while now, and they work just fine on my Macbook 8,1 for standard installs. In fact, I cannot get the Pendrive+CD combo booting trick to work when using a Mac image.

---

### Post by ts3 on 2012-04-29
> **pnneves said:**
> I tried to access the image u mention, but got an "access denied" error...do u know how to circumvent this in order to download the iso file?
Thx!

note- from another guy desperate to be able to boot ubuntu from a usb pen drive :P

Sorry the link didn't work; at first I thought it was because the daily build is switching to 12.10 (no rest for the developers I guess) but then the link to the regular release [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/) didn't work either.  I followed the link at the top of that page to mirrors, then clicked on one of the US mirrors for the DVD install and found a working download in a mirror here: [http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/precise/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/precise/release/)

I'd make sure it's the desktop .iso rather than the alternate which is first on the list & I'd check the md5sum.  The mirror is hosted by something called the Argonne National Laboratory for what that's worth.

But first, if I had to do it from scratch, I'd try the regular final 12.04 amd64 release and see if it boots off a USB made using dd as described above; it seems to have worked for other people.

---

### Post by PaisCharos on 2012-04-29
I'm fairly new to Linux and have had a very disappointing couple of days trying to get *something* installed on my MacBook 3,1.  I was able to make a CD for 12.04, which installed fine but wouldn't boot unless I booted from the CD.  After exhausting every how-to instruction regarding that, I decided to try an older version, so I downloaded 10.10.

Unfortunately I no longer have any CDs available (at least none with enough space) and can't readily get to a store to get one, so using UNetbootin I burned it onto my USB device.  Now, of course, my MacBook won't recognize the USB as a boot device.  I've tried both UNetbootin AND I've tried doing it manually with dd.  I even tried dding the USB device onto a partition of my MacBook's HD, and that didn't even show up as a bootable device.

As a newbie to Linux, this has all been quite frustrating.  Does anyone have any suggestions on what I should do now??  :confused:

---

### Post by iqtedar on 2012-04-30
Trying to create a bootable USB stick of Ubuntu for the Mac has been time-consuming, very frustrating and unsuccessful thus far. I've tried so much over the past 3 days but nothing seems to work. In the end, I burned the ISO image onto a CD and used an external drive to boot the Mac and install Ubuntu. I've learned that Linux is lacking in proper support for Macs. For your information, I used the ubuntu-12.04-desktop-amd64+mac ISO to install onto a Macbook early 2009 model with a faulty optical drive. Now I'm faced with the daunting task of trying to install Ubuntu onto older G3 iMacs as well (for classroom use) and it's far from straightforward. At the same time, I need to keep partitions with the Mac OS installed too and the Linux support for hfs is very poor.

---

### Post by Wheels2050 on 2012-05-01
Thanks for the replies. Unfortunately, I require a full install on a USB, which may complicate things somewhat (I usually just see talk of doing it with a LiveCD).

I was attempting to use Ubuntu 10.04 32-bit edition. Does anyone know if (late model) Macbook Pros have some restriction against using 32 bit OSs?

---

