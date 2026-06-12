---
title: "can't find the 915resolution package"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by phu5ion on 2007-02-10
I know this is constantly covered, and I've tried everything I can to keep from having to make another post about installing the Intel 855/915 patch.  

I've just installed Ubuntu 6.10 on my Dell 700m and I'm trying to follow the sets as described at this site: [http://www.server-guy.com/linux-articles/dell-inspiron-700m/]("http://www.server-guy.com/linux-articles/dell-inspiron-700m/")

I've tried using the GUI tool and apt-get but can't find 915resolution, this is what apt-get returns:

> phu5ion@phu5ion-laptop:/etc/default$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 915resolution


If I get the source and run make install I don't have the config file (915resolution) that is supposed to be in /etc/default.  

Any other ideas?  My knowledge of Linux is pretty rudimentary, so please talk slowly and use small words. :D

---

### Post by jordanmthomas on 2007-02-10
```
gksudo gedit /etc/apt/sources.list
```
In it there are lines that start with a # like this
```
# deb *blah*
```
These lines are skipped when apt-get reads the file.  
915resolution is in the *universe* repository, which is commented out by default
What you need to do is go through the file and take out the # of lines that say ```
# deb *blah*
``` so they will look like ```
 deb *blah*
```
Then, save and close gedit.
```
sudo apt-get update
sudo apt-get install 915resolution
```

This help any?

---

### Post by r4ik on 2007-02-10
Try,
    * To get the higher resolutions the package "915resolution" installed.
    * Your graphics driver is an i810

Using Synaptic Package Manager search for i810 and check that you have a driver installed. I'm pretty sure you will have.

Next search for "915" and you should see 915resolution. Install this.

Easiest thing to do next is just to reboot. If you are more adventurous (and know to use Ctrl+Alt+F1 to get a command prompt to reboot out of difficulty):

    * Use AltF2 to bring up the run command window. Run the command:
    * sudo /etc/sbin/915resolution
    * Close everything that you want to save and restart X windows "Ctrl + Alt + Bksp"


Good luck.

Credits "veloce"

---

### Post by jordanmthomas on 2007-02-10
> If you are more adventurous (and know to use Alt+F1 to get a command prompt to reboot out of difficulty):
wouldn't that be <ctrl><alt>F1 ?

---

### Post by r4ik on 2007-02-10
Correct edited thank you.

---

### Post by phu5ion on 2007-02-10
jordanmthomas, thank you.  Yeah once I uncommented the 'universe' repository i was able to install the 915resolution package.  followed the rest of the instructions as described by server-guy and I have high-res widescreen love.

Thanks again.

---

