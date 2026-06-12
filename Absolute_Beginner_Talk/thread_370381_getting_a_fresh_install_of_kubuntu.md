---
title: "getting a fresh install of kubuntu"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by qiemem on 2007-02-25
Just installed Kubuntu for the second time. The first time I did, I was quick to rearrange all of the panels, and explore all the configuration options and such, but winded up back with gnome, completely uninstalling it (via aptitude). I decided to give it a second chance, but I'd like the default configurations on the panels and all settings; essentially a fresh install. Upon reinstalling though, everything was how I had before, which I suppose is a good thing, but still. So I tried aptitude purge to get rid of all the config files and such, but that didnt work either. Anybody know of a way to do this?

---

### Post by ed-j on 2007-02-25
If you go to the options in the bottom left of your login screen, look for the option about changing the session. You should get an options screen that gives you the choice of which OS to boot into.

Failing that, if you go to _[www.psychocats.net/ubuntu/index](www.psychocats.net/ubuntu/index)_ there is a truly excellent walk-through of the KDE installation process. All the best!

---

### Post by qiemem on 2007-02-25
Oh, perhaps I wasn't clear.

I'm not having any trouble installing Kubuntu or booting into that. I'm just wondering how to reset all of my settings in it. I would like the default kubuntu set up, getting rid of all the panel  changes I've made.

Thanks though.

---

### Post by ed-j on 2007-02-25
My fault, sorry, I didn't notice your OS description and I got the wrong end of the stick. If no-one answers, perhaps try at *[https://bugs.launchpad.net/bugs/?loggingout=1](https://bugs.launchpad.net/bugs/?loggingout=1)* Best I can do, sorry for the confusion.

---

### Post by qiemem on 2007-02-25
Hey, no need to apologize. Its kind of a weird question.

Its not really a bug though either, but thanks for the link. I just need a way to wipe the kde config files from my system so I can do a fresh install and get all the default settings. Unless there's a better way.

---

### Post by gwpritch on 2007-02-25
```
rm -r ~/.kde/
``` 

Log out then log in again.

---

### Post by qiemem on 2007-02-26
Perfect, exactly what I was looking for. Thanks!

---

