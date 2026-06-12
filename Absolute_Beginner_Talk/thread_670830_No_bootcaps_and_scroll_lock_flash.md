---
title: "No boot/caps and scroll lock flash"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by jimsheep on 2008-01-17
ok, so after a power outage, all of the hardware in the house is fine except for my ubuntu box.  i try to boot to ubuntu 7.10 and get as far as the boot menu.  i choose anything on that list and get an error 15 file not found.  ok, fine.  i throw in the live cd and try to choose anything from the loader menu on that.  it looks like it will load, it loads linux, and then the screen hits standby and i get the caps/scroll flash.  i don't want to have to reformat both of my drives, though.  what can i do?

SYSTEM CONFIGURATION:

Asus A8N-E with AMD 3500+ 64-bit, Radeon X800, 2GB RAM, 80GB SATA drive, 160GB IDE drive and 160GB USB drive.

---

### Post by Dynaflow on 2008-01-18
Supposedly, that error means that everything is okay, but your kernel is not where (a possibly-corrupted) GRUB thinks it is: [http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/]("http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/").

Have you tried [Knoppix]("http://www.knoppix.org")'s liveCD to try to make the computer boot?  That's what I usually use to get into majorly screwed systems to do repairs.  It's made for situations like that.

There's a possibility that your hardware may have been damaged by a power surge too, so if you can't at least boot into a shell, you may want to transplant those hard drives into another machine to see if you can evacuate your data from them before you try a complete reformatting and reinstallation.

---

### Post by jimsheep on 2008-01-18
ok, knoppix worked to get my hardware running.  can i repair grub from there?  if so, can i copy it from the 7.10 disk?  that thread you posted let me verify that the kernels are still in the /boot folder, but i don't know what to do next!

---

### Post by Dynaflow on 2008-01-18
You can do it from Knoppix's terminal [like this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4").

However, since I just ran across this yesterday and am curious to see if it works, I'd recommend trying the  [Super Grub]("http://forjamari.linex.org/projects/supergrub/") liveCD.  Apparently you boot from it, select a language, tell it "Linux," select "Fix Boot of Linux (GRUB)" and whatever installation you're trying to restore, and *poof*, all is well in GRUB Land when you reboot.

If it doesn't work, just follow the instructions included in the first link.

---

### Post by jimsheep on 2008-01-19
superGRUB worked like a charm!  i selected linux, then the install, and it took less than 5 seconds to fix it and boot to my HDD!  thanks for your timely help.

---

### Post by jimsheep on 2008-02-04
ok, so super grub didn't work all the way...i'm getting error 15 whenever i boot without the SG cd.  i ran through the disk with help, and it still can't seem to boot.

if i boot from SG everything works great.

---

### Post by Dynaflow on 2008-02-04
Try reinstalling GRUB from Knoppix, then, with the instructions linked to above.

---

