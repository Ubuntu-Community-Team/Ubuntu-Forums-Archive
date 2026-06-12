---
title: "remote login"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Homie Bongo on 2007-04-05
Hi all, I am looking for a way how to remotely log into another Ubuntu box. I have tried the Krfb / Krdc applications combo from KDE, but those offered only a limited windowed access onto the other desktop.

I'd like to use full potential of my workstation using my laptop only as an input/output device for it, so that I could for example play 3D games or work completely on the other computer doing administration stuff etc. over the ethernet. Is such a thing possible? What should I look for, is it what they call remote access? thx for any help

---

### Post by nhandler on 2007-04-05
There are a few possibilities. One is vnc. A vnc server is packaged by default with ubuntu. go to System->Preferences->Remote Desktop to enable it. I recomend setting a password. Now type 'vncviewer xxx.xxx.xxx' Where the x's represent the ip address. This should give you full control (Once you enter the password). However, depending on your internet connection, you might notice some lag that might interfere with playing the games.

Another method that I'll mention (in case you happen to need it) is ssh. This will allow you to connect to another computer. However, unlike vnc, you only have access to a terminal. I won't go into much detail now because I believe vnc should accomplish what you are trying to do. If you want more information on ssh, just ask.

---

### Post by jhorning on 2007-04-05
The problem with VNC is that you are connected to the desktop of the logged in user and you must leave the computer logged in. 

I found NX to work very well and you will log into a new session (like terminal services in Windows). Also seems faster then VNC

You can find instructions for installing it here.
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX](http://ubuntuguide.org/wiki/Ubuntu_dapper#Remote_Desktop_Access_via_NX)

---

### Post by Homie Bongo on 2007-04-06
Thank you guys, the NX looks promising!

---

