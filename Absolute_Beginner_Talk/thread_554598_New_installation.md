---
title: "New installation"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by generious on 2007-09-19
Good morning,

Yesterday after 8 years running windoz i decided to blow it away and install ubuntu or else kubuntu haven't decided on which on yet 100% more then likely leaning towards ubuntu 7.04
So i downloaded both Iso's and burnt them to cd's compared the md5 no problems all is well.

Changed my boot order on the desktop - 
Amd 3800
Asus An32 Sli Premium
2Gb of Ram
Nvidia 7900 Gt
Benq Dvd/CDRW - LG Dvd DvdRw
7 hdds in total - 5 Sata's & 2 IDE's  
5 of them are my data disks files
1 is the backup disk full of my images ect.
Last one is a maxtor raptor 36Gb disk for the OS installation.

So double checked the first hdd is my raptor.
Inserted the ubuntu disk and select install ( Top Option ) 
Screen came up and mouse.
problem here is the text what is meant to be displayed is garbled/ pixelated messed up can't make head or tails out of it.
Rebooted and selected safe video and booted up that way, worked fine ubuntu live loaded up.
On the desktop i ran "  install unbuntu "
That completed without errors, rebooted and removed the cd's and booted of the hdd.

Text and graphics again are all garbled, pretty sure this has something do with the xconf/nvidia drivers not installed or setup correctly.

At the moment i'm downloading the alternate installation cd to do it in text mode and use vesa instead.

Anyone have any work arounds for this?

One more question with regards to the grub when i used the install ubuntu option from the Gui it tries to install grub onto the largest hdd in the system.
I got around this by removing all the disks i  didn't want to touch and it had to install grub onto the raptor that way.

Cheers 
Noobcake Generious

---

### Post by hyper_ch on 2007-09-19
you could boot into command line and manually edit the /etc/X11/xorg.conf and change the driver there to vesa...

or manually boot into the command line and run this:
```

sudo dpkt-reconfigure xserver-xorg

```

Then you can select vesa, boot back into ubuntu gui and let the restricted driver manager install the appropriate drivers.

---

### Post by generious on 2007-09-19
Many thanks for your speedy reply hyper_ch, i will give that a try later on today when i get home from work :)
and post back to let you know how that went.

Cheers
generious

---

