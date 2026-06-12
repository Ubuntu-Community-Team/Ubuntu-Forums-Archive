---
title: "vncserver config help"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by getut on 2007-06-08
Please help.. I got vncserver installed but doing just sudo aptitude install vncserver.

I figured out how to run it and set the default password, but I have a configuration issue. VNC keeps connecting me to a fresh X session.

I vncserver to always display the active local X session so that I can see the desktop items for the person who is logged on to the machine locally. How can I configure it to do this?

---

### Post by stami on 2007-06-08
Did you try vino?? Vino is a vnc server for Gnome. You can configure it from your menu
System -> Preferences -> Remote Desktop

Bye

---

### Post by getut on 2007-06-08
Imagine that.. built right in... who'd a thunk it.

I am so Microsoftized that I had seen the remote desktop item before and just assumed it was running on Microsoft's terminal services/remote desktop protocol. I didn't know it was built on VNC codebase.

That got it.. Thanks!!!

---

### Post by getut on 2007-06-08
Whoops.. spoke too soon.

Vino doesn't start as a service.

I also need to be able to sign on with the vncviewer if the user hasn't already.

I'm trying to use the machine as a very small lightweight place to run vmware images. If it isn't signed on, I need to be able to sign on with VNC... in a session viewable by a local user if there is any... as well as vice-versa... if the local user is already signed on, I need to see the vmware images running in that session.

---

### Post by getut on 2007-06-08
Finally found it.

x11vnc was the answer to my problem. It can connect to the ACTIVE X session while the login manager is active and then carry over into the newly created users X session.

---

