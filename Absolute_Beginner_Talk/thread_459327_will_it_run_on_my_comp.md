---
title: "will it run on my comp?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by redeath on 2007-05-30
iam thinking of installing Ubuntu on my old laptop to try it out.
its a PIII 700  almost 200 ram, will it run Ubuntu, and any pointers?
~Thanks.

---

### Post by Brunellus on 2007-05-30
> **redeath said:**
> iam thinking of installing Ubuntu on my old laptop to try it out.
its a PIII 700  almost 200 ram, will it run Ubuntu, and any pointers?
~Thanks.
does your laptop boot from a CD-ROM? 

What model is your laptop?

---

### Post by Nekiruhs on 2007-05-30
id try xubuntu.

---

### Post by redeath on 2007-05-30
yep, it boots from cd, but when i tryed running older Ubuntu live it loaded forever, so iam thinking alternate cd should do the job, also a while back  installed other versions of linux but i kept having problems with the screer resolution and/or refresh rate

---

### Post by kernel tom on 2007-05-30
> **Nekiruhs said:**
> id try xubuntu.

i definately agree with using xubuntu, because of how light it is compared to ubuntu and kde.
you do however need a CDROM drive in your boot sequence to be able to install it from the live CD

an easy way to check this is to go into your SETUP menu when u reboot your computer, look at the BIOS settings to see what boot order it has, and if CDROM drive can be added/made first priority.

EDIT: so you have the bootable cdrom... now as far as the resolution and refresh rates go for an older laptop, you may be able to find xserver drivers for your graphics card to help get you the correct resolutions and refresh rates

---

### Post by aidanr on 2007-05-30
i think you need 256mb of ram for the live cd, the alternate you need 128mb, also ubuntu would be fairly sluggish on that machine, i'd look at xubuntu or even fluxbuntu

---

### Post by chejrw on 2007-05-30
I run XUbuntu on a pIII 733 with 256 RAM, and it runs really well.  I used the normal CD to boot/install from the first time - it took probably 30 minutes to load, but it worked fine once it got going.  Once it was installed I had no problems.

---

### Post by redeath on 2007-05-30
> **chejrw said:**
> I run XUbuntu on a pIII 733 with 256 RAM, and it runs really well.  I used the normal CD to boot/install from the first time - it took probably 30 minutes to load, but it worked fine once it got going.  Once it was installed I had no problems.

any display or networking problems?

---

### Post by ugm6hr on 2007-05-30
> **redeath said:**
> any display or networking problems?

I've installed Xubuntu7.04 on a couple of laptops - including my Dell5000e (PIII 700, 256MB).  Easy, except that that laptop had an unusual display, but it was easy to sort after installation by editing xorg.conf.  The LiveCD will give you an indication if that is going to be a problem for you.  Runs just fine now.

As for networking - I manually installed ndiswrapper, and got my wireless working.  That laptop didn't have ethernet which made it a bit trickier (although not so hard I couldn't get wireless working within 30 minutes).  The laptop I'm posting from is more modern, but the built in ethernet just worked.  I think the settings defaulted to DHCP, so all I did was plug it in.

If you have wireless, and you want automatic connection, Network Manager is useful, but needs to be downloaded after installation.

Honestly - try the LiveCD.

---

