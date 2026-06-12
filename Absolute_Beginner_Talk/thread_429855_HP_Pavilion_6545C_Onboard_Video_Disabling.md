---
title: "HP Pavilion 6545C Onboard Video Disabling"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Uranium235 on 2007-05-01
Anyone know how this is done.  My alternate low end PC is this pavilion 6545C with crappy on-board video, and I want to install my neato high-speed Nvideo Gforce MX4400. :)

---

### Post by Uranium235 on 2007-05-01
*bump*

How do I sisable it in the ubuntu "device manager"?

---

### Post by dfreer on 2007-05-01
Should be an option in BIOS if it doesn't do it automatically. Have you tried to just plug in your new card and see if it is automatically changed to default video card? At very worst, there might be a jumper you have to switch on the motherboard but I haven't see one of those since like P2-P3's motherboards.

---

### Post by dfreer on 2007-05-01
you shouldn't need to do it in ubuntu at all, it should be disabled before ubuntu even sees it.

---

### Post by Uranium235 on 2007-05-01
The bios has a video option, but it won't allow me to disable it.  Now I can plug the thing in and get text mode all day long, but when I start up Gnome, nothing.  That's where the hangup is and that's why I need it disabled in Ubuntu.

---

### Post by dfreer on 2007-05-02
hmmm. so you plug in your card, and you can reach the CLI with the new card? then your problem is that ubuntu isn't reading your video card correctly. try a
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure X to recognize your new video card.

---

### Post by Uranium235 on 2007-05-02
Is it possible that my motherboard may not support a 128mb card?

---

### Post by dfreer on 2007-05-02
the memory size shouldn't make a difference in terms of Motherboard support, however, the card interface may (there are several different speeds of AGP, plus PCI and PCI-Express to worry about). Generally, if it fits in the slot it should work but... you never know. Try using a live CD with the card plugged in: If it works then your desktop should as well, the only question then is how to configure it. You could copy the contents of /etc/X11/xorg.conf from the Live CD if you get it working with that, and copy it into your hard drive's /etc/X11/xorg.conf

---

### Post by Uranium235 on 2007-05-02
It doesn't work on the live CD either and per the information I'm getting from HP, when I plug the card into the slot, I should get an options in the bios video boot tab for PCI, but it doesn't come up, so I'm guessing the motherboard can't communicate with that particular card.

---

### Post by dfreer on 2007-05-02
can you get a refund for that card, try a different one perhaps?

---

