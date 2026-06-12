---
title: "Compiz on Intel iMac 20&quot; Aluminium"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by piroco on 2007-10-21
Hi people,

Fairly new to Linux (used it a few years back, forgotten most of the CLI magic) and installing Ubuntu 7.10 on my iMac 20" Aluminium which is a Dual-Core 2.4Ghz with an ATI Radeon 2600 HD card. 

Managed to get the wireless to work after picking up tips from the forums here (I used ndiswrapper and it works like a charm) -- however, still no luck getting Compiz to work.

I tried this approach: 

[http://ubuntuforums.org/showthread.php?t=579892](http://ubuntuforums.org/showthread.php?t=579892)

In short - use the "Restricted Drivers Manager" to install the ATI (fglrx) driver. 
My problem is, the Restricted Drivers Manager tells me "Your system does not need any restricted drivers" - then exits.

I tried downloading the newest ATI drivers from the ATI website, and managed to get it to work. I.e. I managed to access the ATI control tab, managed to set up dual-screen, it seemed to work pretty well. But still no Compiz!

I've installed AIGLX - at least so I think - but to no avail.

I know others have had problems too, so if there's someone out there with a similar setup to mine who has been able to get Compiz to work on iMac with an ATI 2600 HD card, I would very much appreciate a dummy run-through.

Thanks for all the other great tips I've been able to pick up on the forums.

Best
P

---

### Post by cyberdork33 on 2007-10-21
ATI drivers need XGL to use compiz

```
sudo aptitude install xserver-xgl
```

---

