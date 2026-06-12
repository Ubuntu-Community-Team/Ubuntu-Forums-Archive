---
title: "Ie"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by realtydog1 on 2007-02-28
In my new job they require IE as the browser.  Can I use this with ubuntu which I am about to install on my laptop?  I have become completely over and under-whelmed with the windows system and want to use ubuntu on the new hard drive I am installing on my laptop.  My work site absolutely wil not work unless I have IE or some way to fool it.

---

### Post by userundefine on 2007-02-28
Try changing the user agent string of a different browser like Firefox or Opera to IE.  Then test the site.  If it works, no need for IE itself.  If not, you can either install IE through wine, or install Windows inside a virtual machine on Linux and use it through there.  Either way, they're both relatively easy to set up and this shouldn't be a problem for you.

---

### Post by szf on 2007-02-28
> **realtydog1 said:**
> In my new job they require IE as the browser. I feel your pain. As things go ( you know what they say about poop and mushrooms), you'll prolly not skate by with the "Agent" trick...

---

### Post by aysiu on 2007-02-28
I would also vouch for the User Agent Switcher extension.

If you must use IE, this may help:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by Praill on 2007-02-28
If you have trouble with the above suggestion using wine, you can always install a small copy of Windows on a virtual drive using an emulator. 
That way you could run other work related Windows apps in the emulation screen without dual booting. I would recommend [VirtualBox]("http://www.virtualbox.org/") for this.

Either way should work, its up to you.

Good luck.

---

### Post by jerrynewt on 2007-02-28
This may be a little off post but would VirtualBox work with my Sony Ericsson GC89 broadband card? It doesn't support linux and can't seem to get it to work at all in linux as yet.

---

### Post by Praill on 2007-03-01
> **jerrynewt said:**
> This may be a little off post but would VirtualBox work with my Sony Ericsson GC89 broadband card? It doesn't support linux and can't seem to get it to work at all in linux as yet.

Unfortunately not.
VirtualBox is simply an emulator that* emulates* your current hardware configuration into another OS.
So any hardware that doesnt work on the host os, wont work in the guest. :(

---

### Post by J11Gyro on 2007-03-01
I have been looking into the same and not sure if this will work or not but here is a link. opinions please [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

---

### Post by luke411 on 2007-03-01
The only reason that I mention this is because it works. Some people will frown on using this type of program on linux but the reality is the system has to work for you. Also, I have used this program for years and it does everything they promise it will. You can read about it and consider buying it at [http://www.codeweavers.com/](http://www.codeweavers.com/). I think the last time I looked the program runs about $40.00. It installs easily and will run IE and other windblows software easily.

Having said that, you might find that Opera works for you. I too have a web page that 'must' have IE but discovered that Opera will run many of the ActiveX controls that IE will. You may get buy just by trying it. IF not, there is always Crossover Office and then you can screw MS by running it on a real OS and still get your work done, all at the same time. 

Good luck.

---

### Post by Praill on 2007-03-03
I dont think anyone frowns upon using Crossover. The people at Crossover are awesome. They are the same people that give us wine :).

---

### Post by Praill on 2007-03-13
BTW, I have come across a neat little project.
[http://www.ies4linux.org]("http://www.ies4linux.org").
Yep, its exactly what the domain name suggests: Internet explorer clones (from version 5 and up) for linux. I installed IE6 on my edgy distro and browsed to a couple sites I knew of that required the IE browser, they worked fine.

---

