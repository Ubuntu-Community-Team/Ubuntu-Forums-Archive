---
title: "making movies open in xine by default?"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-05-14
just wondering how to do that, and how to open mp3s in xmms by default. totem thing cant play anything properly on my machine

---

### Post by Gustav on 2005-05-14
[QUOTE=glandula]just wondering how to do that, and how to open mp3s in xmms by default. totem thing cant play anything properly on my machine[/QUOTE]
 You can install totem-xine.
This makes totem use xine instead of gstreamer.

Or you can right-click on a mp3/movie file, chose "properties" and "open with", then chose wich program you wish to open the file type with.

---

### Post by Knome_fan on 2005-05-14
1. You probably want totem to use the xine engine. To do that, simply do:
sudo apt-get install totem-xine.

2. To change the apps that open a file type, simply open nautilus, right click on a file of the type you want to change, select the last point in the list (should be something like settings, sorry I'm currently running a german system here) and then choose what application to use under the open with tab.

Also, take a look at the ubuntuguide, it should answer most of your question, especially when it comes to multimedia problems:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by glandula on 2005-05-14
outstanding. once again a big thank you

---

