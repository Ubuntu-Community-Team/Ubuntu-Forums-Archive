---
title: "Installed but unable to boot!"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Jax Kovak on 2006-07-07
Hi,

Iv just finished installing Ubuntu and everything went well, or so I thought, and I am now left with a triple boot system that does not recognise that one of the systems is actually there!

Scenario:
I have 3 hard disks.
The main C: drive is my Windows 2000 installation. This is working fine.

The G: Drive, which is a separate hard disk, is my Windows XP installation. This too works fine (I'm there now).

The drive that would have been H: in windows is now my Ubuntu drive, but this does not boot. [EDIT] This drive is a second partition on the drive that is also home to Windows XP. (HD 2 - Partition 2)

There is also a separate data hard disk with no OS on it that is used by windows for storage. This is unaffected.

Problem:
Since I have had two windows installations I have a boot.ini file with two entries in it and I have the choice of which windows OS to boot from. This menu still appears and I can boot both windows installations from it. There is no sign of grub and therefore no way to boot into the Ubuntu installation.

Can anyone give me any ideas about how to boot my Ubuntu installation please.

All the best

Jax

---

### Post by richbarna on 2006-07-07
Take a look at this link:-
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

The complete page is in my sig "grub & menu.lst"
|
|
v

---

### Post by Jax Kovak on 2006-07-07
Thanks for the link richbarna, however, that page seems to deal with the 'Alternate' Ubuntu disk, which I don't have. All I have available is the Live CD.

What would be really good about now would be a way to add the Linux boot to the Windows Boot.ini file. I'm sure I head about this being done once before, but I have no idea how to do it.

I'm in Ubuntu now, using the Live CD to boot, but I have no idea where to go from here.

---

### Post by cotcot on 2006-07-07
You can get the alternative CD on [http://nl.releases.ubuntu.com/6.06/]("http://nl.releases.ubuntu.com/6.06/")

---

### Post by Jax Kovak on 2006-07-07
Thanks cotcot, yes I know *where* to get it, but I have the Live CD right here and I don't really want to download a whole CD just for this problem!

Surely there must be another way other than downloading another 600MB!! ](*,)

---

### Post by Jax Kovak on 2006-07-07
Well Iv done a little research of my own and tried various things (Remember that I only have the Live CD here) and I'm still no closer to booting my installed version of Ubuntu!

Iv tried:
```
(sudo) grib-install /dev/hdf1( and 2)
```

However, this just returns an error no matter which device I point at and I have to assume that this is because I'm running from the Live CD.

I also tried to get a copy of the boot code just in case it was there but simply not accessible:
```
(sudo) dd if=/dev/hdf1(and 2) of=/media/floppy/linux.lnx bs=52 count=1
```

This should have created a file (It did) that I could then use to add the Ubuntu OS to the boot.ini in windows. However, the files did not work and just left me at a flashing command prompt.

Assuming then that GRUB had failed to write anything to my system, perhaps because of the slightly odd HD set up, I then tried running GRUB on its own, and while this worked and it claimed that it had written itself successfully to the drive(s) it has resolutely failed.

Since using GRUB in this way I have tried to create the linux. lnx file again but with no success still.

I even went so far as to download the GAG bootloader program and while that will happily boot both of my windows installations it fails to boot the Ubuntu one.

I'm tempted to reinstall Ubuntu (Over itself as it were) but this seems pointless because if GRUB failed to sort things out the first time I see no reason for it to work the second time!

I have no intention of downloading a whole CD just to fix this problem when I already have a copy of the Live CD that was sent out to me.

Right about now I'm seriously considering just giving up and deleting the Ubuntu partition entirely.

---

