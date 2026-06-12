---
title: "Setting up to use wireless USB adapter?"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2005-06-05
Okay so I just (finally) fought my crappy old PC back into submission and installed Ubuntu (last version of Warty) on it. Since I don't want to run TWO cables into the den if I don't have to, I thought I would be able to use a motorolla wirelss USB adapter to connect to the wireless router in the den. How do I go about setting this up?


Also, I have a hauppage win TV go in this system and I'm wondering how I'd set that up and what you all recommend for watching and recording broadcasts.

Thankx guyz.

---

### Post by briguy on 2005-06-06
Have you tried installing atmelwlandriver-tools package?  I haven't tried it but found it while looking for something else.  It's supposed to be drivers for USB wireless adaptors.

---

### Post by TheAnonymousx on 2005-06-06
Okay I'll give that a try, but I realize something.

I was about to switch over to the other system and do apt get install  <package> when I realized the problem, first and foremost is that I don't have internet access. Is there some other way to install the packages on the system?I guess I could temporarily steal the one from my windows box, but I don't wanna rely on that as a crutch if I get into a situation where I HAVE to install a package w/o internet use.

---

### Post by TheAnonymousx on 2005-06-07
Hmm, okay I run the program and attempt to install and it hangs up. I'm doing this:

gzip -cd home/name/temp/patch-atmel_reste.gz | patch -p1

But it doesn't seem to be able to "find the file to patch." The path I input is indeed the location of the file of the utlities that I need, but I can't seem to open it. I'm taking suggestions for how to get this thing to work outside of these drivers. For the most part, being wired in isn't an option.

---

### Post by Jussi Kukkonen on 2005-06-07
I really don't know if those atmel patches work for motorola devices, but in general I believe you should look at either linux-wlan-ng (for adapters with the prism2 chip, see [README](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README)) or ndiswrapper (see [list of supported cards](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List)).

[edit:]
I checked the list of supported devices for atmelwlan, and there are no Motorolas there.

---

