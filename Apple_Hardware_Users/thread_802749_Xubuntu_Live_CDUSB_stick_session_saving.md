---
title: "Xubuntu Live CD/USB stick session saving"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by Falkenad on 2008-05-21
So I managed to revive an old iMac DV G3 with a xubuntu 6.10 desktop CD. I had to modify xorg.conf disable DRI and modify horizon sync/vertical refresh rates to get the display to work.  Thing is, I don't want to deal with this every time I boot- I'm using a live cd because I don't want to touch the hard drive and keep the os 9(strange, I know).  How can I save my settings/desktop to a USB stick so that I don't have to go through that everytime?
That is my foremost question, I'm very new to linux so the an idiot-proof explanation would be greatly appreciated.  And a smaller question, not my first concern- adobe has no flash support for us, but I've heard good things about Gnash.Again this isn't as important as the first question, but any pointers on that?

---

### Post by stream303 on 2008-05-22
What you are looking for is the "persistent" mode that uses "casper cow".  Really. :)

I haven't tried it personally, but I think you have to specially format your usb thumbdrive, rather than just leaving it in it's native format.

I did a quick read about it here:

[https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence)

Anyone try this already?  Wonder if it is supported on ppc?

---

### Post by Falkenad on 2008-05-22
Yes, I've heard a little bit about casper-cow.. supposedly you're supposed to use casper-rw instead, requiring a specially formatted USB key. shouldn't be too difficult, but that remains to be seen until I actually get another USB stick to use.

---

### Post by Falkenad on 2008-05-25
I tried Casper-rw, but I don't know how to get it to boot from the text based boot loader because everytime I do I have to go through changing xorg.conf a bunch, and I want to bypass that...

---

