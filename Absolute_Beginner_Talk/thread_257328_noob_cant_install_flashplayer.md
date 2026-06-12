---
title: "noob cant install flashplayer"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by ghstwalker on 2006-09-14
alright i've read the readme file for flashplayer 7 and ive been told to manually copy libflashplayer.so and flashplayer.xpt into the plugins folder, but i can't find a plugins folder in the firefox folder and i cannot create a new folder.
heres where i am looking
file system>etc>firefox>
ive looked in all the subfolders...
is there a firefox folder in another directory that im not seeing?
sorry, im an avid windows user and i still have the windows user mentality.
thanks for all your help in advanced.

---

### Post by RobsterUK on 2006-09-14
As with most programs in Ubuntu, Flash can be installed via Applications > Add/Remove

try doing it that way, much easier

---

### Post by joep on 2006-09-14
Like you I'm new to Linux. Install Automatix it will auto install flashplayer and loads more. It really is what converted me to Ubuntu
[http://www.getautomatix.com/](http://www.getautomatix.com/)  Good luck

---

### Post by Najand on 2006-09-14
Just use:
```

sudo apt-get install flashplugin-nonfree

```
Note that you need to have activate the universe repository in your sources.list. To do that, Click System -> Administration -> System Property and check all options. Then use:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by eppoh on 2006-11-08
Thanks Najand! I have been trying for days to get flashplayer installed in 6.04 without success until I read your post:-D 

Somehow on my laptop with edgy and Firefox 1.5, it took just a click when I went to a site that requires flashplayer, but not in 6.04

---

### Post by Najand on 2006-11-09
No Problemo! LOL

---

