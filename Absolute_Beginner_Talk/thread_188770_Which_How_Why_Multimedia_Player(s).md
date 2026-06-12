---
title: "Which? How? Why? Multimedia Player(s)"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-06-04
I want to listen to:

[http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx](http://boss.streamos.com/wmedia/csps/clerks_office/service/church_service.wvx)

This purports to be a Windows wave file of some sort. But when I click the link, an extra browser-tab opens, saying I have "chosen to open" xxx.xxx.ASF as a file name and no Totem, XMMS, AMAROK, etc.

How do I either config FireFox to open this for me, or from where directory / program do I "go" to call the multimedia program player?

This is confusing because other sound files have played w/o the link asking which program to run.

---

### Post by mscman on 2006-06-04
I tried playing this file and it loaded the MPlayer plugin for firefox.  Perhaps this is what you need to install...

---

### Post by bluevoodoo1 on 2006-06-04
I hear the organ! It works for me, embedded in the page with mplayer and mozilla-mplayer.

Try installing those with Synaptic Package Manager or with...

```
sudo apt-get install mplayer mozilla-mplayer
```

---

### Post by Mark_in_Hollywood on 2006-06-04
Automatix says that I have Mplayer and Plug-in for FireFox already installed. Go figure.

I can't find the Mplayer in any menu/sub-menu, either. Go figure.

---

### Post by harishg on 2006-06-04
Check for the plugins installed using about:plugins .The problem is sometimes more than one plugin is configured for the same .xxx extension.If you find a clash remove the plugin which is causing the clash.

---

### Post by harishg on 2006-06-04
about : plugins i hate :p [-(

---

### Post by Mark_in_Hollywood on 2006-06-05
I have nothing in any menu/submenu: 

about:plugins

what gives?

---

### Post by ramcosca on 2006-06-05
[QUOTE=bluevoodoo1]I hear the organ! It works for me, embedded in the page with mplayer and mozilla-mplayer.

Try installing those with Synaptic Package Manager or with...

```
sudo apt-get install mplayer mozilla-mplayer
```[/QUOTE]Heh, I learn with every thread I read. Thanks, I can clearly hear the organ. :KS

---

