---
title: "[SOLVED] kdeinit4 cannot start"
date: 2008-09-02
forum: Arch and derivatives
---

### Post by erickghint on 2008-09-02
So I finished the install, and after some thought on DE, I decided to go with KDE. I'm using Gnome in Ubuntu, and wanted to try something different. After installing KDE, I can get to the login screen, but after that I get a small pop-up that states ```
Could not start kdeinit4. Check your installation.
```

   I'm using the current recommended drivers from nVidia, and I really don't know where to go from here. I've spent quite a bit of time trying to research the answer, and I've come up with nothing. I've seen other people with the same or similar problems, however I can't find a workaround. Most people have either fixed it and not stated how, or the solutions that I've found don't work. If for any reason there isn't a viable solution, can I just remove everything with pacman -Rc , or do I have to uninstall it via another method, and go with say... xfce? Any and all help would be much appreciated.

---

### Post by &amp;wP*!) on 2008-09-06
> **erickghint said:**
> So I finished the install, and after some thought on DE, I decided to go with KDE. I'm using Gnome in Ubuntu, and wanted to try something different. After installing KDE, I can get to the login screen, but after that I get a small pop-up that states ```
Could not start kdeinit4. Check your installation.
```

   I'm using the current recommended drivers from nVidia, and I really don't know where to go from here. I've spent quite a bit of time trying to research the answer, and I've come up with nothing. I've seen other people with the same or similar problems, however I can't find a workaround. Most people have either fixed it and not stated how, or the solutions that I've found don't work. If for any reason there isn't a viable solution, can I just remove everything with pacman -Rc , or do I have to uninstall it via another method, and go with say... xfce? Any and all help would be much appreciated.
Hi Erick, I had exactly the same problem. This is related to desktop environment KDE, not Linux.

[LIST=1]
[*]Login in failsafe mode first. To identify desktop environment problems, kdm in DAEMONS entry of /etc/rc.conf must be disabled (by adding ! character in front of **kdm** in **DAEMONS** entry). Save the file. Go next step.

[*]Reboot. Now in this case if you login, you will get command line session. Just start```
startx
```You will get the messages from X server, to see where the problem is.

The problem is, some ssh program integrated in KDE could not load a special version of shared library libxml2 or whatever. Repository must be updated to clean such a kind of version mismatches between the programs in Linux. See below.

[*]To solve such problems, right after```
pacman -S kde
```The complete package repository must be updated:```
pacman -Syy
pacman -Syu
```Take the change in /etc/rc.conf I told you above, back, ie. remove ! character in front of the kdm. 

To all these things in the previous session (command line).
[*]Reboot. Try to login again. You will see the problem vanished.
[/LIST]
I know, this is not addressed in any document in the world. Nothing is perfect, as you can see..

---

### Post by erickghint on 2008-09-08
Thank you so much :)

---

