---
title: "questions about beryl"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-06-23
I have just installed beryl on my Ubuntu Feisty with the KDE desktop. I was a bit disappointed with Beryl because it has removed the top of the windows which had the minimize, maximize and close buttons. Also the windows are stationary and cannot be dragged around the screen. Also when I rotate the cube, it only has a black background. In this video [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) The person has a background behind the cube, and the tops of his windows haven't disappeared and he can move the windows around. How do I configure Beryl to be able to do what the person has done in the Ubuntu part of the video in the link??:confused:

[Edit]The animation also goes too fast for me and I haven't had much luck trying to slow it down!

---

### Post by Gigzaholic on 2007-06-23
>     *
          o If when you start Beryl you find your windows have no title bar (with the minimise, maximise and close buttons) or borders, you may need to add the following line to the device section of the file /etc/X11/xorg.conf (See this page [http://forum.beryl-project.org/viewtopic.php?f=35&t=1631](http://forum.beryl-project.org/viewtopic.php?f=35&t=1631) for details): 

Option "AddARGBGLXVisuals" "True"

and change to

DefaultDepth 24  

in the "Screen" section.

Also if you are using a NVIDIA GeForceGo graphics card you may also need to add

Option "DisableGLXRootClipping" "True"

in the device section of your xorg.conf

If that still doesn't help you then right click on the beryl diamond icon by the clock and select advanced beryl options-rendering platform and choose "force AIGLX"

This should get everything going. 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

I think that should sort your problems.

---

### Post by Wake Rider on 2007-06-23
Thank you, now I have the title bars back. Just wondering, how do I start Beryl on startup? I can't find the preferences to select which programmes start on start up. My system preferences don't seem to be where the instructions say they will be. Also the cube is still set against a black background. How do I put a graphic BEHIND the cube as is in the video I posted??

---

### Post by Gigzaholic on 2007-06-23
to start up beryl, type the command: beryl-manager.

I don't have my linux installation booted up, so I can't tell you specifically where to go  in order to get the background graphic.

---

### Post by maddot on 2007-06-23
go to system>preference>sessions Then type in add and add beryl-manager

It's called a skydome, look for in in effects i think.

---

### Post by Wake Rider on 2007-06-23
> **maddot said:**
> go to system>preference>sessions Then type in add and add beryl-managerI

This worked for the Gnome desktop but not the KDE. There is no System > preference > sessions in KDE. How do I make beryl activate on startup in KDE? If the GUI won't do it then what is the command I need to type?

---

### Post by Wake Rider on 2007-06-23
How do I add a skydome??

---

### Post by avik on 2007-06-23
Using the Settings Manager (make sure you installed beryl-settings), go to Desktop->Desktop Cube->Skydome.  Then, just choose your skydome image.

---

