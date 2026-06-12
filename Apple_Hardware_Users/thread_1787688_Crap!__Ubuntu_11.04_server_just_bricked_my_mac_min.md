---
title: "Crap!  Ubuntu 11.04 server just bricked my mac mini!"
date: 2011-06-21
forum: Apple Hardware Users
---

### Post by gharris999 on 2011-06-21
OK, I don't think I really knew what I was doing when I tried to install 11.04 server to dual boot on my 2007 intel mac-mini.  But the system now seems totally bricked!  Using a wired usb mac keyboard, the option key won't bring up a boot menu, pressing C won't boot the system from the snow leopard disk, there doesn't even appear to be a way to eject the snow leopard dvd!!!

All that I get is the "bong" boot sound, the gray screen followed by a back screen and a blinking cursor no matter what key combination I hold down on the keyboard.

What's going on here?!?!?!?!

---

### Post by Maheriano on 2011-06-21
There are a few key combinations that will work, I think if you hold the mouse while it's booting, it'll eject the CD.

Google.

---

### Post by gharris999 on 2011-06-21
> **Maheriano said:**
> There are a few key combinations that will work, I think if you hold the mouse while it's booting, it'll eject the CD.

Google.
Yes, I just managed to eject the CD that way.  But no boot menu when holding down the option key?  WTF???

---

### Post by gharris999 on 2011-06-21
OK, after looking at this blog post: [http://reprocessed.org/blog/ubuntu_on_mac_mini](http://reprocessed.org/blog/ubuntu_on_mac_mini)

..I suspect that my problem is that key mac keyboard I'm using is too new for this 2007 era mac mini.  I'll try to find an older keyboard and see if that allows me to boot from the DVD.

---

### Post by kerry_s on 2011-06-21
So you have ubuntu on there now? 
If so, try holding the shift key to get to grub menu.

---

### Post by gharris999 on 2011-06-21
> **kerry_s said:**
> So you have ubuntu on there now? 
If so, try holding the shift key to get to grub menu.
I need to find an older mac keyboard first.  None (!) of the boot-option key combinations work with the keyboard I've got here now.

---

### Post by Maheriano on 2011-06-21
I think you're misunderstanding the definition of bricked.

---

### Post by gharris999 on 2011-06-21
> **Maheriano said:**
> I think you're misunderstanding the definition of bricked.
No, I understand what a brick is. I was just dead wrong about the bricking.  If I can edit the title of this thread, I will.  So please take this as an official mea culpa.

It was all down to the keyboard.  The nice shiny brushed aluminum mac keyboard is useless for invoking the boot menu on this era mac-mini.  My brother-in-law managed to find two old mac keyboards in a closet at work (he had to promise to NOT return them) and that got me back into OSX.  Reinstalling rEFit got me a usable boot menu and into GRUB2 and now Ubuntu Server is humming right along.

Again, mea culpa, mea maxima culpa.

---

