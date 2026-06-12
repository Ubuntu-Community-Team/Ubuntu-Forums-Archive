---
title: "[SOLVED] For gods sake help me"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by TRStealthX on 2007-08-15
I've reinstalled ubuntu 6 times now due to my screen not working properly. I tried getting help by googling and a few guides around the forum, but they just didnt help at all. I have an old computer at home that I'm running ubuntu on, and it has an ATi Radeon xpress 200 graphics card. I don't know whats wrong but my screen resolution is not correctly detected and the display looks horrible. 

I ran the xorg setup again and that just made the problem a lot worse. Now when I start everything up the screen doesn't even turn on. Please guys, help me find a way of getting my 1280x1024 display back up, I want to keep using Ubuntu, but I can't do it with such a bad display. If I need to reinstall the whole OS again, thats fine. Just help me out.

Thanks,
StealthX

---

### Post by olejorgen on 2007-08-15
Could you post your /etc/X11/xorg.conf ?

Sometimes you need to add the modes manually

---

### Post by bodhi.zazen on 2007-08-15
I think you might try installing the ATI driver :

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by ubuntuforums on 2007-08-15
Get Envy and see if that can install proper graphics drivers for your card.  :)

---

### Post by TRStealthX on 2007-08-15
> **olejorgen said:**
> Could you post your /etc/X11/xorg.conf ?

Sometimes you need to add the modes manually

The screen is not showing up at all. Id have to reinstall the whole OS.

---

### Post by bodhi.zazen on 2007-08-15
Hit Ctrl-Alt-F1 to get to a terminal (I hope)

you might need Ctrl-Alt-F2

---

### Post by olejorgen on 2007-08-15
If you've done tons of stuff trying to fix it, I'd recommend to reinstall, and post your xorg.conf (++)

You can do this even if you haven't got X running, but then you'd have to use lynx / usb stick etc to get the output posted.

---

### Post by HermanAB on 2007-08-15
The vesa driver is guaranteed to work.  That is the one used during the install process.

---

### Post by defconoii on 2007-08-15
why dont u install xubuntu, its ubuntu with xfce for low ram systems, feisty 7.04 has better support for such problems
[www.xubuntu.com](www.xubuntu.com)

---

### Post by TRStealthX on 2007-08-15
> **bodhi.zazen said:**
> I think you might try installing the ATI driver :

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Thank you very much. I got everything running fine now :D.

---

### Post by Hobo Joe on 2007-08-15
> **ubuntuforums said:**
> Get Envy and see if that can install proper graphics drivers for your card.  :)

Amen. I've heard so many people say that they couldn't get the graphics drivers working no matter how many guides they took, and then Envy fixed it.

There is a link in my sig.

---

### Post by TRStealthX on 2007-08-15
> **Hobo Joe said:**
> Amen. I've heard so many people say that they couldn't get the graphics drivers working no matter how many guides they took, and then Envy fixed it.

There is a link in my sig.

I didn't get envy. I went through the ATi wiki... xD

---

### Post by Hobo Joe on 2007-08-15
> **TRStealthX said:**
> I didn't get envy. I went through the ATi wiki... xD

Envy is still better.

I'm not kidding.

---

### Post by A-Sylum on 2007-08-15
Is envy an actual driver or does it set up a driver for you?

---

### Post by Hobo Joe on 2007-08-15
> **A-Sylum said:**
> Is envy an actual driver or does it set up a driver for you?

It downloads your drivers, installs them, and configures your xserver/xorg all with 2 presses of the mouse. Literally.

It also has a knack for working when nothing else will.

---

### Post by A-Sylum on 2007-08-15
wow thats useful :D (especially the last part)!!! Does it work on old ATI cards? i have one coming in the mail.

---

### Post by olejorgen on 2007-08-16
> **Hobo Joe said:**
> Envy is still better.

I'm not kidding.
When I tried envy, it crashed my system so bad, that I did an reinstall. To be fair it should be mentioned that I had done a lot "experimenting", so the system wasn't exacly "fresh"

---

