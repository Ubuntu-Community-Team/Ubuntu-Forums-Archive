---
title: "mplayer firefox plugin not showing up!"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by unoobu on 2006-05-20
Situation: mplayer firefox plugin isn't showing up in about: plugins, it isn't there.  I have uninstalled and reinstalled the mplayer firefox plugin through Automatix five times.  I have also manually installed the plugin.  I have mplayer, and it works.  However, the plugin for firefox just doesn't show up.  I have the latest firefox 1.5

Question: So, what needs to be done to get this working?

Thanks,

uNOOBu

---

### Post by glotz on 2006-05-20
Hellow there! For all your Firefox plugin woes, refer to [http://plugindoc.mozdev.org/linux.html](http://plugindoc.mozdev.org/linux.html)

I think you'll need to make a symbolic link of mplayerplug-in.so to your /opt/firefox/plugins

That is, open terminal (applications > accessories > terminal)

First, update the locate list of file locations (this will take a minute)
```
sudo locate -u
```
Then actually search for the plugin
```
locate mplayerplug-in.so
```
Then switch to Firefox plugins folder
```
cd \opt\firefox\plugins
```
And then finally make the symbolic pointing to the plugin here
```
sudo ln -s [path to plugin\mplayerplug-in.so]
```

And restart Firefox and it'll work. Right?

---

### Post by unoobu on 2006-05-22
[QUOTE=glotz]Hellow there! For all your Firefox plugin woes, refer to [url]http://plugindoc.mozdev.org/linux.html[/QUOTE]

It worked, thanks!  Can you tell me why it worked though?  Why didn't Automatix install the plugin properly?  I mean, it obviously placed the file on the hard drive...

---

### Post by glotz on 2006-05-22
No idea. I've never used automatix.

---

