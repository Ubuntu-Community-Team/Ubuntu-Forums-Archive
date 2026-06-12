---
title: "install realvnc"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by sdmtnbiker on 2006-12-07
It's me again! :) I'm getting stuff done thanks to the help I get here. This is my latest challenge, I have realvnc server installed on my XP machine and I have port forwarding all set up. I have downloaded the Linux realvnc to my desktop, I extracted it to my desktop. Now what do I do??  I really just want to install the viewer, so what is my next step?
Thanks in advance.
Steve

---

### Post by Spitfire567 on 2006-12-08
You do not need the package from the RealVNC web site, unless you want to compile it yourself.  Ubuntu has both vncviewer and vncserver in the repositories.  

Use synaptic or apt-get to install vncviewer.  Either search synaptic for the vncviewer package, or type the following on the command line:

sudo apt-get install vncviewer


Enjoy!

---

### Post by houstonbofh on 2006-12-08
Actually it is installed already.  If you want to VNC to Ubuntu, you just need to enable it.  If you want to VNC from Ubuntu, just run it from the menus.

---

### Post by sdmtnbiker on 2006-12-08
> **houstonbofh said:**
> Actually it is installed already.  If you want to VNC to Ubuntu, you just need to enable it.  If you want to VNC from Ubuntu, just run it from the menus.

it is not listed in the menus.

---

### Post by houstonbofh on 2006-12-08
> **sdmtnbiker said:**
> it is not listed in the menus.
Go to the top left. (Unless you moved it)  Click on Applications --> Internet --> Terminal Services Client.  Under Computer put the name or IP of the client.  Under protocol, check VNC.
For the Server go to System --> Preferences --> Remote Desktop. Fill out as appropriate.

---

### Post by noneck on 2008-04-23
> **houstonbofh said:**
> Go to the top left. (Unless you moved it)  Click on Applications --> Internet --> Terminal Services Client.  Under Computer put the name or IP of the client.  Under protocol, check VNC.
For the Server go to System --> Preferences --> Remote Desktop. Fill out as appropriate.

Yah, and after you go here, by default the VNC choice is greyed out, so you will need to close it,

```
sudo apt-get install vncviewer
```

Then re-open, Internet --> Terminal Services Client, and you will now be able to select "VNC"

Hope this helps

---

### Post by houstonbofh on 2008-04-24
It annoys the heck out of me that they took VNC out of Hardy.  No real reason I could see, either.

---

