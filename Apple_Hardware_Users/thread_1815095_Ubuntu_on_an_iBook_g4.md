---
title: "Ubuntu on an iBook g4"
date: 2011-07-30
forum: Apple Hardware Users
---

### Post by baldymcgee on 2011-07-30
Recently my hard drive on my ibook g4 crashed beyond repair by DiskWarrior or Disk Utility. I don't want to buy a new hard drive and replace it, i've heard its a pain, and you can buy this laptop used on ebay for dirt cheap. But low and behold, i want to try running ubuntu on it, without using the HD.

I have run a live cd of ubuntu 10.04 PPC, which is the correct version for an iBook i believe, i tried to install the OS onto a 4gb flash drive. It installed succesfully, but the problem is, i can't boot the USB 2.0 drive on the startup.

I am running out of ideas how to do this without using the internal HD, i just want to use the laptop for taking notes in class. and i don't require to much space.

Does anyone out there have any ideas on how i can do this?
any help would be muchly appreciated.

I had an idea of maybe installing ubuntu 10.04 onto a DL 8.5gb dvd, but i'm not sure if that would work.
I'm pretty new to macs, so i don't really know what i'm doing. But any help would be great, thanks. :)

---

### Post by rsavage on 2011-07-30
[http://ubuntuforums.org/showthread.php?t=1812844](http://ubuntuforums.org/showthread.php?t=1812844)
 
[http://ubuntuforums.org/showthread.php?t=427714&page=20](http://ubuntuforums.org/showthread.php?t=427714&page=20)

---

### Post by baldymcgee on 2011-07-31
I read those threads, and I tried to boot from the USB using the open firmware and i still had no luck.
I'm guessing the ibook g4 doesn't support booting from the usb, only intel macs???

---

### Post by linuxopjemac on 2011-07-31
I also could not get to boot a USB on an iBook G4, don't know why.

---

### Post by rsavage on 2011-07-31
I can boot from usb on my ibook g4 (late 2004 model).  The trick is finding the right openfirmware command as it obviously changes with your setup and what port you stick the usb device in.  It is just trial and error, have a look on google for more guides.
 
If linuxopjemac is right and some ibooks can't then this maybe due to not having uptodate firmware????  Or maybe the USB stick is too modern?
 
I have not managed to install ubuntu onto a flash stick as mine is very cheap and I always fail on setting up a swap partition.  Could you try copying a cd iso to the usb stick with the dd command since that is what I know works?
 
If all else fails, it is not hard to take an ibook apart.  All you need are some small screwdrivers.  There are guides on google and even youtube!  The metal frame around the battery s very fragile so watch out for that.  It would be better to replace the hard drive in my opinion anyway.

---

### Post by B_Free on 2011-08-01
To install a new hard drive 
[http://eshop.macsales.com/installvideos/](http://eshop.macsales.com/installvideos/)

---

