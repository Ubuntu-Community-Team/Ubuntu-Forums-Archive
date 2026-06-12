---
title: "X server"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-05
Hello!
I broke it. So what can I type in the command line to bring up files to edit (or if it's totally broken, which I don't know yet, how do I reinstall it). I tried the tutorial [here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29"), and it got broken.
Thanks (I'm totally confused right now)!

---

### Post by blendmaster on 2006-10-05
Uggh, tried to do sudo dpkg-reconfigure xserver-xorg, but it pauses the program at the part where I select the color bits (I chose 24 the first time, but it didn't matter what I chose, it would force the program to quit, and then return to the command line). Any ideas?

---

### Post by james_san on 2006-10-05
type `sudoedit /etc/X11/xorg.conf`
look down through the start of that file and there is a line that says "to automatically regenerate this file, type `sudo dpkg-reconfigure xserver-xorg blahblahblah`. It has an extra option (-phigh if I remember correctly) that means the only question you get is what driver to use (and it takes a good guess first).
Also, if you rename xorg.conf (`sudo mv xorg.conf xorg.conf.broken`) and then type in `startx` to get the server running, it tries to start it with automatic settings. this may help to get back up and running for now.

---

### Post by blendmaster on 2006-10-05
Alright, I'll try this and see what I get.

---

### Post by Herman on 2006-10-05
The tutorial has you making a backup of your /etc/X11/xorg.conf file as the very first step, so I would guess that restoring your original /etc/X11/xorg.conf file should do the trick. 
Here is how you made the backup,```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```Here is what you probably need to do to restore it,```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` That should do it, you might also need to type 'startx', and/or reboot, I'm not sure. I hope that does the job for you.

Running 'sudo dpkg-reconfigure xserver-xorg' should also fix it for you, by writing you a brand new /etc/X11/xorg.conf file. It is supposed to drop back to the shell after you enter '24'  for the default color depth, because that is the last question.
Probably you just need to type 'startx', and it will be fixed! ```
startx
``` Here is an example web page for [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") in case you want to check that you are doing it okay, but I think you are, probably. :D
Regards, Herman :D

---

### Post by blendmaster on 2006-10-05
Okay, well, I tried james_san's first idea, and I found nothing in the file (hopefully I'm doing it right, but I've never run in command line based mode before). so I tried renaming the file sudo mv xorg.conf xorg.conf.broken, but it said that there is no such file. So then I got mad and just typed startx. It actually started x, but in a really bad looking environment. Now I'm in Linux, and I'm finding there is no restart or shut down buttons in the shut down menu. I have no clue why that is. I did Herman's idea, but I get replied with

> Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


I'm so confused. Thanks for sticking with me so far!

---

### Post by blendmaster on 2006-10-05
it says that after I say startx.

---

### Post by james_san on 2006-10-05
ok basically your xorg.conf file is missing, which is why its going so screwy.
at the command type `sudo dpkg-reconfigure xserver-xorg -phigh` (without the quotes). this should replace the file, then restart your computer (if it asks you which driver to use, you should be able to just press enter with the detected one)

---

### Post by Josey on 2006-10-05
If you messed with 'gdm.conf-custom' you may need to to do the following

```
sudo gedit /ect/gdm/gdm.conf-custom
delete this under [servers]

0=Xgl
 
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glxbuffer
flexible=true
```

---

### Post by blendmaster on 2006-10-06
Hello!
I fixed my gdm.conf-custom file to say what it originally says, and now I can at least get into the GUI. However, the diplay is not very good, and the screen is fixed in the wrong way (I have things going off the screen where I can't see them). It might be my gdm.conf now, because I look in it, and it has a bunch settings still there. Anyone know what might be the problem and how to fix it?
Thanks!

---

### Post by blendmaster on 2006-10-06
I'm so happy!:mrgreen: 
Got it fixed 100%!:mrgreen: 
I'm never messing with the xserver files again!

---

