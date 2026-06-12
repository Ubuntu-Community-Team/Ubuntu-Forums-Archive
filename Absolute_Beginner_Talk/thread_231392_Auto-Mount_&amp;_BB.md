---
title: "Auto-Mount &amp; BB"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by amazongalhn on 2006-08-07
Hollo-this is my first foray into the forums here.

  I tried searching for the answer to my question,  but didn't see what I wanted.  I know an auto-mount feature is working vis-a-vis the cdrom drive because when I boot the system the disc shows on the desktop if the drive contains a disc;  otherwise not.

  My question:  How does one turn off/on the automount feature for the cdrom?  I've looked in fstab and the entry for the cdrom reads:
   /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

  So noauto (mount).  From the search results the next most likely candidate is Gnome.  Likely,  because a Gnome window pops up whenever I insert a disc.

  My system: a personlly assembled bunch of parts from newegg.com.  Dual boot, Windoze 98SE,  Ubuntu Breezy - the Breezy is pretty much vanilla;  only a couple of tarballs and something from Debian.  Synaptic reports a couple of archives not found but otherwise functions normally.

I may not answer immediately as I've got to go to work.

---

### Post by OpsVentus on 2006-08-07
/dev/hdc /media/cdrom0 udf,iso9660 **nouser**,noauto 0 0

Will not allow users to mount it. Properly it won't automount.

Cheers,
Bart.

---

### Post by mcduck on 2006-08-07
In Gnome's menu, open System/Preferences/Removable Drives and Media, and on Storage tab there are checkboxes for 'Mount removable drives when hot-plugged' and 'Mount removable media when inserted'. :)

---

### Post by amazongalhn on 2006-08-07
Thanks OpsVentus.  True, did not mount on boot.  Could mount/umount as R/O disc w/ content via sudo; Gnome poped up a window showing content.  But blanks still auto mount - asks if I want to burn something.   :(

---

### Post by amazongalhn on 2006-08-07
Hey mcduck,  that worked pretty good.  I unchecked all the items on the menu.  What I have now is no mount on boot if not mounted before;  no pop up if I insert a blank disc.  All good.

I still get an icon on the desktop and an accompanying label of the disc.  The cdrom is not mounted according to mount.

Here is what I'm working toward:  I want to use [shunt]("http://www.serice.net/shunt/") to create multi-disc archives.  To this end I need the cdrom drive to be left alone so shunt has complete control over it.

I'm going to try this using the arrangement I've got so far.  Ultimately,  I intend to load DD.  But I want to be able to reload my system if something goes south.   Also I need to develop a back-up capability ( doesn't everyone?  :)

---

### Post by OpsVentus on 2006-08-08
Sometimes the answer is more easy then fstab. :)

Cheers,
Bart.

---

