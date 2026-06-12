---
title: "Flash from automatix"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-10-30
I downloaded flash player from automatix but i doesn't seem to work with firefox it still shows that i have to download the plugin to show some flash objects in some web sites 

I restarted firefox and it still does it 

do i have to restart my pc to make it work or something didn't installed right?

---

### Post by fasoulas on 2006-10-30
i forgot to mention that i use firefox 2

---

### Post by arnieboy on 2006-10-30
> **fasoulas said:**
> i forgot to mention that i use firefox 2

what does typing about:plugins on firefox do? Does it list the flash plugin?

---

### Post by nickburns on 2006-10-30
I have noticed that they fixed this problem with 6.10.  Perhaps it is time for an upgrade?

---

### Post by jkvv_1973 on 2006-10-30
Automatix flash install is no good...


Try this:
[http://www.kungfuice.com/index.php/2...n-ubuntu-edgy/](http://www.kungfuice.com/index.php/2...n-ubuntu-edgy/)

---

### Post by fasoulas on 2006-10-30
I use the 6.06 version not the 6.10 you mean that i can't make it work on that version ?

I don't want to install edgy right now it is full of problems 

I just install 6.06 last night for the first time along with Xp

---

### Post by arnieboy on 2006-10-30
> **fasoulas said:**
> I use the 6.06 version not the 6.10 you mean that i can't make it work on that version ?

I don't want to install edgy right now it is full of problems 

I just install 6.06 last night for the first time along with Xp
ok lets take it step by step. which architecture of ubuntu 6.06 are you on? 386/amd64/ppc ?

---

### Post by fasoulas on 2006-10-30
> **arnieboy said:**
> ok lets take it step by step. which architecture of ubuntu 6.06 are you on? 386/amd64/ppc ?

i use 386

---

### Post by arnieboy on 2006-10-30
> **fasoulas said:**
> i use 386
and what does about:plugins say? does it list flash player 9?

---

### Post by fasoulas on 2006-10-30
> **arnieboy said:**
> and what does about:plugins say? does it list flash player 9?

it doesn't show anything about flash or other plugin

---

### Post by arnieboy on 2006-10-30
do the following one step at a time.
```
wget http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin/
sudo apt-get remove flashplugin-nonfree        
sudo apt-get install alsa-oss gsfonts gsfonts-x11 gsfonts-other m4
sudo tar zxvf FP9_plugin_beta_101806.tar.gz -C /opt
sudo mv -f /opt/flash-player-plugin-9.0.21.55 /opt/flash32
sudo chmod 755 /opt/flash32/libflashplayer.so
sudo cp -f /opt/flash32/libflashplayer.so /usr/lib/mozilla/plugins
sudo cp -f /opt/flash32/libflashplayer.so /usr/lib/mozilla-firefox/plugins
sudo cp -f /opt/flash32/libflashplayer.so /usr/lib/firefox/plugins
sudo rm -f ~/.mozilla/plugins/libflashplayer.so
rm -f ~/FP9_plugin_beta_101806.tar.gz
```

---

### Post by blitzer on 2006-10-31
Thanks arnieboy automatix2 is downloaded and will be put to good use :D

---

