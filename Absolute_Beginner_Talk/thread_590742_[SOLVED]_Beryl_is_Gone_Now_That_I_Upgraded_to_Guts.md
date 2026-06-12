---
title: "[SOLVED] Beryl is Gone Now That I Upgraded to Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-25
I just upgraded to Gutsy yesterday and it seems to be working nice.    My problem is that Beryl is no longer working.  It took me a while to get it working with Fiesty and I'm not even sure how I was actually successful.  i have an ATI graphics card dammit and wanted to find out if Gutsy can handle ATI video cards better or is it still an issue with proprietary drivers not being open source.  Any help or advice will be appreciated.  

Thanks in advance,

VC

---

### Post by magicman5421 on 2007-10-25
you shouldn't have a problem getting your ati card to run nice with ubuntu. and u know that ubuntu 7.10 has compiz fusion built in which does similar things as beryl does. worst comes to worst, u can just use compiz (which btw is actually pretty nice).

---

### Post by FredB on 2007-10-25
> **videocheez said:**
> I just upgraded to Gutsy yesterday and it seems to be working nice.    My problem is that Beryl is no longer working.  

Beryl is DEAD ! Now, it is Compiz Fusion.

> It took me a while to get it working with Fiesty and I'm not even sure how I was actually successful.  i have an ATI graphics card dammit and wanted to find out if Gutsy can handle ATI video cards better or is it still an issue with proprietary drivers not being open source.  Any help or advice will be appreciated.  

Thanks in advance,

VC

ATI cards are really a pita. But it seems that new generation of ATI drivers will understand AIGLX (at least !)

For now, try to install drivers from restricted manager tool.

---

### Post by videocheez on 2007-10-25
> **magicman5421 said:**
> you shouldn't have a problem getting your ati card to run nice with ubuntu. and u know that ubuntu 7.10 has compiz fusion built in which does similar things as beryl does. worst comes to worst, u can just use compiz (which btw is actually pretty nice).

How do I get this compiz fusion working?  I need some eye candy.

---

### Post by FredB on 2007-10-25
> **videocheez said:**
> How do I get this compiz fusion working?  I need some eye candy.

if you have 3D enabled drivers, you will just have to reboot. Compiz will load. 

Go to  System /  Preferences / Appearance.

Install after that Compiz Config Settings Manager if you want to tweak effects after that.

---

### Post by videocheez on 2007-10-25
Thanks man.  It seems to be working.  Can I uninstall the emerald theme manger now that i'm using compiz?

---

### Post by geeree on 2007-10-25
> **videocheez said:**
> It seems to be working.  Can I uninstall the emerald theme manger now that i'm using compiz?

Compiz Config Settings Manager will let you change window management settings. But you will need Emerald if you want to have various themes the way you must have had them in Beryl. But beware, Emerald is having some new problems in installing themes: 

[http://ubuntuforums.org/showthread.php?t=588086](http://ubuntuforums.org/showthread.php?t=588086)

I'm not sure if there are any other theme managers for Compiz.

Girish.

---

### Post by videocheez on 2007-10-25
thanks for the tips.:popcorn:

---

### Post by nikky on 2007-10-25
Hello to all
I have a X600 mobility ati and aiglx is working with open source driver
But I cannot start compiz because my chip is in blacklisted chip section of 
the bash script /usr/bin/compiz. (at the top of the script)

But with another script from my feisty installation compiz start correctly
(i simply copy the script from old /usr/bin/compiz to something like /usr/bin/compiz-old) and
started it and it works!!!!!

but

why my chip is in blacklisted chip list?

Thaks

---

