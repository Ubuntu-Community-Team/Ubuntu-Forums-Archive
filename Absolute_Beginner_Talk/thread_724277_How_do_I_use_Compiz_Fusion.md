---
title: "How do I use Compiz Fusion"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by TheJokerV on 2008-03-14
Is there a guide or could someone tell me how to enable compiz fusion on ubuntu 7.10. I have heard in this release that its included. Also do I need to change my video drivers in order to run it. Thanks

---

### Post by NightwishFan on 2008-03-14
You need to install the restricted drivers. Then reboot and run this command in a terminal:
```
sudo apt-get install compizconfig-settings-manager
```
There will be a place in the system/preferences/ menu to adjust the effects.

---

### Post by chlorinekid on 2008-03-14
> **TheJokerV said:**
> Is there a guide or could someone tell me how to enable compiz fusion on ubuntu 7.10. I have heard in this release that its included. Also do I need to change my video drivers in order to run it. Thanks

use this code to install the settings manager. once installed it will appear in system > prefs

```
 sudo apt-get install compizconfig-settings-manager

```

---

### Post by glennric on 2008-03-14
To enable compiz go to System->Preferences->Appearance and select the Visual Effects tab.  Then select Normal, Extra, or Custom to enable compiz.  Custom may not appear unless you have compizconfig-settings-manager installed.  This may not work, depending on your hardware and configuration.  If you have an nvidia or ati graphics card you may have to enable the restricted modules.  To do this go to System->Administration->Restricted Drivers Manager.

---

### Post by jayg1169 on 2008-03-14
this guide is good!

[www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

---

### Post by CJ56 on 2008-03-14
And this one ain't bad, either...

[http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html]("http://devolio.com/blog/archives/82-Installing-Avant-Window-Navigator-in-Gutsy.html")

.... 8)

---

### Post by Therion on 2008-03-14
[How to Set Up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) - Get it running and looking good... Basic set ups here.

[What all the plugins DO](http://wiki.opencompositing.org/PluginsMain).

[What all those cool animations look like](http://wiki.opencompositing.org/Plugins/Animation).

---

