---
title: "how to run windows games without inserting disks"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by davew_tx on 2007-12-13
complete Noobie here, mc'lovin Ubuntu........

Need to know how to put games on and run them without inserting all the disks when the kids want to play.   In Windows, there was game drive, although I never ran it.  Just heard about what it did.

Anyone got a recipe for that?

---

### Post by CaptainInsaneO on 2007-12-13
You could copy all the files on the disc to a directory on your harddrive. That's how I install a lot of multi-disc games with wine, maybe it'll work for what you need as well. :)

---

### Post by defrex on 2007-12-13
My first thought would be to get an iso image of the dist in question, and then mount it as a drive.

Put the disk in your drive, and right click on the disk icon that shows up on the desktop. There should be a "copy disk..." option. In that menu, you can select to copy it to a file. Name and save the .iso somewhere.

Then follow this howto for mounting/unmounting iso images using a gui tool.

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

---

### Post by davew_tx on 2007-12-14
thanks, I'll give those a try.

Also, when I install Quake 2 from the Synaptic, all I get is a .sh file in my game directory.    What next?

---

### Post by davew_tx on 2007-12-15
OK,  not working on a couple of ISpy games for the boys.

Make the iso image using dd terminal command.
Gmount the iso on /media/cdrom0
enter mount, use the setup.exe (have removed the physical disc at this point)

the resulting installation is under wine, and prompts me for the disc still.

Any other ideas?

---

### Post by anjilslaire on 2007-12-15
Get a no-cd crack and replace the lauch exe file (keep a backup). Somewhere like megagames.com or gamecopyworld should have them.

---

