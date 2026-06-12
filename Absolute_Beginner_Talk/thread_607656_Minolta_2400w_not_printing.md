---
title: "Minolta 2400w not printing"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mlrustich on 2007-11-09
Hi anyone

I am new to Ubuntu, and wanting to kick XP out of my life, but I just can not get my Konica Minolta 2400w to print on 7.10, I have installed the m2300w driver and changed *Manufacturer:	"MINOLTA", re-installed printer. 

I keep getting the message in print status as print STOPPED. Being new at this, were do I go from here?

My epson R210 worked as soon as I put it into the USB, but it doesn't print as fast, as cheap and as good as the konica laser.

help

Mick:confused:

---

### Post by Dripbagulhos on 2007-11-09
Hi mlrustich,

Have you already pinted to [http://localhost:631/](http://localhost:631/) ?

Check in the last tab: Printers. See if you can start your printer there and if you are able to send a test page. If not, try to remove it from cups (there, in the browser interface) and re-install it from cups.

Let me know what happend.

---

### Post by mlrustich on 2007-11-10
Hi

thanks for getting back to me about this problem so soon, I did as you instructed and got this error message

"/usr/lib/cups/filter/foomatic-rip failed"

If you can help that would great

cheers
Mick

---

### Post by Dripbagulhos on 2007-11-11
> **mlrustich said:**
> Hi

thanks for getting back to me about this problem so soon, I did as you instructed and got this error message

"/usr/lib/cups/filter/foomatic-rip failed"

If you can help that would great

cheers
Mick

Hi mlrustich!

CHeck this topic: [http://www.linuxforums.org/forum/redhat-fedora-linux-help/70814-printing-problems.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/70814-printing-problems.html)


In short there are two things you can do: the first suggestion is:

```
sudo foomatic-cleanupdrivers

```

And the second one is about the .ppd (similart to a printer driver in windows) you are using. On this page there is a link for a ppd:

[http://orion.laylalawlor.com/software/min00/](http://orion.laylalawlor.com/software/min00/)

The direct links:

[http://orion.laylalawlor.com/software/min00/min00_v0.9.tgz](http://orion.laylalawlor.com/software/min00/min00_v0.9.tgz)

Hope this solve your problem!! :-)

---

