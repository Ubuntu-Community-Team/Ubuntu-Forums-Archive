---
title: "Gnome 3 Bug - Flash not working in Epiphany Web Broswer"
date: 2011-09-29
forum: Any Other OS
---

### Post by TheMidnightWings on 2011-09-29
Well, as the title says, I am trying to use Epiphany ([http://projects.gnome.org/epiphany/](http://projects.gnome.org/epiphany/)) to surf the web. However whenever I go to sites that require flash, such as; Youtube, Vimeo, Metacafe, or just try to watch most videos in General, I can't. Example: 
[IMG]http://imgur.com/1mVrZ[/IMG]

However, I have flash installed: 

[IMG]http://imgur.com/cJzOR[/IMG]


Any ideas you tech wizards out there? :confused:

---

### Post by kronolf on 2011-10-13
Flash player uses gtk2, epiphany 3 uses gtk3.. they're not compatible together. You have to use nspluginwrapper to see flash videos.

---

### Post by TheMidnightWings on 2011-10-14
Thank you, that actually worked! :) :popcorn:

---

### Post by AndeeeUk on 2011-10-20
I have installed nspluginwrapper and I still am not able to get flash working. Can you show me how you installed it? Do I still need gtk3 also?

I have checked if the plugin is enabled in the browser and it does say that it is enabled.

Thanks
Andy

---

### Post by nknico on 2011-10-22
I installed nspluginwrapper but there is no way to see any Flash content in epiphany.

Is there an other way to make it work ?

---

### Post by nknico on 2011-10-31
Up !

---

### Post by rorschachwalter on 2011-10-31
After you install nspluginwrapper, close all your browsers. Then do
```
sudo dpkg-reconfigure flashplugin-installer
```
This got it working for me.

---

### Post by kronolf on 2011-11-22
I'm using Debian.
All I can say is that downloading a 32bit version of Flash Player 10 (not 11) I made it work on Epiphany just running something like
```
nspluginwrapper -v -i /home/pol/Scaricati/libflashplayer.so
```

Of course you have to change the path of the file.

---

