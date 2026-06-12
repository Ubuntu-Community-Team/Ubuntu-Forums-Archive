---
title: "Install &amp; Dual Boot on a MacBook, w/o CD?"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by Riddlez on 2009-04-10
Let's just say... I'm a giant newb. I know nothing about Linux or Ubuntu so far, but I'm looking to install it to be able to run some extra apps.

My biggest problem, aside from the newbness, is that my MacBook is unable to burn CDs. I've seen a few threads about how to install Ubuntu without a peripheral device, but... I haven't been able to really understand what they're saying.

So, would it be possible for someone, or a group of someones, to **really** walk me through the partitioning and installation process without the use of a CD/DVD or USB flash drive? Help would be greatly appreciated.

From what I can tell, this is a great community, and I hope to stick around long enough to be able to help others out in the future. Cheers!

---

### Post by cyberdork33 on 2009-04-10
> **Riddlez said:**
> My biggest problem, aside from the newbness, is that my MacBook is unable to burn CDs.
order a disc online or get a friend to burn it for you.

Also, how do you have a Macbook without a burner?

---

### Post by khelben1979 on 2009-04-10
I think that [this]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") (installation netboot install from internet) is what you're looking for.

---

### Post by Riddlez on 2009-04-11
> **khelben1979 said:**
> I think that [this]("https://help.ubuntu.com/community/Installation/NetbootInstallFromInternet") (installation netboot install from internet) is what you're looking for.

That's probably exactly what I'm looking for, but, unfortunately, I don't understand a word of it... that's the reason for a separate topic. :(

---

### Post by pxwpxw on 2009-04-11
> **Riddlez said:**
> That's probably exactly what I'm looking for, but, unfortunately, I don't understand a word of it... that's the reason for a separate topic. :(

It is not quite right for you , unless you already have another linux OS on you MacBook, with a grub bootloader. 

However the Net install method does work just using MacOSX - briefly -

Download the linux and initrd.gz installer files direct to your OSX partition.
Download install and try rEFIt which all intel macs should have for linux.
Download install grub.efi bootloader which finally can boot (from command line) the linux and initrd.gz installer, all from the OSX partition.
All these files are quite small.

The Net installer images then download all the ubuntu installation from the internet.

In fact we used the net installer images as a test for grub.efi debugging on the grub2 EFI bootloader thread
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

Post #523 has grub.efi attachments for download.

rEFIt is from refit website

Installer linux and initrd.gz files as above except you need later version intrepid 810 or jaunty 904.

Index of /ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386
[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

Also need to know what is your MacBook model - as in 'About this Mac'. MacBook2,1?..5,1?..


Thats assuming you dont want to try getting a CD.

---

### Post by khelben1979 on 2009-04-11
In the above you need a bootloader command to be able to execute the file, but I think that's not the best way for you to do this in any case. (so you can forget this)

If you download a netinstall iso image file of Ubuntu and then extract it's file contents to a usb memory and then boot it just like an ordinary CD-R or DVD-R disc, then you will have this working!

I suspect that you might need to alter your BIOS settings so that it will be able to boot from the usb disc and I'm not sure that your BIOS supports this, but it might. My old pc at home which I bought for nearly six years ago is able to do this.

---

### Post by pxwpxw on 2009-04-11
> **khelben1979 said:**
> In the above you need a bootloader command to be able to execute the file, but I think that's not the best way for you to do this in any case. (so you can forget this)

If you download a netinstall iso image file of Ubuntu and then extract it's file contents to a usb memory and then boot it just like an ordinary CD-R or DVD-R disc, then you will have this working!

I suspect that you might need to alter your BIOS settings so that it will be able to boot from the usb disc and I'm not sure that your BIOS supports this, but it might. My old pc at home which I bought for nearly six years ago is able to do this.

That works on a PC with pc bios, but the fundamental problem with Apple Intel Macs is they dont boot legacy grub pc-bios bootloaders from external.

Thats where the gub2 grub.efi bootloader comes in to the rescue.

---

### Post by cyberdork33 on 2009-04-11
Also, he said he didn't want to boot from USB.

---

### Post by khelben1979 on 2009-04-12
> **cyberdork33 said:**
> Also, he said he didn't want to boot from USB.

Yes, but why?

---

### Post by cyberdork33 on 2009-04-12
> **khelben1979 said:**
> Yes, but why?
why not boot from CD?

---

### Post by Riddlez on 2009-04-14
Actually, I'm in luck...

The fact was that I was too lazy to go out and get a USB drive, but, for other reasons, I had to buy one anyway.

I can't boot from a CD because I don't have a working burner. This computer might as well be dead, because only about half of it really works.

---

### Post by pxwpxw on 2009-04-14
> **Riddlez said:**
> Actually, I'm in luck...

The fact was that I was too lazy to go out and get a USB drive, but, for other reasons, I had to buy one anyway.

I can't boot from a CD because I don't have a working burner. This computer might as well be dead, because only about half of it really works.

So use the method I outlined at post #5.

---

