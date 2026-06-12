---
title: "Access camera storage via USB"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-02-08
I would like to be able to browse my camera's contents in a file browser.  Ubuntu edgy opens a wizard to import the files which is nice but it doesn't find all of my files.  Namely the quick time *.mov files.  (which I cannot play and Im going to start another thread for that).

I would prefer if it came up as a mounted volume on the desktop like usb flashdrives do.  How can I make edgy do that?

---

### Post by teaker1s on 2007-02-08
right click on desktop panel, select add to panel, and select disk mounter.
it makes using removable media easier

---

### Post by Jive Turkey on 2007-02-08
yeah the disk mounter makes it really easy to access my 2 non existent floppy drives, as well as a USB flash drive, but no camera.

I dont think that app is named very well because it doesnt actually mount anything it just opens already mounted stuff when you click on it

---

### Post by teaker1s on 2007-02-09
works fine for me, otherwise there should be the drive icon appear as removable storage on desktop-this is how mass storage devices appear.

---

### Post by Jive Turkey on 2007-02-10
yes, thats what I want to happen but it doesn't, I hope someone could point me to some terminal commands that might force it since it doesnt happen automatically with my particular camera.

---

### Post by teaker1s on 2007-02-10
assuming that your drive is a mass storage device then this link explains mount commands


[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows")

think you need to use this command to work out your drive/partition location

[COLOR="Red"]sudo fdisk -l[/COLOR]

you are looking for usb drive which will be example sda4

---

