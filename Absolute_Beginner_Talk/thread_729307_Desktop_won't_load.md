---
title: "Desktop won't load"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kei-clone on 2008-03-19
So, I just installed my gutsy gibbon on my computer last night, and after installing literally 200 updates, I told terminal to shutdown +25 and went to sleep.

When I woke up, the computer was not powered off (because I forgot to add +P to the shutdown command) but it was in bash, so I typed "reboot" into bash, and everything was fine until I got to the ubuntu login screen. After typing my username and password, I get to the default gnome orange background, but nothing loads.

I try to figure out what's going on by ctrl + alt + F1. No error output there. Using "top" showed me that the only process that was active was "init". I can't figure out what's going on, but I can still access the linux partition from Windows, which is where I'm typing this post.

someone plz help?

---

### Post by kei-clone on 2008-03-19
bump?

---

### Post by NightwishFan on 2008-03-19
try this in command line
```
sudo apt-get update
```
if it asks you do any commands, add sudo in front of them and type them.

---

### Post by kei-clone on 2008-03-19
lol wow I can't believe it was that easy. thanks :)

---

### Post by NightwishFan on 2008-03-19
No problem. :KS:popcorn::KS

---

### Post by unutbu on 2008-03-19
Um, NightwishFan, would you please explain why sudo apt-get update works?

---

### Post by NightwishFan on 2008-03-20
It basically corrects anything that might have failed with the updates.

---

### Post by unutbu on 2008-03-20
In what way does apt-get update correct things? I thought all it did was update index files so the machine knows where to go to get packages. 

The man page (apt-get(8)) does not help me understand either:

> 
           update is used to resynchronize the package index files from their sources.
           The indexes of available packages are fetched from the location(s) specified
           in /etc/apt/sources.list. For example, when using a Debian archive, this
           command retrieves and scans the Packages.gz files, so that information about
           new and updated packages is available. An update should always be performed
           before an upgrade or dist-upgrade. Please be aware that the overall progress
           meter will be incorrect as the size of the package files cannot be known in
           advance.



---

### Post by NightwishFan on 2008-03-20
Yeah. He must have had an error with that somehow.

---

