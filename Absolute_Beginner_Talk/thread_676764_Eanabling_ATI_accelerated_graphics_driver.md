---
title: "Eanabling ATI accelerated graphics driver"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by alamjadtawfiq on 2008-01-24
I have a problem in enabling this driver. I tried this package, which was not for Gusty ([link]("http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.15/xorg-driver-fglrx_7.0.0-8.25.18+2.6.15.12-29.1_i386.deb")), and after I restarted the system, the X server didn't work, I installed Edubuntu again. What can I do now?

---

### Post by lswest on 2008-01-24
you have to go to system-->administration-->software sources (it may also be under preferences, not sure atm) and check the boxes for universe and multiverse.

---

### Post by alamjadtawfiq on 2008-01-24
I do not have an internet connection yet on Ubuntu, will that work?

---

### Post by mikeyphi on 2008-01-24
> **alamjadtawfiq said:**
> I do not have an internet connection yet on Ubuntu, will that work?

No!! - you need an Internet connection to download software........however, if you have access to the Internet elsewhere (friend's system?) then look into this:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

That package allows you to burn Ubuntu software to CD so you can install just as if you were on the Internet.

---

### Post by alamjadtawfiq on 2008-01-24
I have XP on the same computer, and using it to connect to the internet.. but when I install this package, what should I do?

---

### Post by mikeyphi on 2008-01-24
> **alamjadtawfiq said:**
> I have XP on the same computer, and using it to connect to the internet.. but when I install this package, what should I do?

No - you don't install that package - I should have explained!!

The apt on CD lets you download all the packages you need onto a CD - you can then use that CD to install packages on Ubuntu - as though you are connected to the Internet.

Read the info at the site I posted:  [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
It should explain the methods.

You should then enable the ATI driver - if it isn't installed - it will install from the CD.

BUT from you post (above) you have an Internet connection through XP on your computer - so why don't you have a connection under Ubuntu?????
Lets talk about that - it will make your life much easier!!

---

### Post by alamjadtawfiq on 2008-01-24
Thanks for your help.

I use dial-up connection, after a lot of effords, I was able to identify the modem. Now I tried to connect via this modem using Gnome-ppp. I failed, and I posted the problem before on a separate thread:
[http://ubuntuforums.org/showthread.php?t=676758]("http://ubuntuforums.org/showthread.php?t=676758")

---

### Post by mikeyphi on 2008-01-24
> **alamjadtawfiq said:**
> Thanks for your help.

I use dial-up connection, after a lot of effords, I was able to identify the modem. Now I tried to connect via this modem using Gnome-ppp. I failed, and I posted the problem before on a separate thread:
[http://ubuntuforums.org/showthread.php?t=676758]("http://ubuntuforums.org/showthread.php?t=676758")

Sorry - I know nothing about ppp but you should get some pointers here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by alamjadtawfiq on 2008-01-24
No problem, but do you know anything that can help me for the graphics card (which is **ATI radeon xpress 200m**)?

---

### Post by mikeyphi on 2008-01-24
> **alamjadtawfiq said:**
> No problem, but do you know anything that can help me for the graphics card (which is **ATI radeon xpress 200m**)?

Look under Synaptic - do a search on fglrx:
you'll get the linux restricted modules (they should already be installed if you correctly enabled the repos in Software Sources)
You should also see the xorg-driver-fglrx.

The correct ATI driver should be installed automatically if you use the Restricted Drivers Manager - or you can do it yourself!

You can install using the apt on CD if you don't have Internet on Ubuntu.

---

### Post by alamjadtawfiq on 2008-01-24
I am now able to open the internet from Ubuntu! I searched for the first package, and I found that it was installed, while I didn't find the second package (the xorg...)

And when I tried to install the accelerator from the restricted drivers manger, the same window appeared (the thumbnail in the first post).

How can I download that package and get started? I downloaded a package that has the same name, but it didn't work, it was for Dapper. In the description of the package, I didn't find the name of my ATI card. I tried to search for it through the internet, but I failed.

Can you help, or do you know anyone you can help please?

---

### Post by mikeyphi on 2008-01-24
> **alamjadtawfiq said:**
> I am now able to open the internet from Ubuntu! I searched for the first package, and I found that it was installed, while I didn't find the second package (the xorg...)

And when I tried to install the accelerator from the restricted drivers manger, the same window appeared (the thumbnail in the first post).

How can I download that package and get started? I downloaded a package that has the same name, but it didn't work, it was for Dapper. In the description of the package, I didn't find the name of my ATI card. I tried to search for it through the internet, but I failed.

Can you help, or do you know anyone you can help please?

Open System/Administration/Software Sources.....check the box for Proprietary drivers for devices (restricted)
Use the Restricted Drivers Manager....if there's any problem.....
 open Synaptic - reload the index - search for and install xorg-driver-fglrx

---

