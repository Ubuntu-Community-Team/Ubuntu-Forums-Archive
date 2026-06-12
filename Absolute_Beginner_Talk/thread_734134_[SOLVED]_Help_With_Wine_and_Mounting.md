---
title: "[SOLVED] Help With Wine and Mounting"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by ClearyA on 2008-03-24
Ok, so im new to linux i finally got rid of windows because i was sick of the instability and cost etc.. however i do enjoy video games haha and i was wondering how exactly (im so new i need detailed instructions) of how to mount an iso file (.ccd file) with wine to install a game. please help!!!

---

### Post by AndyCooll on 2008-03-24
Assuming you've installed Wine, if using the gui usually you just need to navigate to the setup.exe on the disk and then double click on it. Wine should then kick in. 

From the command line (Applications > Accessories > Terminal) it might be something like this:
```
cd /media/cdrom0
wine setup.exe
```

You shouldn't need to manually mount an iso, it should do so automatically when you put the CD in. However if it isn't already a CD I found this link that might give some help: [CD-Images]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES")

:cool:

---

### Post by very_japi on 2008-03-24
I think he doesn't want to load Cd's and would rather mount ISO files.

so, this is how you mount an ISO

mount -o loop -t iso9660 file.iso /media/cdrom0

You can convert other cd images to ISO files using poweriso (google it).

Algo theres a graphical utilty called gmount-iso or something like that.

---

### Post by herbster on 2008-03-24
You may wish to try Acetoneiso2: [http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.1_x86.deb?modtime=1202501447&big_mirror=0](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_2.0.1_x86.deb?modtime=1202501447&big_mirror=0)

It's a GUI app that can mount, unmount, browse your ISOs, convert them, etc. etc.

---

### Post by bulletxt on 2008-03-25
AcetoneISO2 is the best and also the only solution that actually works in 99% of case. it also does a lot of other stuff.

---

