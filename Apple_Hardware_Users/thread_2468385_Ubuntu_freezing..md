---
title: "Ubuntu freezing."
date: 2021-10-27
forum: Apple Hardware Users
---

### Post by catacombs38 on 2021-10-27
I have installed Ubuntu20.04.03 desktop-amd.64 , minimal install, onto a mid 2009 Mac Book Pro 17 inch.  I used a WiFi Dongle to allow it online during install.  And the only thing on SSD is Ubuntu.  I did the first updates.  Seems to freeze while doing things online, only allowing me to move around cursor, and doing that better with a USB mouse.  

I suspect part of this is related to WiFi, and some auto updates feature.

I understand the part about not trying to use Firefox.  It says use Chromium, which to me translates to Google Chrome.   

The thing goes off refusing to do anything for long periods.   Leading to a hard Power Off.  Not helpful to the further cause of using Ubuntu.

Is there a good way to be sure Ubuntu is 'functional'  after I did a hard power off, except to reinstall.  

I only need this for a short project.   I hate to spend hours just trying things.   My project requires either Debian or a Derivative.  Ubuntu grades high on this.  Perhaps I messed up by not specifying that I must login at the beginning.  Or that I let it install Ubuntu rather than specifying Ubuntu64.   Or I might try another Dongle, this one might be getting old. 

Instructions about holding down keys to get out of freeze doesn't relate to keys I have.   Be nice if Ubuntu told me what it was doing, while not allowing me to do anything else.   That it is not permanently frozen.   

Thanks for any advice

---

### Post by vmpx on 2021-10-27
**How to fix Ubuntu 18.04 freeze after boot when NVIDIA card installed**

Replace in GRUB menu for 18.04 ”quiet splash” with ”quiet splash   nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)
After that freeze should be gone.

---

