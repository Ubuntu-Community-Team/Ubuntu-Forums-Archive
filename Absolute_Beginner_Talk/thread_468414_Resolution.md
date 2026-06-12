---
title: "Resolution?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by SuperPetRalf on 2007-06-08
I installed Ubuntu when I was using my old monitor 17" and I recently bought a new, 22" display, The resolutions now supported are alot greater, however I cannot seam to use these.

System > Preferences > Screen Resolution

Only shows upto 1024 x 768, however I know the new monitor can go past this, anyway to do this.
Ive got the correct graphics drivers installed.

Thank you in advance,

One hopelessly lost Student, SuperPetRalf.

---

### Post by racoq on 2007-06-08
open terminal and type the following command

sudo dpkg-reconfigure xserver-xorg

you can accept defaults drivers that are selected until you get to the setup of the monitor section, there you will be able to select your resolution,

hope it helps

---

### Post by Ricbuntu on 2007-06-09
Like most, I'm a first time user of Ubuntu (or any other Linux distro). I freshly installed 7.04 on my existing XP box (as a dual boot system), and encountered the same screen res issue. 

I followed racoq's advice (thank you!) and stepped through each of the xserver screens accepting the default values *most* of the time. I'd advise anyone inexperienced with Ubuntu to read each of the screens, because some may warrant the selection of the non-default option. Rule of thumb would be that, if you don't know the right selection, go with the default.

When I arrived at the screen monitor setup, I simply selected 1280x1024 as one of the options. After the xserver config program is done, close the terminal, and [restart your machine. When Ubuntu starts up again, it should automatically be running on the highest resolution you selected previously.

One final note. During the xserver config, I found at certain screens pressing Enter would not progress you to the next screen. Instead, pressing Esc worked fine for me.

---

