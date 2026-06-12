---
title: "What Do You See As The Absolute Essential Packages To Load onto Ubuntu?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by AgCrew08 on 2007-11-12
Im still new to all of this and I was just wondering what the more experienced guys think is the most essential programs to download and install. 

Security?
Convenience?
Fun?

What do you think?

---

### Post by TadH on 2007-11-12
first of all let me know if i EVER need a security package for linux..i will stop using it. 
second i like frostwire, its like limewire pro but free. vlc media player is a must for me anyway abd alien arena is a sick fps

---

### Post by AgCrew08 on 2007-11-12
Wait, so you guys really have no concern what so ever about security using linux?

---

### Post by TadH on 2007-11-12
no

---

### Post by alwiap on 2007-11-12
> **AgCrew08 said:**
> Wait, so you guys really have no concern what so ever about security using linux?

breeze through [http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372) for an idea of the security with ubuntu

there's a thread somewhere if you searched the forums (i'm too lazy/tired/hungover) for the top 10 packages people install after a fresh install of ubuntu.  obviously you don't have to go hogwild and install everything but it gives you an idea of popular programs and why.

---

### Post by ciscosurfer on 2007-11-12
You can also check here: 
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7) for the Servers and Security section of UbuntuForums for more on security.

---

### Post by mivo on 2007-11-12
Besides what comes with the base installation of Ubuntu, for me the essentials are Wine, Deluge, GVim, PuTTY, Grsync, OpenSSH Server, Java and Firestarter because Ubuntu comes without any iptables rules enabled (so no active firewall). I also use Swiftweasel instead of Firefox.

---

### Post by -grubby on 2007-11-12
wine,kolourpaint, and kaffeine

---

### Post by avik on 2007-11-12
Security is very important, but there's no product that can magically provide security.  It's a mindset.  Ubuntu, unlike Windows, comes locked down and highly secure, so there's no need to worry about other packages to deal with security.

However, you still need to be aware of threats, and use sudo priviledges widely.

As far as the original question goes, one important package is ubuntu-restricted-extras (also available in kubuntu and xubuntu versions).  With that, you'll get all the codecs you need, even the flash player.

If you're using Compiz, and you like to customize your environment, get ccsm (compizconfig-settings-manager).

I also like inkscape and kolourpaint for various drawing purposes in addition to the preinstalled GIMP.

As far as games go, supertux is great.  Just be sure to get the supertux-stable package, as the supertux package is the buggy development version.

There are plenty more, but those are a few that come to mind.

---

### Post by stalker145 on 2007-11-12
Conky, Cowsay, various Fortunes modules... just to add some not mentioned ;)

Of course, it's always good to have a bit of antivirus in there just to be kind to the unconverted... in the event that you "accidentally" pass on a virus.

---

### Post by mivo on 2007-11-12
> **avik said:**
> Ubuntu, unlike Windows, comes locked down and highly secure, so there's no need to worry about other packages to deal with security.

If you call the lack of an active firewall "highly secure", then sure, Ubuntu is that. ;) Ubuntu has iptables enabled, but there are no rules for it, so the machine is unprotected unless it is behind another firewall (built into the router for example). There are no services like SSH running, but it will respond to pings. The moment the user installs a web server, SSH server, etc. the machine is wide open for attacks, and it is not invisible to outsiders out of the box. You can verify this [here]("http://www.hackerwatch.org/probe/") (select "port scan").

Everyone really should install the **firestarter** package and run the wizard. This will set up sufficient rules to protect the machine. Some customization is probably desired, but this is better than nothing -- and it takes only a minute. Firestarter is not a firewall, it is only a frontend to configure iptables (the firewall), so it does not need to be running.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
an example of passing on a virus 
move in with my  roommate and i had many videos i dl off the net and they didnt do any thing to my ubuntu copmuter but man they shur screwd up his windows after he copyed em
i had them on there for a year never botherd me.
its like being amun to aids and giveing it to someone :)

---

### Post by newman on 2007-11-12
Wine, K3b, Kaffeine, GQview

---

### Post by rsambuca on 2007-11-12
> **mivo said:**
> If you call the lack of an active firewall "highly secure", then sure, Ubuntu is that. ;) Ubuntu has iptables enabled, but there are no rules for it, so the machine is unprotected unless it is behind another firewall (built into the router for example). There are no services like SSH running, but it will respond to pings. The moment the user installs a web server, SSH server, etc. the machine is wide open for attacks, and it is not invisible to outsiders out of the box. You can verify this [here]("http://www.hackerwatch.org/probe/") (select "port scan").

Everyone really should install the **firestarter** package and run the wizard. This will set up sufficient rules to protect the machine. Some customization is probably desired, but this is better than nothing -- and it takes only a minute. Firestarter is not a firewall, it is only a frontend to configure iptables (the firewall), so it does not need to be running.

Regular desktop users don't really need Firestarter.  I agree, though, if you are running an Ubuntu Server it is a good idea to configure your iptables.

---

### Post by LaRoza on 2007-11-12
* build-essential
* Fluxbox (don't like GNOME or KDE)
* Abiword
* Opera

---

### Post by rsambuca on 2007-11-12
This [TOP 10 thread]("http://ubuntuforums.org/showthread.php?t=35208") is pretty good for getting ideas.

---

### Post by avik on 2007-11-12
> **mivo said:**
> If you call the lack of an active firewall "highly secure", then sure, Ubuntu is that. ;) Ubuntu has iptables enabled, but there are no rules for it, so the machine is unprotected unless it is behind another firewall (built into the router for example). There are no services like SSH running, but it will respond to pings. The moment the user installs a web server, SSH server, etc. the machine is wide open for attacks, and it is not invisible to outsiders out of the box. You can verify this [here]("http://www.hackerwatch.org/probe/") (select "port scan").

If you're running a server, you should know a bit about security.  Otherwise, you shouldn't be running a server.  When I ran a web server, I used firestarter.  Most people don't have to be worried about this, though I agree configuring your firewall is a good idea.

Once again, it's a mindset, not a product.  No matter how secure a tool is, it's only as safe as the user is willing to let it be.

---

