---
title: "please, help!"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-03-29
Which packages and plugins are needed to play asx streaming?

---

### Post by Doug11 on 2007-03-29
> **linux-beginner said:**
> Which packages and plugins are needed to play asx streaming?

First, I would download Automatix2, for a begeinner, that is the easiest way to get all your codecs and plugins (restricted and non-resricted). Can't remember the exact name of the site, just google  >get automatix< and that should do it for you. It's a pretty good site.

---

### Post by xyz on 2007-03-29
Do you have all the codecs...w32 among other things?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Automatix or Easy Ubuntu do it,too.

---

### Post by linux-beginner on 2007-03-29
yes, I think.
I have also tried Automatix2 but It couldn't help me.
If I play this streaming:
[http://switch.streamgate.nl/cgi-bin/streamswitch?streamid=42&a=.asx](http://switch.streamgate.nl/cgi-bin/streamswitch?streamid=42&a=.asx)
I don't get any error message but I don't also have sound!
Why? What is wrong?

---

### Post by Obor on 2007-03-29
> **linux-beginner said:**
> 
If I play this streaming:
[http://switch.streamgate.nl/cgi-bin/streamswitch?streamid=42&a=.asx](http://switch.streamgate.nl/cgi-bin/streamswitch?streamid=42&a=.asx)
I don't get any error message but I don't also have no sound!
Why? What is wrong?
It plays on my firefox just fine. I'm using Totem Browser Plugin 2.18.0. [How to install here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Totem.29_with_plug-in_for_Mozilla_Firefox")

---

### Post by linux-beginner on 2007-03-29
I think i's just the problem! I can't intall totem-gstreamer-firefox-plugin on my Ubuntu 7.04!
this is what i did:
> mehdi@mehdi-desktop:~$ sudo apt-get install totem-gstreamer-firefox-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting totem-mozilla instead of totem-gstreamer-firefox-plugin
totem-mozilla is already the newest version.
The following packages were automatically installed and are no longer required:
  libgmp3c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

