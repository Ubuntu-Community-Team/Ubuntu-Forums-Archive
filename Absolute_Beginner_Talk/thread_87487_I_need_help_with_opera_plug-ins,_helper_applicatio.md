---
title: "I need help with opera plug-ins, helper applications"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by cityismine on 2005-11-08
Hey guys, I installed opera by following the ubuntuguide.  I got it up and running, but when I downloaded a pdf, it wouldn't launch.  So my question is, how do I get it to start using plug-ins, and helper applications that work for firefox?

---

### Post by Orunitia on 2005-11-08
I don't know if this will help, but try downloading Opera 9 beta. It seems to have fixed all my problems with plugins that I had with 8.5.

[http://snapshot.opera.com/unix/9.0-Preview-1/intel-linux/opera-static_9.0-20051020.1-qt_en_i386.deb](http://snapshot.opera.com/unix/9.0-Preview-1/intel-linux/opera-static_9.0-20051020.1-qt_en_i386.deb)

---

### Post by shinygerbil on 2005-11-08
I installed mozplugger, and it set everything up for me :) Run:

```
sudo apt-get install mozplugger
```

Then restart Opera and it should find it. If it doesn't find it automatically, open Synaptic or Adept (or any package manager), find the mozplugger package, click on Installed Files and look for the directory containing the file "mozplugger.so". It should be something like /usr/lib/mozilla/plugins/mozplugger.so. (There may be more than one, it doesn't mater which you use) 
Now go into Opera, go to Preferences->Advanced->Content->Plugin Options... and press Change Path. Now add the directory that contains mozplugger.so and restart Opera, and you're sorted :P

BTW, I can't get KPDF to embed itself into opera, I don't know if it's possible. I can't seem to get KParts to load, does anyone know how that works?

Steve

---

### Post by eyebrowman92 on 2005-11-08
i tried installing opera 9 by downloading the deb package to my desktop, then i extracted and got two tars.  i extracted those and went to the usr folder and found the file to install opera. i ran it in a terminal and the terminal popped up for a second and dissappeared.  the same thing happened when i was trying to install ie. i just had to install cabextract. does anyone know if i have to install anything here?

---

