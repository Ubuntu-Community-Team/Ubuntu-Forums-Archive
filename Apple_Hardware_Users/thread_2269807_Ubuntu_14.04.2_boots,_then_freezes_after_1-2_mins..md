---
title: "Ubuntu 14.04.2 boots, then freezes after 1-2 mins."
date: 2015-03-18
forum: Apple Hardware Users
---

### Post by sam119 on 2015-03-18
Ubuntu 14.04.2 installed on MacBook runnig OS X Mavericks.

The Ubuntu installation will boot and seems to behave fine but then after 1-2 minutes it freezes. Note that I can still move the mouse pointer around, but I can't click on anything and the keyboard is not responsive.

Can anyone suggest what may cause this, how to diagnose?

Thanks!

---

### Post by este.el.paz on 2015-03-18
> **sam119 said:**
> Ubuntu 14.04.2 installed on MacBook runnig OS X Mavericks.

The Ubuntu installation will boot and seems to behave fine but then after 1-2 minutes it freezes. Note that I can still move the mouse pointer around, but I can't click on anything and the keyboard is not responsive.

Can anyone suggest what may cause this, how to diagnose?

Thanks!

This may be a bug that I and others have listed on Launchpad with name like "GUI Freezes" . . . so you could search there and see if there are some solutions.    You could first try some boot parameters "nomodeset" type of options in GRUB and see if that improves the freezing issue . . . like I said, this isn't a new problem so there should be lots of threads on it, search the forum or Google and see what fits for your computer. Depending on if you have a Radeon video card, it might relate to that . .  . visit the FAQ instructions and try to set up an xorg.conf  file for your computer, it's not too difficult . . . might be more  clear on the PPC FAQ??? even though your computer is not PPC, the basics on xorg.conf file should be similar. 

If I didn't mention it in your other threads, hopefully you have checked the md5sum number for the iso; I had Xubuntu 14.04 installed on my MBPro and didn't have to do much tweaking that I recall, but it has an Nvidia video card.

e.e.p.

---

### Post by sam119 on 2015-03-23
Thanks for the lead, e.e.p.

Turns out it was the Nouveau graphics that was causing the issue. Booted in and very quickly before the screen locked I activated the nVidia third party drivers. Having a much more consistent experience since!

---

### Post by este.el.paz on 2015-03-23
> **sam119 said:**
> Thanks for the lead, e.e.p.

Turns out it was the Nouveau graphics that was causing the issue. Booted in and very quickly before the screen locked I activated the nVidia third party drivers. Having a much more consistent experience since!

Great, thanks for the follow up . . . if it holds up for awhile then you could always mark this thread as "solved."

e...

---

