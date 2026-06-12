---
title: "Stop VNC Service using ssh?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-16
Is it possible to Stop/Start the VNC server through SSH access? If so, how?

---

### Post by kelbizzle on 2007-03-16
[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

There you go.

---

### Post by scxtt on 2007-03-16
eh, vino and a (true) VNC server are different, IMO ...

i'd do this:

1. ssh into your box
2. type: vncserver -geometry 1280x1024 -depth 24
(note, you can use more or less anything for 1280x1024)

this will start a :1 connection (assuming no other VNC servers are running), and you can start subsequent ones the same way - giving you :2, :3, etc. ...

you can also use x11vnc to connect to your :0 connection (like vino does, but you DON'T HAVE TO BE LOGGED IN ALREADY from :0 - you can use SSH to start it and password protect it) ...

---

### Post by kvonb on 2007-03-16
If you want to server up the currently logged in desktop, and be able to re-login later, you need to use "x11vnc".

install with:

```
sudo apt-get install x11vnc
```

Next you should create a password for it: (sorry I forgot the actual command, but this will tell you)

```
man x11vnc
```

...use arrows to scroll up/down, and 'q' to quit.

Then run it with this command after you ssh into the sharing computer:

x11vnc -forever -display :0 -rfbauth /home/username/.vnc/passwd

Or simply copy the attached script files into your home folder.  There is one which enables you to login if you haven't enabled auto-login.

---

