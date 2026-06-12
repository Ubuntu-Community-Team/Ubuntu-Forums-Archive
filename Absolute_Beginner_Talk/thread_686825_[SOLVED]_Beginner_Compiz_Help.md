---
title: "[SOLVED] Beginner Compiz Help"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-03
After recently (as in today) switching over to gutsy from feisty, I couldn't figure out where exactly I could enable compiz-fusion. I went to System > Preferences > Appearances but there was no specific mention of compiz so i searched online. I found this guide ([http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/](http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/)) and typed these two commands from that page:

```
sudo aptitude -y update && sudo aptitude dist-upgrade
sudo aptitude install compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf libcompizconfig0 python-compizconfig
```

However, whenever I try enabling any of the visual effects except for "None" I get the following message:

```
The Composite extension is not available
```

---

### Post by Ub1476 on 2008-02-03
If you are using ATI with flgrx drivers, install xserver-xgl. If you have nvidia/intel edit xorg.conf and set composite to "1".

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by intense.ego on 2008-02-03
My graphics card is an ATI Radeon X1300, and I am using the restricted drivers. Should I install XGL, like i did with Beryl on Feisty?

---

### Post by Ub1476 on 2008-02-03
Yes. On Gutsy, XGL will automatically be set up for you thought. 

```
sudo apt-get install xserver-xgl
```

Logout.

---

### Post by jan quark on 2008-02-03
try it and change the session during the login in to xclient

---

### Post by intense.ego on 2008-02-03
everything is working fine now, thank you so much for your help.

---

