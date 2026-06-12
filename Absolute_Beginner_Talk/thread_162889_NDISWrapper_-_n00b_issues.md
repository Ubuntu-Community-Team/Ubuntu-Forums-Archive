---
title: "NDISWrapper - n00b issues"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Trinity_Quasar on 2006-04-19
I'm in the directory, and I type "make" and I get 
"Can't find kernel build files in /lib/modules/2.6.10-5-386/build; 
   give the path to kernel build directory with
   KBUILD=<path> argument to make"

I have no idea what this means, this is my first time playing with Ubuntu, I'm running it from a LiveCD of version 5.04 given to me by a friend. I'm not sure if it's due to the fact I'm using the LiveCD, but any help anyone is willing to throw my way will be greatly appreciated.

---

### Post by brentoboy on 2006-04-19
just get it from the repo.
(its in the universe)

---

### Post by FizDev on 2006-04-19
[QUOTE=brentoboy]just get it from the repo.
(its in the universe)[/QUOTE]

To do this, type in a terminal :
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by Trinity_Quasar on 2006-04-19
Done that, it requested the CD. Done. Now I'm not sure what to do. (Trying from the beginning again get's the same issue)

---

### Post by brentoboy on 2006-04-19
you dont need to "make" it anymore (make just builds a binary that works on your kernel) the copy from the repo put the binaries where they go.

Its been a few years since I used ndis, but is seems like you need to
The wiki has a nice writup on getting ndiswrapper working.

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

you are at step 2.2.1 (I think)

---

### Post by Sandlst on 2006-04-19
Also if you want a nice GUI for ndiswrapper you can do ```
sudo apt-get install ndisgtk
``` It installs to (System/Administration/Windows Wireless Drivers)  note that this will remove the other ndiswrapper package.

---

