---
title: "Support for Kubuntu?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by chip616 on 2008-03-20
I tried the Kubuntu LiveCD for 7.10 in December, and found a lot of pieces missing, so did not pursue it.  However, maybe I just need some direction.

Video Drivers:  The display on my laptop came up at substantially less than the 1920 x 1200 native.  Kubuntu was the only one of the 'major' distros that missed this.  When I posted asking for help, I was directed to the nvidia site and given directions on how to compile my own.  This seems pretty strange for a distro that is supposed to be easy to use.  Is there no repository that has pre-compiled nvidia video drivers for 7.10?

Incomplete Menus:  Many of the menu items had miscellaneous garbage characters following their entries in the Kmenu tree.  Has this been fixed?

Lack of Wireless Support out of the box:  This is a Dell Vostro 1700 with Intel wireless chipset.  This is not weird harware.  If I remember correctly, it didn't work right away.

All of the above led me to the feeling that Kubuntu was incomplete and got rushed out the door.  Therefore, my question has to do with the level of support for KDE in Ubuntu.  Is this a product that is fully supported, or just an add-on?

I ask because I tried Fedora 8 instead of Ubuntu, and I am finding that KDE support in Fedora, while there, is hardly stellar.  In addition, I can't keep up with the furious pace of development in Fedora, and the inevitable 'breakages' that occur in this frenetic advancement.  I need more stability.  I've been looking at Debian, and have been a Xandros user for 5 years.  I need more software than Xandros offers, but more stability than Fedora offers, yet nothing quite as lethargic and DIY-oriented as Debian.  Kubuntu should be a good fit for me, but I can't warm up to it.

Suggestions?

Thanks.

Frank.

---

### Post by arochester on 2008-03-20
1) OK UbuntuForums covers Kubuntu, but Kubuntu has it's own forum at [http://www.kubuntuforums.net](http://www.kubuntuforums.net)

2)If you have an Nvidia card then try the script called "Envy" from Albert Milone from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) . It works for many people but not everyone.

3) I've never noticed "miscellaneous garbage characters". Is it a fonts problem? What happens if you install other fonts?

4) Wireless? Have you looked at [https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700) ? OK there are small differences between Ubuntu and Kubuntu but they are fairly simple.

---

### Post by (((X))) on 2008-03-20
Restricted drivers for Nvidia are in standard ubuntu repos(restricted-manager-core and frontend for kde: restricted-manager-kde)
You will aso find various linux-restricted** packages, just open synaptic and I'm sure you find them.

Ubuntu or KDE is less stable then Xfce or Xubuntu os. 

> Incomplete Menus: Many of the menu items had miscellaneous garbage characters following their entries in the Kmenu tree. Has this been fixed?


They can be removed by Right clicking on Ubuntu main-menu>edit menus orso.


[QUOTE]Lack of Wireless Support out of the box: This is a Dell Vostro 1700 with Intel wireless chipset. This is not weird harware. If I remember correctly, it didn't work right away.[/QOUTE]

Imroved, My wifi works outof the box on Gutsy.
But, yours isn't working, Ndiswrapper is only solution at the moment.

---

