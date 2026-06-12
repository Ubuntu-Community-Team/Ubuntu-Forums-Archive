---
title: "problem with Xserver and intel gma 950 on intel MacBook"
date: 2007-06-18
forum: Apple Intel Users
---

### Post by mc95078 on 2007-06-18
Hi everyone...here goes...
I' ve got ubuntu 7.0.4 installed on a MacBook 2 Duo with the classic 13.3 inch monitor...and the intel gma 950 chipset...Everything is fine, except the resolution is stuck to 1024x768 when it should have been 1280x800. I've done the dpkg-reconfigure xserver-xorg thing, also checked the xorg.conf and made sure that 1280x800 was where it should be....but nothing :( 
I read somewhere that the horizonal sync and vertical refresh setting might be the problem....Does anyone know what are the correct settings ???

---

### Post by NickFury on 2007-06-18
not sure if this will break anything or not on a regular macbook, but I have done this for many people who use the 915,945, and 950 intel chipsets..

```
 sudo apt-get install 915resolution 
```

Then restart X (ctrl + alt + bkspce)

---

### Post by mc95078 on 2007-06-18
Worked like a charm...thanks !

---

### Post by NickFury on 2007-06-18
good to know it works, my buddy is putting Feisty on his Macbook C2D tonight, now I can get his screen resolution to native.  Thanks for letting us know it worked :D

---

### Post by HUKI365 on 2007-06-20
I tried this, but only obtained:

ubuntu@ubuntu:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 915resolution

Any assistance?

---

### Post by Gen2ly on 2007-06-20
915resolution is probably in the repositories.  Look at synaptic package manager in the preferences.

---

### Post by ivesjd on 2007-06-20
You need to enable the universe repositories if they are not already, then try the code.

---

### Post by HUKI365 on 2007-06-21
I realised I'd been an idiot. I was running off the DVD, and hadn't ACTUALLY installed the OS yet. So I will do that and then try again. The probablem was I couldn't enable the repositories (gave me some error - probably related to the fact I was running of the DVD).

Thanks anyways guys. I'm really liking my Ubuntu experience so far!

---

