---
title: "Remote Desktop"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-08-08
Ok I have a laptop that is i have set up to dual boot Ubuntu and Windows XP...

I have recently been given an older HP computer that had 128MB ram and I am going to put Xubuntu on it...

I was wondering because I do not have the room for another monitor/keyboard/mouse if it was possible to access it on my laptop... 

How would I be able to do this...

---

### Post by Depressed Man on 2007-08-08
Yes there is. Once you load Ubuntu on there if your using Gnome you just have to setup remote desktop. 

Applications > System > Administration > Remote Desktop


Check the boxes for allow other uses to see your desktop and control it. And put a password on there (well this is optional but I like security and wouldn't want anyone controlling my desktop!). The asks for confirmation means that whenever anyone tries to remote desktop to your HP you'd have to get on your HP to approve it. Since you don't want it to have a keyboard and mouse I would turn this off (uncheck the box). 

After that you can get into your HP box by typing in the command they gave you from that window for Ubuntu. 

It would be something like 

vncviewer hostname:0

Then if you want to access it from XP you would need to install a VNC client like tightvnc. I don't know how to use XP Pro's built in remote desktop to connect to this. But from there I believe you can remote desktop into your HP box with the ip address.

---

### Post by Technoviking on 2007-08-08
Set up VNC.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

---

### Post by Depressed Man on 2007-08-08
Or that. 

I really should get use to looking at the Wiki :)

---

### Post by HermanAB on 2007-08-08
One word: ssh

VNC works but is kinda the Windozy way to do things.  In contrast SSH allows you to log in remotely and run programs directly without wasting time with a desktop.  Using ssh, you could even run the gnome-panel or KDE kicker to get the menus, without having to bother with the rest of the desktop.

Cheers,

Herman

---

### Post by Depressed Man on 2007-08-08
Interesting. I currently use remote desktop and VNC. The reasoning behind it is because I want to control my desktop's media player. So my laptop logs me into my desktop and I change the playlist around. 

But if I SSH into it, wouldn't that just mean I launch the program from my desktop box onto my laptop?

---

### Post by silent1643 on 2007-08-08
im still waiting for logmein to release a version for linux desktops

[promising news however]("http://jkontherun.blogs.com/jkontherun/2007/08/logmein-offers-.html")

---

### Post by HermanAB on 2007-08-08
SSH runs by default on almost all Unix systems.  It is also usually by default configured to forward X.  The advantage of SSH is its versatility - it can do much more than just forward a desktop system.  It is also secure - the channel is encrypted with strong encryption.

You can use SSH to forward the whole desktop system just like VNC does, but that is generally not a good idea.  You can also run VNC over SSH in order to use SSH encrypt the VNC channel.  The best way to use it though, is to simply log into the remote machine and then run whatever program you want:

$ ssh joesoap@1.2.3.4
Password: whatever
$ (this is the prompt from the remote system)

Now you can run anything at all, for example gedit to edit a file:
$ gedit filename &
(The editor will run on the remote machine, but the X windows dialogues and mouse clicks will be forwarded.  It will seemingly be just the same as if it is running on your local machine, except that it isn't).

You can even do this from Windoze.  Install Greenend PuTTY or Cygwin, then log into a Linux machine and run a Gnome or KDE application, or run gnome-panel to get all the Linux menus and go nuts.

So in short, since SSH is already installed, you don't have to do anything - just log in and go for it, while with VNC, you have a long winded installation and configuration rigmarole and then it doesn't work all that well anyway.

To speed ssh up a bit, you can select a faster encryption mechanism, for example:
$ ssh -c blowfish-cbc joesoap@1.2.3.4

Cheers,

Herman

---

