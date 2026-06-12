---
title: "video streaming"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by trebor on 2006-09-04
Ok, forgive me if this does not sound right.  I have been up all night trying to figure this out. Between downloading installing and compiling I almost got everything to work, that is totem will now play all the diferent codecs that I need.  My only problem is I cannot get fire fox to stream video.  Before you start to tell me what to do, please take in mind that I am a noob.  I only just inatalled unbuntu about a week ago.  In that time I have done quite a lot with it to get it to do what I want. So I have figure out a bit what to do, just I need things spelled as to how to go about fixing this problem.  Please help.

---

### Post by meborc on 2006-09-04
i strongly advise to read the dapper guide in my sig... just search for firefox and see how different plug-ins are installed...

have fun :mrgreen:

---

### Post by Fedz on 2006-09-04
Not the official way I fear but, I did the following ...
**[Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://www.ubuntuforums.org/showthread.php?t=202537)**
*See the Mplayer plugin*

I then just went and installed the codecs using Ubuntu nstaller.

Works like a dream on my system AMD64. Very impressed.

---

### Post by rohan! on 2006-09-04
if you're using totem then you need to install the totem-gstreamer-firefox-plugin. To do this you need to open a terminal and enter ```
sudo apt-get install totem-gstreamer-firefox-plugin
``` after this is installed restart firefox and it should work.

---

### Post by trebor on 2006-09-04
> **meborc said:**
> i strongly advise to read the dapper guide in my sig... just search for firefox and see how different plug-ins are installed...

have fun :mrgreen:

I have tried that how to, but it seems to be missing some steps or I am being a noob basically I do not understand completly what to do.  It did help me to install the nessacary codecs, which allowed me to play what I want just not stream as I said earlier.

---

### Post by trebor on 2006-09-04
> **rohan! said:**
> if you're using totem then you need to install the totem-gstreamer-firefox-plugin. To do this you need to open a terminal and enter ```
sudo apt-get install totem-gstreamer-firefox-plugin
``` after this is installed restart firefox and it should work.

yup i have done that as well.  as well as going into add remove and making sure all all gstreamer 10 for drapper were installed.

---

### Post by jslmsca on 2006-09-07
sudo apt-get install totem-gstreamer-firefox-plugin

produces the following error message:

The following packages have unmet dependencies:
  totem-gstreamer-firefox-plugin: Depends: totem-gstreamer (= 1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed
E: Broken packages

Anyone with an idea of how this can be fixed?

---

