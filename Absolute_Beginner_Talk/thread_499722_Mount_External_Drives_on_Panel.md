---
title: "Mount External Drives on Panel?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2007-07-12
Hello,

I was wondering if anyone knew how to make an external (usb) hard drive mount on the gnome panel.  I don't really like icons on my desktop...

I tried out the Sabayon Linux live cd and in that OS they automatically mounted each hard drive on the kde panel.  Does anyone know if there's a way to do this on Ubuntu?

I appreciate any suggestions.  

Thanks!

---

### Post by mikewhatever on 2007-07-12
There is an applet called Disk Mounter you can add to the panel. Right click on the panel-->Add to Panel, and chose Disk Mounter. That should be it. I've checked it on Ubuntu 7.04, but not sure it works the same on Kubuntu 6.10 if that's what you use.

---

### Post by NewRubberSoul on 2007-07-13
PERFECT!

That was exactly what I was looking for and so easy!  Thank you.

Do you know if there's any (simple) way to take the floppy drive off of there?  (I never use it.)  It shows two floppy icons, I only have one floppy drive.  They both say "unmounted"

---

### Post by Ek0nomik on 2007-07-13
> **NewRubberSoul said:**
> PERFECT!

That was exactly what I was looking for and so easy!  Thank you.

Do you know if there's any (simple) way to take the floppy drive off of there?  (I never use it.)  It shows two floppy icons, I only have one floppy drive.  They both say "unmounted"

You could simply right click on the panel, select Add To Panel, Custom Application Launcher, then select File, and just put in your mount point as the path.  Then you can customize the logo, etc.

---

### Post by mikewhatever on 2007-07-13
> **NewRubberSoul said:**
> PERFECT!

That was exactly what I was looking for and so easy!  Thank you.

Do you know if there's any (simple) way to take the floppy drive off of there?  (I never use it.)  It shows two floppy icons, I only have one floppy drive.  They both say "unmounted"

No, I don't. Permanently unmonting partitions in Feisty is somewhat irregular. For example, I have three partitions I do not ever want mounted. I've even deleted the related lines from fstab, but, two partitions keep showing as unmounted, while the third does not show at all. That was not the case in Edgy. If you find the way to get rid of the unwanted ones, please let me know.

---

