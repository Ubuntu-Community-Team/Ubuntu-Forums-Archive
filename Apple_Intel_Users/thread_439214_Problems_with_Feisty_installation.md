---
title: "Problems with Feisty installation"
date: 2007-05-10
forum: Apple Intel Users
---

### Post by the.dark.lord on 2007-05-10
I just burned a CD of Feisty Fawn, and tried to install it on my Intel iMac, when I start the live CD, it just loads the linux kernel up to 100%, and freezes. I even tried the 64 bit version - resulting in the same problem.

Help please!

---

### Post by liberalist on 2007-05-10
I have trouble with my iMac with Intel Core 2 Duo processor as well. It starts and loads Xubuntu 7.04 (Feisty Fawn) and then I get an error message about the X server. So I cannot boot Xubuntu as a Live CD.

---

### Post by ronocdh on 2007-05-10
> **liberalist said:**
> I have trouble with my iMac with Intel Core 2 Duo processor as well. It starts and loads Xubuntu 7.04 (Feisty Fawn) and then I get an error message about the X server. So I cannot boot Xubuntu as a Live CD.
See the link in my sig.

---

### Post by ronocdh on 2007-05-10
> **the.dark.lord said:**
> I just burned a CD of Feisty Fawn, and tried to install it on my Intel iMac, when I start the live CD, it just loads the linux kernel up to 100%, and freezes. I even tried the 64 bit version - resulting in the same problem.

Help please!
This sounds like a bad disc creation error. Try verifying the checksum via the main screen of the live CD boot screen ("check integrity" or something, the option is called). Also, create the disc using a program like **Burn**, available from [here]("http://www.opensourcemac.org"). It automatically verifies the integrity of the disc immediately after creation.

---

### Post by liberalist on 2007-05-10
Thank you very much, ronocdh. Will this issue be fixed in a later release of Ubuntu and its deratives (for instance 7.10 Gutsy Gibbon)?

---

### Post by benanzo on 2007-05-10
the xserver bug is being evaluated upstream by the xorg people.  It affects not just Ubuntu.  I imagine a patch to the xserver will be released soon, then Ubuntu will incorporate it.  We might see a 7.04.1 with the patch.  If not, Gutsy will have it.

---

### Post by russo.mic on 2007-05-10
All you have to do to install Feisty under Macbook C2D is 

sudo apt-get xorg-driver-fglrx
sudo aticonfig --initial
startx

you'll pop right into your live desktop!

---

### Post by Lt_Data on 2007-05-10
Ronocdh to the rescue again!

---

### Post by the.dark.lord on 2007-05-11
> **ronocdh said:**
> This sounds like a bad disc creation error. Try verifying the checksum via the main screen of the live CD boot screen ("check integrity" or something, the option is called). Also, create the disc using a program like **Burn**, available from [here]("http://www.opensourcemac.org"). It automatically verifies the integrity of the disc immediately after creation.

Thanks. It happens that my CD had a problem, I installed Ubuntu 64 bit 7.04 with a new CD :). I'm writing this on Ubuntu. Woohoo.

But, I have plenty of problems with this now. No sound, many applications do not work. I read many people here having the same problem with sound, but I could not find a solution here. When I start  Ubuntu an error comes saying: 
> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Message did not receive a reply (timeout by message bus)

GNOME will still try to restart the Settings Daemon next time you log in.

Many applications like GAIM do not work. The default theme is blue [KDE???] instead of orange- this is Ubuntu not Kubuntu.   It seems there is an error in GNOME.  Help again. Thanks.

Other than these problems, I'm highly impressed with Ubuntu :KS

---

### Post by the.dark.lord on 2007-05-12
Is my problem *that* bad?????!!!!!!!

---

### Post by the.dark.lord on 2007-05-12
UPDATE: I recieved my ShipIt CDs today, and installed Feisty using it.
And, I have everything working now. Woohoo.

---

