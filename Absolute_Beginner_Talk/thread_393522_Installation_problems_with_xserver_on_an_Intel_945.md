---
title: "Installation problems with xserver on an Intel 945 graphics card"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by infernon on 2007-03-25
I am attempting to install Ubuntu 6.10 on my Dell Latitude D620 laptop.  It has a Mobile Intel 945GM Express chipset.

After attempting to boot from the CD menu using either the normal boot option or the safe graphics mode option, I receive an error message telling me that the X Windows server failed to start.  

I810: No matching Device section for instance (BusID PCI:0:2:1) found
I810(0): No video BIOS modes for chosen depth.
Screens found, but none have usable configuration.
Fatal Server Error:
No Screens found

I've searched around and no one seems to be having this problem during the actual installation, but rather after they install.  Are there boot options that I can set to force the installation to proceed?

---

### Post by lamalex on 2007-03-25
try adding this bootflag, vga=(some number and resolution). hit f1 i think to see what flags you can add, pick the vga one with the correct parameters after it and then hit f6 to add it. that should force some video options. I don't have a livecd on me to test it, but give that a try!

---

### Post by infernon on 2007-03-26
I believe that the correct bootflag is vga=771.  Unfortunately, it didn't make much of a difference other than making the screen appear a bit different than that.

Someone has to have figured this one out, it's a common video card. :confused:  Does anyone know where I need to go from here?

---

### Post by zvacet on 2007-03-27
```
sudo dpkg-reconfigure xserver-xorg
```
and pick your card

---

### Post by infernon on 2007-03-27
I can't do that.  This happens when I attempt to boot from the live cd.  As soon as I select any option from the boot menu, the same thing happens.  I have also attempted changing boot flags with no success.

---

### Post by infernon on 2007-03-27
I don't mean to be a pain, but I really need any help that anyone could provide on this:)

Bump!

---

### Post by infernon on 2007-03-28
Just as a follow-up, I have found out about the Alternate CD which is available from the download mirrors.  I was able to install Ubuntu using this disc and now have access to a command line with which I can resolve the video problems.  

If someone is running into this on Dell Latitude D620 laptop with the video card described above, you need only to use the Alternate CD to install.  Good luck.

---

### Post by tschneiter on 2007-03-28
Im on a 640m here (from dell) and ran into the same troubles. My solution was to start the process with a secondary monitor plugged in, and then install as normal. Just having the second monitor plugged in made the primary monitor work properly. After I finished the install, I needed to run 915resolution to get the primary working properly on its own.

Good Luck! (and just use the alternate install CD if this hack doesnt work)

---

