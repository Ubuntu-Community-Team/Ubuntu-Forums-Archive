---
title: "Remote Desktop?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-30
What is remote desktop? Does it come with ubuntu 7.10? Can I use it to control someone else's desktop over the internet?

I hope to accomplish the following...

1. Control another desktop from my Ubuntu 7.10 install (both are Ubuntu 7.10)
2. Allow them to view what I am doing while I am doing it

I have read about VNC and other things, but would that allow me to control their desktop while they can witness it all?

[http://ubuntuforums.org/showthread.php?t=135036&highlight=Remote+Desktop+howto](http://ubuntuforums.org/showthread.php?t=135036&highlight=Remote+Desktop+howto)

Would ^^ satisfy my needs?

---

### Post by Corbin D on 2007-10-30
Ubuntu has both features built in, though you'll have to enable the sharing of your desktop in the System settings (sorry in Windows right now, don't remember the exact name).

You can both share your desktop and control someone else's using the default VNC installation.  I did it last night to help someone with Ubuntu, believe it or not.

You will have to configure any firewalls and routers on both sides so that person's VNC server can be contacted and connected to.  It's usually port 5900.

---

### Post by jonobr on 2007-10-30
CHeck this

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

---

### Post by Onay on 2007-10-30
> **Corbin D said:**
> Ubuntu has both features built in, though you'll have to enable the sharing of your desktop in the System settings (sorry in Windows right now, don't remember the exact name).

You can both share your desktop and control someone else's using the default VNC installation.  I did it last night to help someone with Ubuntu, believe it or not.

You will have to configure any firewalls and routers on both sides so that person's VNC server can be contacted and connected to.  It's usually port 5900.

The person's desktop I'm viewing is going to be directly connected to the internet (at a university, might be routed...) , but I'm going to be the one going through a wireless router. Do you think this would be difficult to set up?

How can I access another desktop from my computer over the internet with the built in client? Is it only through the terminal?

---

### Post by Onay on 2007-10-30
It seems that VNC cannot find the host (113). Is there something else I need to do... this seems to easy. How can I change which ports are open and which are closed?

---

