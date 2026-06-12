---
title: "Boot Camp alternatives for CoreDuo Macbook?"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by XeutonMojukai on 2007-10-23
I currently use a CoreDuo MacBook with the Tiger OS.

I would use Boot Camp to ease my transition into Ubuntu, but unfortunately Apple has deactivated its firmware support of it, and doesn't allow me to download it at all.  This is all in preparation for it being standard in Leopard.

Basically, I'm wondering what kind of alternative to Boot Camp I should look to, now that Boot Camp is simply not an available choice for me anymore.

Thanks in advance.

~ XM

---

### Post by alephsmith on 2007-10-23
Boot camp is really just a GUI for resizing your OSX volume and a driver CD.

You can resize your volume from the command-line. For an explanation on how to NOT use bootcamp to triple boot look here: [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp).

Of course you will not have the drivers CD but that is only necessary for the legacy OS.

---

### Post by XeutonMojukai on 2007-10-23
Thanks very much, and hopefully I'll be back soon as a full-on member of the Ubuntu community :)

~XM

---

### Post by XeutonMojukai on 2007-10-23
I've followed the instructions, but since I only wanted a partition for Ubuntu, and not Windows XP as well, I wrote the following command line:

sudo diskutil resizeVolume disk0s2 40G Linux Ubuntu 15G

I was able to make the partition, but it lists its type as "Microsoft Basic Data".  The partition is listed as bootable, so I can't erase or reformat it.

Is this normal, or have I made a mistake?  If so, what should I do?

~ XM

---

### Post by cyberdork33 on 2007-10-23
> **XeutonMojukai said:**
> I've followed the instructions, but since I only wanted a partition for Ubuntu, and not Windows XP as well, I wrote the following command line:

sudo diskutil resizeVolume disk0s2 40G Linux Ubuntu 15G

I was able to make the partition, but it lists its type as "Microsoft Basic Data".  The partition is listed as bootable, so I can't erase or reformat it.

Is this normal, or have I made a mistake?  If so, what should I do?

~ XM
You are fine. You can boot the Ubuntu CD, select the partition, format it, and install to it.

---

### Post by XeutonMojukai on 2007-10-23
Now that I've downloaded Live CD, I've got the following file(s):

ubuntu-base-20060326.iso.bz2
-becomes-
ubuntu-base-20060326.iso
-becomes-
A Mounted Virtual drive called CDROM
-becomes-
A Mounted Virtual drive called Linux

Is there a certain one of these I should burn, or does it not matter?

Thanks again, guys!

~XM

---

### Post by FXEF on 2007-10-23
> **XeutonMojukai said:**
> Now that I've downloaded Live CD, I've got the following file(s):

ubuntu-base-20060326.iso.bz2
-becomes-
ubuntu-base-20060326.iso
-becomes-
A Mounted Virtual drive called CDROM
-becomes-
A Mounted Virtual drive called Linux

Is there a certain one of these I should burn, or does it not matter?

Thanks again, guys!

~XM

You do not need to mount the iso file. Unzip ubuntu-base-20060326.iso.bz2, then burn iso image ubuntu-base-20060326.iso to a CD. This will make a Live CD. Boot from this CD, then install Ubuntu.

FXEF

---

### Post by XeutonMojukai on 2007-10-23
Excellent, thanks!

~XM

---

### Post by XeutonMojukai on 2007-10-23
I burned the CD, and pressed C, but the system just went to rEFIt.

I then got rid of rEFIt as the documentation suggested, and it still would only go straight to Mac OS X.

I'm completely unable to boot from this CD, and I'm not sure if I'm doing something wrong or not.

~XM

EDIT: I think I may have solved the problem (I'm using Toast Titanium instead of the Mac OS X Burner program, so hopefully this will work better).

---

### Post by ItsMitsHere on 2007-10-24
try [http://ubuntuforums.org/showthread.php?t=560644]("http://ubuntuforums.org/showthread.php?t=560644")

---

### Post by cyberdork33 on 2007-10-24
> **XeutonMojukai said:**
> I burned the CD, and pressed C, but the system just went to rEFIt.

I then got rid of rEFIt as the documentation suggested, and it still would only go straight to Mac OS X.

I'm completely unable to boot from this CD, and I'm not sure if I'm doing something wrong or not.

~XM

EDIT: I think I may have solved the problem (I'm using Toast Titanium instead of the Mac OS X Burner program, so hopefully this will work better).Burn slowly...

rEFIt would not cuase your cd not to boot... it should, rather, show up in rEFIt as a bootable disc

---

