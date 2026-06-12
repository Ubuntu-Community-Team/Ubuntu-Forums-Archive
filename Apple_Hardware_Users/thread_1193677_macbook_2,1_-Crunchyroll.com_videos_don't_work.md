---
title: "macbook 2,1 -Crunchyroll.com videos don't work"
date: 2009-06-21
forum: Apple Hardware Users
---

### Post by Death_To_The_World on 2009-06-21
I am using jaunty on macbook 2,1 with firefox.  I got it so videos will play on just about every other website, but videos will not play on crunchyroll.com for some reason.

---

### Post by tiagobt on 2009-06-21
I have the same hardware and the videos in crunchyroll.com seem to work. Is your Flash plugin properly installed? It might be a version problem as well.

Just to compare, I'm using the following:
- Kubuntu 9.04
- Firefox 3.0.11
- Flash plugin 10.0.22.87 (flashplugin-installer)

---

### Post by Death_To_The_World on 2009-06-21
Im usuing Ubuntu 9.04, firefox 3.0.11, and I wasnt sure how to check but under plug ins it says i have divx web player, quicktime plugin 7.2.0, shockwave flash 9.0.r999, vlc media plug in(compatible totem 2.26.1), windows media player plug-in (compatible;totem)

---

### Post by tiagobt on 2009-06-22
Your Flash plugin is outdated. This could be the reason why the videos are not being displayed. Try to update the plugin with the following commands:

```
sudo apt-get update
sudo apt-get install flashplugin-installer
```

Notice that the multiverse repository has to be enabled in your /etc/apt/sources.conf file.

---

### Post by Death_To_The_World on 2009-06-22
I tried it and in the terminal it said it worked, but when i check firefox the version is still the same and videos still do not work.  hmm any other ways i can try to do it? I dont know how to uninstall it.

---

### Post by tiagobt on 2009-06-22
Do you remember how you installed the Flash plugin? Did you use the Firefox wizard? Did you download a DEB file from Adobe's website? Did you use a package from the Ubuntu repositories? The instructions to remove the plugin depend on how you installed it.

If you don't know how the plugin got installed in first place, you could go for a more aggressive approach...

1. Remove all the packages that have something to do with Flash:
```
sudo apt-get --purge remove adobe-flashplugin flashplugin-installer flashplugin-nonfree gnash gnash-common gnash-tools mozilla-plugin-gnash konqueror-plugin-gnash swfdec-mozilla nspluginwrapper konqueror-nsplugins libflashsupport
```

2. Remove all the folders where the Flash plugin might have been installed:
```
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rf /usr/lib/nspluginwrapper
sudo rm -f /etc/alternatives/*flash*
sudo rm -rf ~/.macromedia
sudo rm -f ~/.mozilla/plugins/*flash*
```

3. Install the latest Flash plugin from the multiverse repository:
```
sudo apt-get update
sudo apt-get install flashplugin-installer
```

---

### Post by irwand on 2009-07-18
I just got crunchyroll to work on my machine. Thanks for the hint tiagobt!!
I tried your steps, it still didn't work for me, but then I removed my ~/.mozilla directory and restart firefox. After that, it worked. Yes, I lost all my firefox setting, but now I can watch Naruto again on my linux machine! Yay!

---

