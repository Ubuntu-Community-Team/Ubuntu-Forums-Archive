---
title: "Install from USB, using osx to prep media"
date: 2010-01-12
forum: Apple Hardware Users
---

### Post by dirty.hippy on 2010-01-12
I am trying to install ubuntu onto a computer without a cd drive.  I  have only a macbook at my disposal, with no other OSes easily available.   According to [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick"), I need a .img image to boot from USB.   How can I convert the stock .iso image to a .img image suitable for USB  installation?  The guide lists no osx-compatible converters, and Google  isn't turning anything up.  Is a regular Ubuntu install (not Net Remix)  available directly in .img format?  I have not been able to find it if  so.  Or, is there another method I'm overlooking?  Thanks in advance for  suggestions!

---

### Post by iponeverything on 2010-01-13
It is just an extension, for your purposes the file is the same.

If the extension matters to you change it with: 

```
mv file.iso file.img
```

---

### Post by dirty.hippy on 2010-01-13
My understanding is that while the file format of .img and .iso my be identical, Ubuntu releases on .imf are formatted for usb booting while releases on .iso are formatted for optical disk.  Just changing the extension won't repack a release intended for cd/dvd for usb.  I'd love to be wrong about this, though.

---

### Post by linuxopjemac on 2010-01-13
read this howto:
[http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick](http://mac.linux.be/content/installation-ubuntu-karmic-koala-macbook-pro-31-usb-stick)

---

### Post by dirty.hippy on 2010-01-13
Perhaps I wasn't clear, but I'm not trying to install ubuntu to my macbook, but to another computer.  Using that guide as a starting point, would it be possible to: follow the first 3 steps (through installing to a usb stick) as described, then use the USB stick to boot my new computer, then install ubuntu to the HDD of the new computer from the running USB installation?

---

### Post by linuxopjemac on 2010-01-13
If your "other computer" is also a Mac, you need that fancy EFI stuff. Otherwise I would just follow this wiki:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by dirty.hippy on 2010-01-13
That's the guide I have been using, and linked to in my first post.  It requires a .img file, which I do not have and cannot find.  I can find one for UNR, but I don't want UNR, I want regular old Ubuntu.

[edit] The computer I'm trying to install to is not a mac, it's a regular old atom amd64.

---

### Post by mick222 on 2010-01-13
Try unetbootin i think it's available for mac . That will create a bootale usb from an iso file

---

### Post by dirty.hippy on 2010-01-13
> **mick222 said:**
> Try unetbootin i think it's available for mac . That will create a bootale usb from an iso file

Unetbootin is not available for OSX.

---

### Post by linuxopjemac on 2010-01-13
didn't read well, sorry.

---

### Post by dirty.hippy on 2010-01-13
> **linuxopjemac said:**
> didn't read well, sorry.

No worries, I appreciate the suggestions!  It's irritating that my use case is not so well supported, but that's life.

---

### Post by Kevbert on 2010-01-13
Can you run up a Ubuntu live-CD ? If so, there should be an option to make a USB startup disk (under System-Admin) then just point it to your ISO file and you should be OK.

---

### Post by dirty.hippy on 2010-01-13
> **Kevbert said:**
> Can you run up a Ubuntu live-CD ? If so, there should be an option to make a USB startup disk (under System-Admin) then just point it to your ISO file and you should be OK.

That is interesting, I shall have to give it a try.  Also, I suppose unetbootin would work from the liveCD as well...

---

### Post by mick222 on 2010-01-13
You could always install ubuntu remix then 
```
sudo apt-get install ubuntu-desktop
``` and remove netbook remix you should then have a normal ubuntu install .

---

### Post by linuxopjemac on 2010-01-13
I found something interesting:

I erased a USB stick, then unmounted it:

jeroen-diederens-computer:/Users/jeroen/Desktop root# diskutil unmountDisk /dev/disk1

I converted the .iso file into a .dmg file with Toast. Then I dd-ed it to the USB...

jeroen-diederens-computer:/Users/jeroen/Desktop root# dd if=/Users/jeroen/Desktop/disk2.dmg of=/dev/disk1s1 bs=1m
149+1 records in
149+1 records out
157258921 bytes transferred in 140.699247 secs (1117696 bytes/sec)

I can't boot from it, probably because it's only MBR, but I guess when I stick it in a PC, it will boot. I will try later to put it in a PC.

EDIT: I cannot set the BIOS of my PC to boot from USB, I guess the PC is too old for that...

---

### Post by dirty.hippy on 2010-01-13
> **mick222 said:**
> You could always install ubuntu remix then 
```
sudo apt-get install ubuntu-desktop
``` and remove netbook  remix you should then have a normal ubuntu install .

This seems like the ticket, thanks!

> **linuxopjemac said:**
> I found something interesting:

...



In poking around the BIOS of the new computer, I found an option to boot from a USB HDD, but treat it as a CDROM.  If the UNR image doesn't work out I'll explore this option more.

---

### Post by mick222 on 2010-01-13
> EDIT: I cannot set the BIOS of my PC to boot from USB, I guess the PC is too old for that..
   I thought that to but was installing lucid and used f11 to choose the boot device and discovered boot from usb device there, my phone was pluged in.

---

### Post by dirty.hippy on 2010-01-13
Well, I finally got things going using unetbootin.  I first tried using  on the ubuntu livecd, but it refused to install because of a dependency  problem (p7zip-full, not that it matters).  Luckily a friend stopped who  had a windows VM available, so I was able to use the windows version of  unetbootin.  Thanks for the suggestions, everyone!

---

### Post by linuxopjemac on 2010-01-14
Just for your information:

I was able to make a bootable USB from within Ubuntu with a net install iso of Debian Lenny. I inserted the thing on my work PC and I booted in Debian. It works very well for PC. I could not get the same to work for an Intel Mac, not even with GPT or Mac partitioned USB drive. rEFIt complained about the firmware of my MacBook 2,1 (EFI 1.1). Probably it's not good enough for USB booting.

---

