---
title: "Tripleboot OSX Win7 Ubuntu Oneiric"
date: 2011-11-28
forum: Apple Hardware Users
---

### Post by paulinchen on 2011-11-28
On my MacBookPro 5.5 I would like to install Oneiric, Windows 7 and Osx. Following different website guides, I figured out one problem: Since 11.04 it's not possible anymore to install Grub directly on the Ubuntu partition via the Advanced Menu. And I didn't managed it to change this correctly afterwards. Neither with grub-install --force nor with boot-repair.

Sure, I could just install every OS after the other, but this would let Grub also handle Windows 7, which is really annoying, choose Win7 first via Refit and again in Grub.

Is there anyway to fix this, so I could boot every OS directly in Refit?

Thanks in Advance

---

### Post by enochpc on 2011-11-28
You could install 10.10, which does allow to install Grub directly on the Ubuntu partition, then upgrade up.  That's how my quad boot works. Using Chameleon as the main boot loader (it's a hackintosh)  I currently can boot OSX 10.6.8, 10.7, Windows 8 Developer preview, and 11.11 Ubuntu.

---

### Post by paulinchen on 2011-11-30
Seems like a timespending job, install first 10.10 and afterwwards upgrade first to 11.04 and afterwards to 11.10.

Isn't there an easier way? I mean after reinstall grub with boot-repair on the linux partition, I can see  it's definitely there, but it's not booting.

---

### Post by Dr. McKay on 2011-11-30
Don't know if it's related, but I had a Grub error after having installed Ubuntu on my mac with refit (only dual boot with SL, though). 
Have you tried running the Ubuntu Oneiric installer from the live cd again, but this time choosing the  "upgrade ubuntu" option ? That did the trick for me...

---

