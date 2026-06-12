---
title: "Installed and removed Gnome-Dock, now I cannot even boot"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by AndrewZorn on 2008-04-08
I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=302570](http://ubuntuforums.org/showthread.php?t=302570)

and hated it.  It's slow.
I could not remove it with Synaptic, so I just deleted the directory I created in /opt and then did apt-get remove on all the packages I installed.  It warned about uninstalling Evolution and stuff, so I went back through and removed them one by one, only uninstalling the ones that would uninstall by themselves.
Then I did an autoremove.

Firefox wouldn't start anymore, nor would System Monitor.  I restart.  After GRUB, I just get black.  Hard drive spins a bit, but then no more.

Recovery mode lets me do startx, but nothing works... no panel, no menu bars in Nautilus (which is the only thing I can get into without a panel.

In text-based recovery mode, I was just going to install the packages I removed (even if they aren't necessary).  I cannot because I am not online.  I cannot figure out how to GET online, even with a wired connection.

I am totally stuck and this is really pissing me off, so I'd really appreciate some help as far as **really basic networking in Recovery Mode.**  I think some of the libr... crap I removed has something to do with X and that's why I'm not getting a login screen or the panels in Recovery Mode.

---

### Post by AndrewZorn on 2008-04-08
Well, I finally figured out how to install the packages **I explicitly removed**, but it didn't fix anything.  So that means it's a lot more screwed up than I thought.

Is there some way to go through and look for packages I'm missing and get them?  Unless it's a coincidence, I just KNOW it has to be that I removed something that I shouldn't have.

EDIT also did this
[http://ubuntuforums.org/showthread.php?t=714744&highlight=gnome+deamon+settings](http://ubuntuforums.org/showthread.php?t=714744&highlight=gnome+deamon+settings)
and it did not fix the exit status 127 I get when I do startx in recovery mode:
"There was an error starting the GNOME Settings Daemon. ... Process /usr/lib/gnome-control-center/gnome-settings-daemon exited with status 127"

EDIT and during starting Recovery Mode I get a FAIL for
Mounting local filesystems... mount: special device /dev/disk/by-uuid/07D8-0113 does not exist
is this bad?

---

### Post by louieb on 2008-04-08
try ```
sudo dhclient
``` and see if that doesn't get an IP
may have to run this 1st.
```
sudo /etc/init.d/networking start
```Good luck.

See you got networking going
try ```
sudo aptitude reinstall ubuntu-desktop
```

---

