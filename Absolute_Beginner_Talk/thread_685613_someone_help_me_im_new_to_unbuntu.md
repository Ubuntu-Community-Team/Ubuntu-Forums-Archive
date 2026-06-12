---
title: "someone help me im new to unbuntu"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by newone19 on 2008-02-02
i have a dell inspiron 1520 which i installed ubuntu yesterday. and i just got my wireless driver working this morning. but i found out that my audio driver did not work. i've tried using the guide from this post [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)  but still cannot get it to work.

anyone have any ideas how to fix my problem? :confused:

---

### Post by jan quark on 2008-02-02
please post the result of the terminal command
```

lspci
```

also have a look at system > preferences > sound

see my configuration what is yours

---

### Post by candtalan on 2008-02-02
Welcome! Well done for getting it installed and working.
You do not say which version  of Ubuntu you are using - is it the latest version 7.10?
The link you suggest you have been trying seems to be related to the earlier version Ubuntu 7.04.

Did you install it from the live CD? If you have the live cd available I would try it with the live cd to find out what the sound does when the live cd is being used also. You would usually find that the later version will work better and in more machines. And of course, get all of the available updates too for your installed system, before troubleshooting.

FWIW I often use the kubuntu approach (note1) and I see there is a system settings>sound system>test sound facility which I have found always works to bring back my sound when it has been temporarily borked for some reason. Might be worth considering if a solution for ubuntu here is slow to appear.

Note 1:
internet connection
synaptic package manager>search kubuntu-desktop
request install
apply

When all downloaded and installed automatically, log out, choose session kde,
login again 
use the kde menu system settings, sound system, test sound.

good luck

---

