---
title: "Can't Login using gnome"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by allohakdan on 2006-10-17
Hi

So I had Ubuntu Dapper working just fine on my computer until this morning. A few weeks ago I figured out how to put an XGL Session option on my login screen, installed beryl, and upgraded the drivers for my Nvidia GForce3 Card. That was all running fine. No problems. But then last night there was a power outage and i guess my computer didnt shutdown correctly or something because now when i turn the computer on it will boot fine until i get to the login screen. when i put my username and password in, it pretends like it is starting gnome/xgl/gnomefailsafe and it will start to load and then all of a sudden, it takes me strait back to the login screen. I managed to get it to start it failsafe-terminal and start gnome by typing sudo gnome-session. when i did that gnome started up only this time i could see some stuff from the terminal and i noticed it said something about:

gdk_pixbuf_scale_simple: assertion 'dest_width >o' failed
libnotify-Message: Unable to get session bus: Unable to determine the address of the message bus

and there is this popup window that says:
**Power Manager**
This program cannot start until you start the dbus *session* service. This is usually started automatically in X or gnome startup when you start a new session.

Could someone please help me?!

---

