---
title: "Opera And Flash Final?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2008-01-23
How do I get flash working with Opera? I installed flash but it doesn't recognise it. After research I realized that it doesn't work without a workaround.

Any ideas?

---

### Post by LaRoza on 2008-01-23
> **tdrusk said:**
> How do I get flash working with Opera? I installed flash but it doesn't recognise it. After research I realized that it doesn't work without a workaround.

Any ideas?

Install Opera 9.50b. Works fine on my end.

Although it is beta, it is worth using, I use it as my primary browser with no big problems.

---

### Post by tdrusk on 2008-01-24
bump

---

### Post by benerivo on 2008-01-25
It should work with 9.50b. Did you try this version or does it have to be with 9.25?

---

### Post by rosegarden78 on 2008-01-25
Yeah I had to get 9.5 beta from Opera site.  

Then navigate to /usr/lib/mozilla/plugins and
Copy flashplugin-nonfree.so
To /usr/lib/opera/plugins. 
 
Or check /home/user/.mozilla/plugin directory.

You might need to launch "gksudo nautilus" "kdesu konqueror" or "gksudo thunar" to open a file manager as root.  Otherwise you might not be able to copy and paste certain files.

---

### Post by bwtranch on 2008-01-25
How about gnash? It's the only thing that will work on my AMD64. I tried the workaround on it, but it didn't work, so I installed gnash and it worked in a flash. Made me feel good, not having to use something made by the mudmasters (adobe).:)

---

### Post by rosegarden78 on 2008-01-26
Not to promote bias as I tried Gnash but was unable to get 100% so cannot suggest as #1 choice maybe #2 but since flashplugin-nonfree.so is working with 9.5 Beta 100% why fix something that isn't broken?

---

### Post by LaRoza on 2008-01-26
> **rosegarden78 said:**
> Not to promote bias as I tried Gnash but was unable to get 100% so cannot suggest as #1 choice maybe #2 but since flashplugin-nonfree.so is working with 9.5 Beta 100% why fix something that isn't broken?

As long as it works.

---

### Post by bwtranch on 2008-01-26
Yeah, I agree, whatever works gets me through the day. But adobe has not issued a 64 bit version of their famous plug-in (and I'm not the only person irked about that). I think they just did issue the windows 64 and say the open source may be out later this year! Ahhh, well, you can draw you own conclusions on that one. In a related story Gates said that microsoft (which literally means very, very tiny software) can lose money for years to stem the tide of open source. Talk about shooting oneself in the foot to spite your wallet.

---

### Post by wheezer on 2008-01-30
I don't want to run the opera beta. I have 9.25. Does the mozilla flash plugin work for that?

---

### Post by wheezer on 2008-01-30
PS
There is no such plugin in my usr/lib/mozilla directory. Just totem plugins.
There is plugin directory in home/user/.mozilla at all.

Do I actually have to install flash again, just so Opera will find it?  This is so maddening. It's always something like this in linux virtually every day. I love aspects of it at times, but it too often feels more like hobby than a practical tool for real work (for anything but my server). 

Oh well, just a vent.  Ubuntu is still the best of the breed. It's the breed that feels like an evolutionary  throwback sometimes :)

---

### Post by gandaran on 2008-01-30
> **wheezer said:**
> I don't want to run the opera beta. I have 9.25. Does the mozilla flash plugin work for that?

wheezer
            check the version of flash you have installed, if you have the flashplugin-nonfree 9.0.48 it will work, just copy the plugin to the opera plugin folder.
if you flash version is 9.115, forget it , it will  never work with opera 9.25.
I installed opera 9.50 beta, just copied the plugin folder (flash 9.115) from  the home mozilla folder to the home opera folder, working smoothly.
gandaran

---

### Post by wheezer on 2008-01-30
> **gandaran said:**
> wheezer
            check the version of flash you have installed, if you have the flashplugin-nonfree 9.0.48 it will work, just copy the plugin to the opera plugin folder.
if you flash version is 9.115, forget it , it will  never work with opera 9.25.
I installed opera 9.50 beta, just copied the plugin folder (flash 9.115) from  the home mozilla folder to the home opera folder, working smoothly.
gandaran


My Flash works fine in firefox 2.0.11.  There is no plugin folder in my home folder, so there is nothing to copy

Next?

---

### Post by badmotor on 2008-01-31
Yeeha! This thread delivers.

Went to Firefox plugin folder, copied the libflashplayer.so into the Opera home folder (there was no visible plugin folder).

And hey presto.  :)

---

### Post by gandaran on 2008-01-31
> **wheezer said:**
> My Flash works fine in firefox 2.0.11.  There is no plugin folder in my home folder, so there is nothing to copy

Next?

yes, there is no plugin in you home mozilla folder if your flash is flashplugin-nonfree.
flashplugin-nonfree is installed on the file system, /usr/lib/flashplugin, that's where you must look, then copy either to /usr/lib/opera/plugins or make a plugins folder on home/user/.opera.

---

