---
title: "[SOLVED] Xubuntu to Ubuntu Problems"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-18
Ok this seems strange. I wasn't completely satisfied with Xubuntu 7.10 Gutsy Gibbon so I decided to switch over to Ubuntu 7.10. The only how-to I could find on this subject explained how ubuntu was installed using a kubuntu live CD. I followed these instructions and simply replaced kubuntu with xubuntu in the command lines:

```
sudo apt-get install ubuntu-desktop
sudo apt-get remove xubuntu-desktop xubuntu-artwork-usplash
sudo apt-get autoremove
```

The Ubuntu 7.10 installation was entirely successful. However the removal of Xubuntu doesn't appear to have worked out at all. The apt-get remove command only removed 7 packages and the autoremove command removed only 4 packages. Ever the optimist, after I rebooted my machine I still expected Xubuntu and everything that came with it to be gone however it wasn't. All Xubuntu software packages that came with installation have somehow clung to my harddisk and in my settings menu I have all the ubuntu settings and all xubuntu settings (i.e. Main Menu and Menu Editor).

I don't have any blank cd's so creating a Ubuntu Live CD is out of the question for a long time and I still haven't received the CD I requested, so if anyone at all could offer me some advice on how to go about eradicating Xubuntu from my system manually, I would be forever grateful. Thanks.

---

### Post by LeAstrale on 2008-01-18
i have personally switched from Ubuntu to kubuntu (without a reinstall)

the way i did was to sudo apt-get install kubuntu-desktop

then install it all and then sudo apt-get remove ubuntu-desktop && sudo apt-get autoremove

after that i had Kubuntu everything, but Gnome (ubuntu-desktop) still left one hell of a mess of programs and so on. so what i did was manually go through the whole package handling (the packages installed) and then removed whatever i didnt need (be it GNome or KDE apps) and now i have a pretty clean kubuntu, i think the same should work for you.

---

### Post by overdrank on 2008-01-18
> **Semong said:**
> Ok this seems strange. I wasn't completely satisfied with Xubuntu 7.10 Gutsy Ribbon so I decided to switch over to Ubuntu 7.10. The only how-to I could find on this subject explained how ubuntu was installed using a kubuntu live CD. I followed these instructions and simply replaced kubuntu with xubuntu in the command lines:

```
sudo apt-get install ubuntu-desktop
sudo apt-get remove xubuntu-desktop xubuntu-artwork-usplash
sudo apt-get autoremove
```

The Ubuntu 7.10 Gutsy Ribbon installation was entirely successful. However the removal of Xubuntu doesn't appear to have worked out at all. The apt-get remove command only removed 7 packages and the autoremove command removed only 4 packages. Ever the optimist, after I rebooted my machine I still expected Xubuntu and everything that came with it to be gone however it wasn't. All Xubuntu software packages that came with installation have somehow clung to my harddisk and in my settings menu I have all the ubuntu settings and all xubuntu settings (i.e. Main Menu and Menu Editor).

I don't have any blank cd's so creating a Ubuntu Live CD is out of the question for a long time and I still haven't received the CD I requested, so if anyone at all could offer me some advice on how to go about eradicating Xubuntu from my system manually, I would be forever grateful. Thanks.

Hi and maybe this link will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Semong on 2008-01-18
> **overdrank said:**
> Hi and maybe this link will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Ahh thank you my friend that worked beautifully. I was midway through uninstalling everything with synaptic and this sped things up nicely.

---

