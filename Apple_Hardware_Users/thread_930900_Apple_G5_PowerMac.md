---
title: "Apple G5 PowerMac"
date: 2008-09-26
forum: Apple Hardware Users
---

### Post by liquidfunk on 2008-09-26
Considering it's specs are about the same as mine, how well would this perform? 

[http://cgi.ebay.co.uk/APPLE-G5-POWERMAC-DUAL-CORE-2-3GHZ-4GB-250GB_W0QQitemZ120309997537QQcmdZViewItem?hash=item120309997537&_trkparms=72%3A1300%7C39%3A1%7C66%3A2%7C65%3A12%7C240%3A1318&_trksid=p3286.c0.m14](http://cgi.ebay.co.uk/APPLE-G5-POWERMAC-DUAL-CORE-2-3GHZ-4GB-250GB_W0QQitemZ120309997537QQcmdZViewItem?hash=item120309997537&_trkparms=72%3A1300%7C39%3A1%7C66%3A2%7C65%3A12%7C240%3A1318&_trksid=p3286.c0.m14)

---

### Post by DRM_free on 2008-10-24
It's a fairly recent and powerful system, but Apple makes a lot of proprietary customizations to its hardware, so Ubuntu may not have optimized drivers for it.

---

### Post by brain2008 on 2008-10-24
The professional-grade computer was the most powerful in Apple's lineup when it was introduced, and was touted by Apple as the fastest personal computer ever built. The Power Mac G5 was introduced with three models, sharing the same physical case, but differing in features and performance.
==================================================
Brian
Our mission is to provide high quality end to end solutions to the BPO segment in a manner that will improve the operational efficiency while reducing the cost of the services to the client.
[email]4thdimension1@gmail.com[/email]

---

### Post by tiresia on 2008-10-24
Ubuntu runs very well on my PowerPC G5 (2x2.5).
To get a first impression, before installing Ubuntu, you can try the LiveCD.
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

The Mac G5 is a 64 bit powerpc - so when you install or run the LiveCD at yaboot prompt, hit TAB and choose the powerpc64 option. You have the same limitation as every PowerPC (no flash - but I don't find this a big limitation, there are other solutions). If you need to use MOL (Mac on Linux), there is no port for Powerpc64. Anyway you can always use a dualboot configuration with MacOSX. 

Be aware that in some powermac g5, the installer fails to install a correct yaboot configuration.
Here you can get more informations. [https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607)
This bug should be solved in the next release (Intrepid)

---

### Post by pxwpxw on 2008-10-24
> **tiresia said:**
> Ubuntu runs very well on my PowerPC G5 (2x2.5).
To get a first impression, before installing Ubuntu, you can try the LiveCD.
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)


Be aware that in some powermac g5, the installer fails to install a correct yaboot configuration.
Here you can get more informations. [https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607](https://bugs.launchpad.net/ubuntu/+source/yaboot/+bug/122607)
This bug should be solved in the next release (Intrepid)

The current powerpc64 intrepid version has the revised yaboot package (ofpath) fix, and it installed nicely here on g5 to an external firewire and dual internal sata, for a cli install. Then sadly. for the GUI, the xorg install fails, "cant find core keyboard", and I had to go back to using xorg from hardy, with the intrepid kernel and base.

---

### Post by tiresia on 2008-10-25
> **pxwpxw said:**
> Then sadly. for the GUI, the xorg install fails, "cant find core keyboard", and I had to go back to using xorg from hardy, with the intrepid kernel and base.

In the last days I tried to install Intrepid on my G5, but my Drive could not mount the CD. I did then a dist-upgrade from Hardy. There was no GUI, as you report. But yesterday I updated the system, and now everything is working well.

---

### Post by pxwpxw on 2008-10-25
Yes I now have intrepid X gui running ok on a reinstall of xorg, after having installed and removed hardy and gutsy xorg to compare. Don't want any special effects or video/audio for now. Installed using the net instaall mini.iso, very slow server at ports.ubuntu.com. (20kB/s average).

---

### Post by tiresia on 2008-10-25
> **pxwpxw said:**
> Yes I now have intrepid X gui running ok on a reinstall of xorg, after having installed and removed hardy and gutsy xorg to compare. Don't want any special effects or video/audio for now. Installed using the net instaall mini.iso, very slow server at ports.ubuntu.com. (20kB/s average).
Which g5 do you have? Have you got problems with the installer CD?

---

### Post by Frak on 2008-10-25
Let's just say, if I lived in the UK, I'd buy it.

G3's run slow, G4's run rapid with 3rd party upgrades, G5's run rapid with no upgrades (don't think there are any).

---

