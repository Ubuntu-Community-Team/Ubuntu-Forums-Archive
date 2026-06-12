---
title: "GParted Live CD"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2007-08-23
I need to use Gparted and I've heard its on the 6.06 Live CD (I still use Dapper Drake :P) but when I launch the Live CD it boots straight into the OS, and if I run Gparted then, I can't resize because the HDD is mounted. How can I change the boot order? OR what do I need to do to boot from the CD first.
Dan

---

### Post by tompickles on 2007-08-23
Have you changed the Boot order in the BIOS to boot the CD first?
The other option is if the HDD is automatically mounted in the Live CD environment, you count unmount it - not exactly sure how, but think you can do it by right clicking on it in the file manager - then running GParted through System -> Administrator.

Hope this was some help!

---

### Post by Hopeless on 2007-08-23
mate

[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

step by step bios how to...

HTH...:KS

---

### Post by dptxp on 2007-08-23
The key to go to bios may not be 'DEL'. See at bottom of screen when you boot.

---

### Post by Skidpad on 2007-08-23
If you don't gey your bios boot order figured out,  you can unmount a drive from within GParted while running the OS - its under the "Partition" tab (on my Edgy installation anyway).

Additionally, you can also download GParted itself and make a boot cd from it alone.  That way, you don't have to worry about any OS loading during boot.  I keep this cd around as part of my "toolkit".  :)

---

### Post by Dr Small on 2007-08-23
I found that my BIOS key, to access the BIOS was F2, from what the manual said, so I made a note in the back in case I ever forget. ;)

Why can't you just download Gparted from the repositories and use it on your OS, instead of booting up on the livecd?

Dr Small

---

### Post by Terl on 2007-08-23
Or use the gparted live cd.  Works like a charm.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

