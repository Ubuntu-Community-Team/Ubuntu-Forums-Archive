---
title: "System info in Feisty Fawn 7.04"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-08-08
How can I look at my sistem information in Feisty Fawn 7.04? System>Preferences>Hardware Information doesn't help much. Basically, I want to see what wireless card do I have; BTW I just bought a Dell Inspiron 1501 and everything's working fine so far, except the wireless which I can't seem to install even though I've tried two guides already.

---

### Post by igknighted on 2007-08-08
> **Baby Boy said:**
> How can I look at my sistem information in Feisty Fawn 7.04? System>Preferences>Hardware Information doesn't help much. Basically, I want to see what wireless card do I have; BTW I just bought a Dell Inspiron 1501 and everything's working fine so far, except the wireless which I can't seem to install even though I've tried two guides already.

Try the command 'lspci' in the terminal.  It will give you info about anything connected via a PCI bridge.  Also, try the commands 'ifconfig' and 'iwconfig' for info on network adapters.

---

### Post by Baby Boy on 2007-08-08
Thanks, the 'lspci' worked. I have a Dell Broadcom 1390 WLAN, but what's strange is that it says my GPU is Ati X200M (I get the same thing in Hardware Information from the preferences menu) which is impossible because all Inspiron 1501 models come with Ati Xpress 1150. What the heck? :confused:

---

### Post by Hospadar on 2007-08-08
I would suggest using sysinfo ```
sudo apt-get install sysinfo
```and then go to Applications->system tools->sysinfo this gives more information than than the standard hw manager.
you might also try "df" in the terminal for disk usage info

If you are trying to figure out which ati driver to install, try using envy ```
 sudo apt-get install envy
envy -t
```

This from my experience does a pretty good job of automatically installing the correct proprietary drivers.

---

### Post by Baby Boy on 2007-08-08
> **Hospadar said:**
> I would suggest using sysinfo ```
sudo apt-get install sysinfo
```and then go to Applications->system tools->sysinfo this gives more information than than the standard hw manager.
you might also try "df" in the terminal for disk usage info

Well thanks, but the system info doesn't display much more information than that 'lspci' command - the GPU is just recognized as 'Ati RS480' and there is no info on the wireless. Nevermind though, I found out what I needed already.
> If you are trying to figure out which ati driver to install, try using envy
Code:

 sudo apt-get install envy
envy -t

This from my experience does a pretty good job of automatically installing the correct proprietary drivers.
Actually, I've already installed *some* Ati driver using the restricted driver manager. Is that how you do it? And I've tried using that code you gave me, but I just get:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy

About the Ati graphic card...I think this may be why it's recognized as Ati X200M in Ubuntu (found this in Wikipedia):

> Radeon Xpress 200M

    * Radeon Xpress 200 chipset optimised for Mobile applications.
    * Includes AMD Turion 64 support.
    * Support for Unified Memory Architecture
    * **Later renamed as Radeon Xpress 1150 for AMD notebooks**


---

### Post by Rocket2DMn on 2007-08-08
try
```
sudo lshw
```
or more advanced to dump into a file like:
```
sudo lshw -html > lshw.html
```

---

### Post by corney91 on 2007-08-08
You could use a program called Hardinfo:
```
sudo apt-get install hardinfo
```

---

### Post by Baby Boy on 2007-08-08
Both of these methods are pretty neat, thanks. But my card is still recognized as Ati X200M :?!
EDIT: Apparently, it's a linux thing. Found this link after googling a bit.
[http://www.suseforums.net/index.php?showtopic=34291]("http://www.suseforums.net/index.php?showtopic=34291")

What's buggin' me is should it be recognized for what it really is? Do I have the wrong drivers or something? Any Ati Xpress 1150 users here?

---

