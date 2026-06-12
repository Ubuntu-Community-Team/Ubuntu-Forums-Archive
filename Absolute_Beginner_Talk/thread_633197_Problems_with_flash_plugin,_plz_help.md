---
title: "Problems with flash plugin, plz help"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by josefa on 2007-12-06
I just switched to ubuntu 7.10 and I must say that I'm very pleased. I thought I had installed flash with libflash0c2 and libflash-mozplugin, but didn't work., so I installed flashplugin-nonfree too. No luck. I uninstall these 3 plugins and reinstall flashplugin-nonfree but I'm still getting "additional plugins are required to display all media on this page" and "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player". Can I be redeemed at this point?

---

### Post by SpacePilot on 2007-12-06
sudo apt-get install j2re1.4-mozilla-plugin
sudo apt-get install flashplugin-nonfree

---

### Post by Znort_Ubern00b on 2007-12-06
is this for use with firefox?

if so go to firefox add ons section.in there are plugins that will enable flash etc...

[Firefox addons]("https://addons.mozilla.org/en-US/firefox/browse/type:7")

---

### Post by Roland123 on 2007-12-06
you probably have the same problem i did. If you try to install flashplugin-nonfree in synaptic you don't see a error message, telling that md5sum failed and flash not installed. 

if you try to install it in console ( "sudo apt-get install flashplugin-nonfree" ) and it tells you that md5sum mismatch... the problem is solved here: [LINK]("http://ubuntuforums.org/showpost.php?p=3902460&postcount=31")

---

### Post by josefa on 2007-12-06
Thanks everyone, Roland, I visited that thread but it's too complicated for me at this point. I guess I'll have to learn to live without flash for a while.

---

### Post by SpacePilot on 2007-12-06
Well, if you don't want to fix the unfree (which i never had any trouble with) You can use the free one.

sudo apt-get install mozilla-plugin-gnash

---

### Post by josefa on 2007-12-06
I think either firefox or ubuntu should fix this issue, flash is a big deal

---

