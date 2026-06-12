---
title: "Connecting remotely to Ubuntu on OS X (X11)"
date: 2008-01-28
forum: Apple Intel Users
---

### Post by Eluzion on 2008-01-28
I have an Ubuntu server setup which I can access through SSH just fine. However, I'm trying to access it through X11 on OS X Leopard. It loads up fine and I can initially see everything, but everything except the wallpaper of Ubuntu disappears so all I'm looking at is the wallpaper that is covering everything in OS X except for the menubar and dock. Any ideas what's going on? Thanks.

I have X11Forwarding enabled.

---

### Post by empthollow on 2008-01-28
From what i understand, you set up the remote desktop in system -> Preferences -> remote desktop.  
you then are trying to connect from osx to control your ubuntu desktop.  correct me if i am wrong in these conclusions.  i have the remote desktop setup on my ubuntu system and use vncviewer2.0.1 for my mac and i have no problems.  not sure what client you are using to connect to ubuntu.  i am using tiger.

---

### Post by Eluzion on 2008-01-28
Hey,

Leopard comes with X11 installed by default. I'm trying to run the gnome-session through X11. I have tried the following through X11.

ssh -X [email]username@xxx.xxx.xxx.xxx[/email]

gnome-session

And also

ssh -Y [email]username@xxx.xxx.xxx.xxx[/email] gnome-session

The first method will load the Ubuntu desktop but, like I mentioned, everything disappears except the wallpaper so I can't do anything. The second method doesn't work at all but if I try to load just a single program like Firefox, it works.

---

### Post by empthollow on 2008-01-28
i'm not sure this is the functionality for x11 you are looking for but you try putting "gnome-session" in the xinitrc file.  this would make it so that every time you start x11.app gnome-session would be invoked automatically  just like when x11 starts on linux.

---

### Post by cyberdork33 on 2008-01-28
I think you have to enable remote login for gdm

---

### Post by Eluzion on 2008-01-29
Remote login is enabled.

Everything appears to be connecting just fine. I can see everything initially for about 2 seconds then everything disappears except the Ubuntu wallpaper. I'm guessing it's a problem with X11 on Leopard or some setting.

---

### Post by el.duderino on 2008-03-24
hi there. 
i got exactly the same problem, an yes, it seems to be a leopard x11 problem. all other howtos  regarding the ssh-forwarding of a gnome-session to a mac are written for tiger. since leopards x11 has been completely different to tigers x11, there's a problem with forwarding the entire gnome-desktop (starting single ubuntu-apps in a winow just works fine).

it would be really really great if ANYONE had a workaround for this!

---

### Post by appelappe on 2008-07-20
> **el.duderino said:**
> hi there. 
i got exactly the same problem, an yes, it seems to be a leopard x11 problem. all other howtos  regarding the ssh-forwarding of a gnome-session to a mac are written for tiger. since leopards x11 has been completely different to tigers x11, there's a problem with forwarding the entire gnome-desktop (starting single ubuntu-apps in a winow just works fine).

it would be really really great if ANYONE had a workaround for this!

Hi all!

I had the same problem. I found this page on my surf for a solution. I have now elsewhere found something that worked for me. Even though I guess the guys in this thread has found their answer, I post my findings for the next guy like me:

```
$ Xnest -geometry 1024x768 :1& DISPLAY=:1 ssh -X <HOST> gnome-session

```
So, by usin Xnest you avoid the problem, and get a nice litle window to manage your ubuntu desktop.

---

