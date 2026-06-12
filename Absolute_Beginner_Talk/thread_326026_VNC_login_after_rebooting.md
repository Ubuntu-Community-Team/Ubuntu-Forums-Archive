---
title: "VNC login after rebooting"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by seasteve on 2006-12-26
I have a PC with 6.06 loaded.  It's in a remote place without a keyboard, mouse, or monitor connected.  I use VNC to connect to it.  Often, after updating, the OS needs to rebooted.

How can I create an automatic user login so I can use VNC to remotely login after a "local" has happened.

---

### Post by fjdowney on 2006-12-28
seasteve,

i have the same problem.  until i get a better solution this is what i did.

System->Administration->Security

Enabled Automatic Login

frank

---

### Post by seasteve on 2006-12-28
I knew there had to be a simple setting.

Thanks.

---

### Post by joshov on 2007-07-19
I've been looking around, is there a better way to do this?  By the way I'm using Feisty, as this post is from a while back.  Thanks.

---

### Post by Rocket2DMn on 2007-07-19
Why do you want it to automatically login?
You can set it up so a vncserver is booted for a particular user on boot, or you could ssh in and boot a vncserver manually.
If you have programs that need to run in the background, it can also be set to have the load with the computer and not with a login.

---

### Post by joshov on 2007-07-19
Ok that makes sense.  But, when I load vncserver from putty, then vnc to the machine, it gives me a blank desktop.  How do I log-on to an active desktop, as the user I want???

---

### Post by Rocket2DMn on 2007-07-19
If you login over putty/ssh under the user you want, the vncserver will be created for that user when you issue the "vncserver" command.
You then open your vncviewer and type in the ip : port (no spaces) and give it your password.  You should then have your desktop as the user you want.
If you are getting a window with a terminal in it in the viewer, you need to edit the file XSTARTUP in $HOME/.vnc/  the kill the vncserver and restart it.
I don't understand what you mean by blank desktop, is it just black and you have no mouse or anything?

---

### Post by joshov on 2007-07-19
It's just my wallpaper, no start bar, no icon's, nothing but the wallpaper.

---

