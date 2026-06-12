---
title: "[SOLVED] Update &amp;amp; Package Manager Error"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by bbcg on 2007-07-06
Update Manager got shut down in midst of update, now it and package manager says
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." when trying to do updates.

I do not know how to use console to get to that command as superuser, nor do I know what to do once I get there, please help ?

---

### Post by abn91c on 2007-07-06
open the console and type dpkg --configure -a the follow the onscreen prompt,it may ask you to type other commands, just be careful they will be case sensitive

---

### Post by testube_babies on 2007-07-06
Applications -> Accessories -> Terminal

Type in```
sudo dpkg --configure -a
```  Enter your password (it won't look like anything is being entered, but it works) and hit enter.  You should be good from there.

---

### Post by abn91c on 2007-07-06
it will look something like the attached snapshot

---

### Post by bbcg on 2007-07-06
OK, got this in respone to the commands, just found su command on another post.

dpkg: dependency problems prevent configuration of gimp:
 gimp depends on gimp-data (= 2.2.13-1ubuntu4.2); however:
  Package gimp-data is not installed.
dpkg: error processing gimp (--configure):
 dependency problems - leaving unconfigured
Setting up automatix2 (1.1-4.10-7.04feisty_i386) ...
Errors were encountered while processing:
 gimp


How do I remove gimp and re-install if package manager will not run ?(assuming that is the issue).

---

### Post by testube_babies on 2007-07-06
It looks like this should solve it:
```
sudo apt-get install -f
```

---

### Post by abn91c on 2007-07-06
sudo apt-get gimp-data

---

### Post by bbcg on 2007-07-06
Package manager is running now, I will try to uninstall gimp and go from there, does that seem correct ?

---

### Post by bbcg on 2007-07-06
sudo apt-get install -f
appears to be working
I appear to need to study up on command line linux, just need to learn the commands, used to be pretty good at Basic, ha ha

---

### Post by bbcg on 2007-07-06
Thank you for your assitance, I appreciate it much, especially quick in this day and age.:popcorn:

---

