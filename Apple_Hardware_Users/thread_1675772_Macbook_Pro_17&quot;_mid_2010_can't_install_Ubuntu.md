---
title: "Macbook Pro 17&quot; mid 2010 can't install Ubuntu 10.10"
date: 2011-01-26
forum: Apple Hardware Users
---

### Post by k1piee on 2011-01-26
Hi,

I have a Macbook Pro 17" mid 2010 and I want to install Ubuntu on it, dualboot with OS X.

The thing is that I have replaced my CDROM with a 1TB harddrive which I want to install Ubuntu on.

I have installed rEFIt and it works just fine. I tried to install Ubuntu using a USB-stick using [this ]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")guide but it doesn't get recognized during boot, it doesn't show up in rEFIt and not even if I hold down the option key during boot, it will just show Machintosh HD and not the USB-stick.
For the record it gets recognized in OS X just fine.

So I tried using an external CDROM and it recognizes it just fine if I hold down the option key and I can boot into it, I get to the grub menu and select "Try ubuntu" but after that the screen just goes black and after a while the cdrom spins down and eventually stops completely. Had it like that for about 30min and absolutely nothing happened.

Is there anything else I can try?
I can't put my internal CDROM back in because then I don't have the 1TB disk that I want to install Ubuntu on and I would really want to avoid put the 1TB disk in the main HDD-slot and install OS X on it Just so I can install Ubuntu on it, if that's even gonna work.


Thanks,
-Patric

---

### Post by k1piee on 2011-01-26
Okey so I just noticed something.
When I boot with the CD in my PC it boots up to a graphical interface directly where I have a window with "Try Ubuntu" and "Install Ubuntu" buttons.

This one: 
[IMG]http://data.fuskbugg.se/dipdip/_IMG_20110126_132133.jpg[/IMG]

But when I boot up my Macbook with the same CD I get just a black Grub menu with the same options..

This one:
[IMG]http://data.fuskbugg.se/dipdip/_IMG_20110126_132238.jpg[/IMG]

And if I choose, for example, Try now it I just get a black screen and the CDROM turns it self of eventually.

I tried to modify the entries in Grub to boot it in verbose without the splashscreen but no luck there either..


Anyone knows how to fix this?

---

### Post by k1piee on 2011-01-26
I tried with Debian and at least that one shows up in rEFIt but I get this error:

```
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Not Found from LocateDevicePath
Error: Load Error while (re)opening out installation volume

The firmare refused to boot from the selected volume.
Note that ecternal hard drives are not well-supported
by Apple's firmware for legacy OS booting.

*Hit any key to continue*
```

And it freezes.

Can I update this firmware somehow to get it working?

---

### Post by k1piee on 2011-01-28
Ok so I tried putting back the CDROM and it boots up from the CD just fine now..

So the only problem is that I don't have the harddrive installed where I want Linux.
Can I somehow install it on the drive thats in now and move it to the other drive when I swap the CDROM for the harddrive again?

---

