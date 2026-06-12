---
title: "after reinstalling Feisty, errors update manager, etc"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by CRIMPS on 2007-04-30
I just finished a clean install of Feisty (i386) because I just couldn't get anything to work with 64bit.  Now, after trying to update and install nvidia drivers I got an error stating something to the effect of "broken package".  Now, after rebooting, I tried to run update manager and I get this error: 

[http://ubuntuforums.org/attachment.php?attachmentid=31355&stc=1&d=1177969051](http://ubuntuforums.org/attachment.php?attachmentid=31355&stc=1&d=1177969051)

What does this mean.  I also started getting errors when I was trying to use synaptic to download nvidia drivers.  

Help would be appreciated.  

Thanks
Z

---

### Post by taurus on 2007-04-30
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by CRIMPS on 2007-04-30
Resolved!!!

Kind of interesting...I started looking through the repositories and, under the updates tab I saw about 20 or 30 third party software sources... all of which were for breezy badger!!!  How does this happen?

Anywho

Thanks

Z

---

### Post by taurus on 2007-04-30
Did you happen to install any third party software like Automatix or something like that?

---

