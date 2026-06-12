---
title: "Couple of issues I'm having"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-03-21
Originally, this was a Kubuntu Breezy install, but then I decided I liked GNOME better. When I shut down now, the terminal says "Shutting down KDM,... pid not found!" or something like that. I simply switched /etc/X11/default-display-manager to use gdm rather than kdm. Any way to correct that?

After messing with XGL for a bit (and later uninstalling it), I now have the following problems as well:

My /var/log/messages is spammed with the following lines:
> Mar 21 14:19:52 spark kernel: [4382474.336000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Mar 21 14:19:52 spark kernel: [4382474.336000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Also, if I use the xmodkeymap commands in the guides, it breaks my language-switching support, and I can only select windows by clicking on the borders or titles.

Also, when I go to System -> Lock Screen,... nothing happens... which is bad considering I like to lock my PC every time I leave it. :(

Should I just apt-get remove gnome and apt-get install gnome?

---

### Post by trent dillman on 2006-03-21
The KDM problem can be solved by removing it completely through synaptic, and if that doesn't work, try 

```
sudo rm -i /etc/rc?.d/???kdm
```

For locking the screen, you might try enabling that in the screensaver properties. Since you're in gnome, try system > preferences > screensaver.

---

### Post by Kurt` on 2006-03-21
Ahh thanks, I had forgotten that +x scripts are executed in that folder during startup/shutdown

[http://xs73.xs.to/pics/06122/screensaver.png](http://xs73.xs.to/pics/06122/screensaver.png)

That's my GNOME screensaver settings. With those as my settings, I still cannot Lock Screen, and the screensaver won't come on. I'm pretty sure I broke something important when installing XGL. :(

---

### Post by trent dillman on 2006-03-21
You may have. I haven't tried XGL yet, so....


...if I'm not mistaken, XGL will be in Dapper, so maybe an early dist upgrade would help?

And the *ubuntu gurus can lambaste me if I'm wrong on that one.

---

