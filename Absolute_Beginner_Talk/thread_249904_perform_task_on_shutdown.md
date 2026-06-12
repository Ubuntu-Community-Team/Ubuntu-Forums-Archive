---
title: "perform task on shutdown"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by rarstar on 2006-09-03
hi all,

is it possible to have ubuntu close azureus automatically when i shutdown my pc?

cheers,
rar

---

### Post by gary4gar on 2006-09-03
> **rarstar said:**
> hi all,

is it possible to have ubuntu close azureus automatically when i shutdown my pc?

cheers,
rar
when u shutdown ur pc ubuntu will close all the running app automactically. so i could not get what are u asking??
pls be clear

---

### Post by rarstar on 2006-09-03
well, if i don't manually exit azureus before i shut down, the next time i switch my pc on, i get a message saying azureus didn't shut down tidily.

cheers,
rar

---

### Post by PacShady on 2006-12-03
I also need something to perform a function just prior to shutting down.

I need to unmount a specific drive before KDE and Xorg close upon restart or shutting down. Because of an error that NO ONE ON THIS FORUM seems to know about (my post keeps getting ignored), a fix I've worked out is to unmount a particular drive of mine just before shutting down or restarting. Otherwise, 90% of the time Kubuntu crashes during shutdown, and my Firefox profile gets corrupted.

So does anyone know how to make this happen? I'd really prefer to just set it up as an automatic thing when shutting down or restarting from KDE, I don't want to have to make a script that I have to click on every time KDE and Xorg shut down.

'Shady

---

### Post by lamego on 2006-12-03
Create the script that you need to run on shutdown at /etc/init.d , example:
/etc/init.d/shutdown
Make sure it can be executed by root:
```
sudo chmod 755 /etc/init.d/shutdown
```
Now you need to choose at which runlevel do you want the process to be run (man telinit for more info about runlevels).
I will setup the process to be called on the start of the shutdown process (runlevel6).
```
sudo ln -s /etc/init.d/shutdown /etc/rc6.d/K999myshutdown
```

---

### Post by PacShady on 2006-12-03
So does this mean it will be run before the Xserver is shut down, or after?

I'll give it a try and see if it works. Thanks

'Shady

---

### Post by lamego on 2006-12-03
The xserver is the fist to be killed during the shutdown:
/etc/rc6.d/K01gdm
It order is based on the number that you use on the K filename.

---

### Post by PacShady on 2006-12-03
So then, theoretically, if I were to rename K01kdm and K01xserver and make them K02... then I should be able to squeeze my script in BEFORE KDE and the Xserver shut down, right?

'Shady

---

### Post by lamego on 2006-12-03
Or just create the link as K00, it should work also...

---

### Post by PacShady on 2006-12-17
OK, just wanted to come back and say how it went.

Well, my little script failed to do what I needed, however I think I know why. The problem, I now realise, is that I need to run my little script BEFORE the runlevel changes, as opposed to after. Is there a way I can set my script to run just prior to the runlevel changing from 5 to 6 or 0? Thanks

'Shady

---

### Post by benpage26 on 2008-03-07
A simple solution may be to create a script that does the required stuff (ie, unmounts your drive) and then tells your computer to shutdown.  You could add a launcher for this to your desktop and click on it when you want to shutdown instead of the normal command.

I don't know how possible that is on KDE though.
ben

---

