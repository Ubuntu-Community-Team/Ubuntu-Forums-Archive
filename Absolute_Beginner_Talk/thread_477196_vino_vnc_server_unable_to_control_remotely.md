---
title: "vino vnc server unable to control remotely"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by rangans on 2007-06-18
hi guys,
            I turned the remote desktop feature inside ubuntu and I also checked Allow Remote users to Control your desktop option. I am able to view the session remotely on my windows laptop but no inputs respond. Also the top panel with menus is not present but my desktop with all icons and any running applications is displayed. 
I tried with tight and real vnc viewer same problem. I have and I am able to run vnc on display 1. But I want the display 0 for an application which runs only if it a local display server. So i run it on my desktop and then vnc to it to control it remotely. This way the application works and I can confirm it becos when I view from the remote system the application does not quit. But I am not able to control with or without the application running just the display 0 alone. Any help is greatly appreciated. Thanks.

---

### Post by tbone844 on 2007-06-18
I think I'm having a similar problem.  When I try to access my Ubuntu box from my Windows XP Pro work PC it displays the screen.  I can move the mouse around, but if i click or type anything, the screen doesn't update.  I literally have to disconnect the VNC Viewer session, and start it back up to see the update.

i.e.,  if i remoted in now, i'd see the remote screen as it is 'now'.  if i double click terminal, nothing changes.  If i disconnect and reconnect, i can then see that terminal loaded.  w00t.  But no one can expect this to be functional.

Used Synaptic Package man to install VNC Server, set password, and that's it.  Using RealVNC or TightVNC viewer have same effects.  

PS shouldn't I be able to MSTSC into the workstation if I've setup Remote Desktop?  Can't do that either.

---

### Post by Y2J on 2007-06-26
I have the problem right now, VNC opens news sission, which I don't want ..
Any ideas ...

---

### Post by lazyart on 2007-06-26
You need to 

- turn off desktop sharing, 
- install x11vnc from synaptic, then start it like this:

x11vnc -noxdamage -forever -passwd *password*

password is optional.  Add it to your startup (system>preferences>sessions).  This is a side effect from using desktop effects/beryl.  Now the screen should update when you connect remotely.  And no, MSTSC won't work going to a linux box.  Wrong protocol.

---

### Post by peterc_ubun on 2008-02-28
> **tbone844 said:**
> I think I'm having a similar problem.  When I try to access my Ubuntu box from my Windows XP Pro work PC it displays the screen.  I can move the mouse around, but if i click or type anything, the screen doesn't update.  I literally have to disconnect the VNC Viewer session, and start it back up to see the update.


Check out this thread:
[http://ubuntuforums.org/showthread.php?t=132625&page=2](http://ubuntuforums.org/showthread.php?t=132625&page=2)

It might have something to do with having Desktop Effects enabled.  Try disabling that feature and it might work properly.

gl

---

