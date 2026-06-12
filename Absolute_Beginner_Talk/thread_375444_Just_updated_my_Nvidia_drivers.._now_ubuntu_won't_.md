---
title: "Just updated my Nvidia drivers.. now ubuntu won't boot"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Spartan22x on 2007-03-03
Okay.. so I just installed the drivers for my GeForce 6800 on my linux partition using the .run file from their site, and now when I restart it's not booting Xserver at all, and it's saying that the Xserver kernel version is different (it's higher) than the Nvidia kernel version, so it basically just stops and leaves me at a black screen with a flashing cursor (which doesn't seem to do anything.. it doesn't seem to be the console)... I'm new to linux, and this has me.. stumped to be quite honest. Any help would be appreciated.

---

### Post by Phantom784 on 2007-03-03
Try running "sudo dpkg-reconfigure xserver-xorg" (without quotes) in the command line.  This will make X reconfigure itsself and will hopefully get you into graphical mode again.

---

### Post by Spartan22x on 2007-03-03
> **Phantom784 said:**
> Try running "sudo dpkg-reconfigure xserver-xorg" (without quotes) in the command line.  This will make X reconfigure itsself and will hopefully get you into graphical mode again.

How can I get to the command line while booting?

---

