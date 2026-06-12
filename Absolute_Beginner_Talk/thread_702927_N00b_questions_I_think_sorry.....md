---
title: "N00b questions I think sorry...."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by sasuke223 on 2008-02-20
I have a few questions. 
To start it off I have a problem creating a wireless connection
    I have entered my
     connection name
     WPA and Password
     Setting it as TKIP
* To tell you the truth I don't know if my wireless card is enabled. The detection light on my keyboard is not lit up... o_O?

I also get these problems in the restricted drivers managment
     
       ATI Accelertated Graphics Driver: 
   * The Software Source for the Package
     xorg-driver-fglrx
     Is not enabled

       Frimware for Broadcom 43xx chipset family:
   * The software source for the package
      bcm43xx-fwcutter
      is not enabled

lol, this is also a very common error with n00bs. I'm having trouble installing a toolchain, because it says I must install automake and autoconf... I've tried this but all of the DEB files were corrupt and they wouldn't install... Any help on this and I would appreciate you very much

These are currently my only questions, post it, PM me, or e-mail me at [email]sasuske223@aol.com[/email]... I really need to know this or I'm going to switch back to windows XP. : )

---

### Post by robkeys on 2008-02-20
As for the drivers not being enabled just click on the checkboxes in the restricted driver manager to enable and install them.

As for the wireless issue, once your driver is installed it should start working!

-r

---

### Post by Presto123 on 2008-02-20
For Broadcom wireless, try this:
[http://ubuntuforums.org/showthread.php?p=4371998#post4371998](http://ubuntuforums.org/showthread.php?p=4371998#post4371998)

---

### Post by Timn on 2008-02-20
It sounds like you just need to connect to the internet via a hard wire then go into the restricted drivers manager and enable both of them. That should fix the problem of both drivers being disabled and also get your wireless connection working.

Timn

---

### Post by sasuke223 on 2008-02-20
Yea, I've already done all of this lol, this is why I asked. I even gave as much info as I could... I'm currently hardwired and still its not working. And thanks for the one who posted the broadcom link:guitar:

---

### Post by kaginken on 2008-02-20
Here is the answer to all your wireless problems, automatic!
[http://backports.ubuntuforums.com/showthread.php?t=405990](http://backports.ubuntuforums.com/showthread.php?t=405990)

Here's another nugget, just fyi:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Presto123 on 2008-02-20
> **sasuke223 said:**
> Yea, I've already done all of this lol, this is why I asked. I even gave as much info as I could... I'm currently hardwired and still its not working. And thanks for the one who posted the broadcom link:guitar:

Not trying to be redundant, but to further build on what Timn says, does Restricted Drivers Manager have checked boxes showing it as being enabled?

---

### Post by sasuke223 on 2008-02-22
I"m currently reinstalling XP, so that I can put both on. But yea, I have boxes to check, I only get those messages when trying to check them... lol. After that it stays unchecked... Also my problems should only be with the ATI driver now... Thanks for the responses guys.

---

### Post by puzzlefreak on 2008-02-22
are you running NDISWrapper? There's a good tutorial somewhere here.

---

