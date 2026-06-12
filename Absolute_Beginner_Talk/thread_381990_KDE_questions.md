---
title: "KDE questions"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-03-11
I want to try out the KDE desktop environment, if I follow [this]("http://www.psychocats.net/ubuntu/kde") guide will it: 
1. Change my GRUB?
2. Change the ubuntu logo that appears during bootup after I select ubuntu from GRUB?

---

### Post by r4ik on 2007-03-11
1.no
2.should not.

You can choose for Gnome or Kde at the login screen

---

### Post by finer recliner on 2007-03-11
1) adding KDM will not change your GRUB configuration. you choose which desktop manager (gnome or KDE) when you log into ubuntu (hit options > sessions). 

2) it will probably change your startup logo, but it can be changed back. i remember having a bit of trouble, but eventaully got it. i dont remember what i did though :(

---

### Post by msak007 on 2007-03-11
> **Matt1632 said:**
> I want to try out the KDE desktop environment, if I follow [this]("http://www.psychocats.net/ubuntu/kde") guide will it: 
1. Change my GRUB?
2. Change the ubuntu logo that appears during bootup after I select ubuntu from GRUB?
1. It will not change GRUB, because you're still booting into the same OS / kernel. The difference will be once X loads.
2. Not sure, as I've never installed Ubuntu / Kubuntu together. Installing **kubuntu-desktop** will install the kubuntu-artwork-usplash package, which is what provides the startup image. If it does force an overwrite and uses the Kubuntu usplash theme, you can always change it by typing the following:
```

sudo update-alternatives --config usplash-artwork.so
```
This will give you a choice between all the usplash themes you have installed, and let you pick the one you want to be your default. Hope this helps, let us know if you need anything else.

---

