---
title: "Prob installing Smeg"
date: 2005-05-25
forum: Absolute Beginner Talk
---

### Post by dj.shenzou on 2005-05-25
Hello all. I installed Ubuntu just 2 days ago. My second try to get rid of Microsoft OS, I feel that with Ubuntu I can do it (good bye for ever Bill Gates).  I've already been able to install couple of programs, get familiar with terminal and GNOME, setup local network etc, so not bad beginning at all. Ubuntu seems wonderful and I will suggest it to my friends. 

But now I need your help - couldnt find a document to learn myself. I tried to install Smeg ([http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/) ), but no success. 
I get error:

# dpkg -i smeg.deb
Selecting previously deselected package smeg.
(Reading database ... 60229 files and directories currently installed.)
Unpacking smeg (from smeg.deb) ...
dpkg: dependency problems prevent configuration of smeg:
 smeg depends on python-xdg (>= 0.11); however:
  Version of python-xdg on system is 0.9-1.
dpkg: error processing smeg (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 smeg
#

Well, some dependencies seem to be missing, but it cannot be python-xdg since its version number is bigger that needed, right? 

I know there is another way to install Smeg, but dont know how to do it (but would like to learn that also). See: [http://dev.realistanew.com/smeg/installsmeg](http://dev.realistanew.com/smeg/installsmeg)
How do I run such a script? Where I have to copy-paste it, and how to run it?

---

### Post by Mez on 2005-05-25
apt-get install smeg

smeg is either in the main repository or in backports

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

So you can install directly via apt-get ;) which is a lot easier)

---

### Post by dj.shenzou on 2005-05-25
Thank you for help. Adding the Backports repository to /etc/apt/sources.list really helped. In no second Smeg got installed.

---

