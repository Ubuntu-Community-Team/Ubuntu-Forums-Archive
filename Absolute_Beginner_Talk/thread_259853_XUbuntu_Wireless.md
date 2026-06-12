---
title: "XUbuntu Wireless"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by JayDSee on 2006-09-18
Hello all.

I just installed XUbuntu on my older (IBM Thinkpad 600E) laptop but the wireless pcmcia (Linksys) card was not configured - no dialogs to enter crypto key.  I had previously  installed Ubuntu and the wireless card was identified and I was asked for the encryption key – it all worked fine.  I installed XUbuntu because I read it might run better on older computers (Pentium II, 500 Mhz).

1)Is it true that Xubuntu might run faster than Ubuntu?
2)How do I run the Wireless utilities to setup my linksys card.  I presume that I will need to do this on a terminal?

---

### Post by selam on 2006-09-19
hi,

JayDSee, can you say the version of your linksys card because i have a linksys wpc11b version 4 card and i wonder whether it works with my ubuntu? does it also support xsupplicant or wpa? i also have an old laptop, dell inspiron 7500. shall i use xubuntu? 
i want to connect to internet via my wireless card with this old laptop in the university. is there anybody who can help me?
thanks.

---

### Post by JayDSee on 2006-09-19
I have a LinkSys WPC11 V3.  The problem I'm having is that the card disappears after I install XUbuntu.  The card is detected when I boot from the CD.

I read that XUbuntu would be better for older hardware.  It seems that it might be:  I've played around with applications and it seems faster that Ubuntu.  I had previously installed Ubuntu and found it irritatingly slow.

---

### Post by happy-and-lost on 2006-09-19
Once you have the card actually working, connect to t'net via ethernet and use...

```
sudo apt-get install wifi-radar
```

wifi-radar is basically a GUI app. which can store and memorise all of your WEP keys etc. :D

---

### Post by JayDSee on 2006-09-19
I should probably start a new thread but .....

Assuming that the Xfc GUI is what makes XUbuntu better (faster) for older machines, can I install Ubuntu (Gnome) and then switch ot Xfc?

If so, does anyone have experience with changing GUI's?

---

### Post by Jukey on 2006-09-19
yea, its the Xfce environment that makes it faster.

if you install ubuntu you'll have to do a sudo apt-get xubuntu-desktop

---

### Post by JayDSee on 2006-09-19
Thanks!

After a little research I found that I can run the following:

sudo apt-get install xubuntu-desktop
or 
sudo aptitude install xubuntu-desktop

Is that all?  After reboot I shoould be in Xfc?

---

### Post by D10 on 2006-09-19
When you reboot just pick what session you want to use from the GDM login screen xfce or Gnome.

---

### Post by JayDSee on 2006-09-19
Once I have the Xfc desktop can I remove Gnome?  If so, would I use the following commands?


sudo apt-get uninstall ubuntu-desktop
or
sudo aptitude uninstall ubuntu-desktop

---

### Post by orb9220 on 2006-09-19
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by JayDSee on 2006-09-20
OK.  I'm officially frustrated.  I've now gone back and installed Ubuntu thinking that the network card would be recognized.  My plan was then to switch to Xfce.  Well, the card was recognized but it will not connect to my WAP.  I can see the card with lshw and iwconfig.  iwconfig lists the wrong frequency and access point but I can't change them – says the device is busy.   

It just shouldn't be this hard?

---

### Post by JayDSee on 2006-09-23
Woo Whooo!  It worked!!

I installed Ubuntu first - this gave me access to my wireless network.  The, I installed the XUbuntu desktop.  I rebooted and choose the Xfce desktop under session on the login dialog.

I hope this helps somebody else.

---

### Post by oss_monkey on 2006-09-23
To get back on topic, I use Xubuntu almost exclusively (not that I have any choice, with the specs of my laptop --check out the sig), and when I got a wireless PCMCIA, I found this tutorial to be very helpful.

[http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101](http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101)

And yes, Wifi-Radar rocks. I tried using GTK-wifi but it didn't work, so I advocate using Wifi-Radar. :)

---

### Post by JayDSee on 2006-09-23
The problem, of course, is that you first have to have a network connection to follow the instructions listed above.  In my case, I had no network connection when I installed XUbuntu.  I had to install Ubuntu first, then insall the Xubuntu desktop.

---

### Post by speckman on 2006-10-25
i have this problem too.  i was amazed to see that little green flashing light on my pcmcia wireless card and went straight to google when the xubuntu livecd booted up.  but after installing, where is my wireless?  dont know.

so i guess it's a problem with the xubuntu dapper installer?

---

### Post by grumpymole on 2006-11-18
It seems that the live CD installs the kernel restricted modules, while a "normal" does not.  I had to *apt-get install* the restricted modules for the kernel to get the driver for my Atheros WiFi card.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

