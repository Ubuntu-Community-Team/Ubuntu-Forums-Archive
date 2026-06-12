---
title: "xubuntu + network manager + wifi problem"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by midorigreen on 2007-05-28
Hi everyone, long time troller, but first time poster!

I've been having problems up to my neck trying to get my xubuntu box to connect with a wireless network.  Here's what I've done so far:

1)  Used ndiswrapper and properly installed the driver for my wifi card.
2)  The card is detecting wifi networks in range (I had to use wifi-radar)
3)  Realized that having wifi-radar installed would affect network manager install, so I uninstalled wifi radar.
4)  Installed network-manager AND network-manager-gnome
5)  Saw that no icons or additional items appeared in my applications menus, so I ran 

```
#nm-applet
```

and I get this error

```
# /bin/sh: /usr/bin/esd: not found
```

Any ideas as to what is happening here? 

TIA! :)

---

### Post by midorigreen on 2007-05-28
update:  still double checking my wireless device driver, but it seems like ndiswrapper is doing it's job

---

### Post by Kobalt on 2007-05-28
Try to launch it with *nm-applet --sm-disable*

---

### Post by ugm6hr on 2007-05-28
Bizarre.

This was the solution:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

But it sounds like you're already doing the right things.  About the error you get with:
nm-applet

Sounds like a problem with network-manager-gnome (or network-manager)
Try uninstalling it, and then re-installing again.  Then try "nm-applet" again.

---

### Post by midorigreen on 2007-05-28
> **Kobalt said:**
> Try to launch it with *nm-applet --sm-disable*
I seem to get the same error message:(

---

### Post by ugm6hr on 2007-05-28
```
# /bin/sh: /usr/bin/esd: not found
```

Just checking - you have Xubuntu7.04 right?

I have the same setup - albeit without ndiswrapper (Xubuntu7.04/NetworkManager), and there is no such file on my laptop (/usr/bin/esd).  I have used ndiswrapper with Xubuntu/NetworkManager on another laptop - but I don't have that one with me, so can't check it.  But I can't see how it would change anything...

Can't work out what that error might mean...

---

### Post by midorigreen on 2007-05-28
> **ugm6hr said:**
> ```
# /bin/sh: /usr/bin/esd: not found
```

Just checking - you have Xubuntu7.04 right?

I have the same setup - albeit without ndiswrapper (Xubuntu7.04/NetworkManager), and there is no such file on my laptop (/usr/bin/esd).  I have used ndiswrapper with Xubuntu/NetworkManager on another laptop - but I don't have that one with me, so can't check it.  But I can't see how it would change anything...

Can't work out what that error might mean...

Yup!  7.04!

I've been researching all morning, and this doesn't seem to be a widespread problem (usually people have a problem with multiple network manager icons, but I can't even get one to show up!)

I've tried uninstalling network-manager-gnome several times followed by restarting, and still no dice...hmmm...

---

### Post by ugm6hr on 2007-05-28
Perhaps something else you've installed?

I've just googled it:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/106588](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/106588)

Looking through my installed packages relating to esound - 
"esound-common" 
And to pulseaudio:
"libpulse0"
are installed on my system according to Synaptic.  Maybe you need to make sure they're installed?  Can't think what that would have to do with NetworkManager though, just trying to think in a different direction.

Can't think of much else.

---

### Post by midorigreen on 2007-05-28
> **ugm6hr said:**
> Perhaps something else you've installed?

I've just googled it:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/106588](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/106588)

Looking through my installed packages relating to esound - 
"esound-common" 
And to pulseaudio:
"libpulse0"
are installed on my system according to Synaptic.  Maybe you need to make sure they're installed?  Can't think what that would have to do with NetworkManager though, just trying to think in a different direction.

Can't think of much else.

Good call!  So I installed the esound package, and the error message is now gone - however when I try and run nm-applet, my terminal freezes..

frustrating!

Thanks so far for all the help!

---

### Post by midorigreen on 2007-05-29
I've tried it all at this point...although I've gotten rid of the error msg, terminal freezes when I run nm-applet --sm-disable

---

### Post by ugm6hr on 2007-05-29
Only thing I can think of is either hardware or software conflict.  Easy way to check - if you have 256MB RAM or more - try booting the Ubuntu (not Xubuntu) LiveCD and see if Network Manager works.  If so, there's obviously an issue with your installation.  Or, bite the bullet and just reinstall Xubuntu and add Network Manager before doing anything else.

Sorry, but I haven't got any other ideas.

---

### Post by midorigreen on 2007-05-29
Don't apologize!  You've helped me out quite a bit!

Thanks everyone

---

### Post by gnychis on 2007-06-14
i've got the same problem :\

---

### Post by midorigreen on 2007-06-14
well, as an update, what I ended up doing was a fresh install of xubuntu

First thing I did was compile the driver using ndiswrapper, then followed that with an install of network-manager ...and now it finally works like a charm.

---

