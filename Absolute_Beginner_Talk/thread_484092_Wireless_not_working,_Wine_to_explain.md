---
title: "Wireless not working, Wine to explain?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Josh_Lapointe on 2007-06-25
Hello Everyone. I'm quite new to (k)Ubuntu. I have a problem, and would like to know if anyone could help. Well, it goes like this I just recently installed a new D-Link Wireless Adapter into my Ubuntu/Xp Computer and everything went fine, and was working properly on Ubuntu, then i updated all my programs, and got the new Fiesty Fawn update, and installed Wine also. After Wine was done installing, i installed Starcraft. Worked great, was happy tried to get on Battlenet, and it then froze. After this happened. I shut it down, because it quite distorted my kde (Icons larger, screen resolution smaller...ect) and once i rebooted my wireless network adapter is no where to be found. It is there physically, and computer recognizes it, but it just doesn't have the connection that would normally start up at the beginning. I know this is a quite newbish question, but hey isn't this what the tread is for :P. 

Thanks alot ahead of time guys.

---

### Post by cam_tram on 2007-06-25
I don't think Wine directly accesses any of your network hardware, so I don't think it could be that.  When you reboot your computer, does the network interface even appear?  If not, you may just need to modprobe your hardware.

For example, if your using ndiswrapper:
```

sudo modprobe ndiswrapper

```

---

### Post by Josh_Lapointe on 2007-06-25
Hmm, I don't know man.. Just recently when i restarted my Linux, it worked. :P If it bugs up again, i'll check that.

Thanks though.

---

### Post by Seisen on 2007-06-25
I know when I had a Dlink wireless card it had worked here and there until I used ndiswrapper and it worked just like a ethernet card would.

---

