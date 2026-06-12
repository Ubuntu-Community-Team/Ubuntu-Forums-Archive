---
title: "Hibernate killed my panel"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by jackpetrilli on 2007-12-07
After running hibernate, I was forced to reboot to try and regain access to my computer.

Now Gnome loads but without either panel (top or bottom).  I get an error msg saying something to the effect that I don't have the rights to make changes to the panel (which I'm not trying to do btw.)

It now does this after every reboot.  Is there a command in xorg.conf I should be eliminating?  Should I just go back to the backup xorg.conf.backup?

Anyone know how I can "re-acquire" these necessary parts to the gnome desktop?

- Jack

---

### Post by ThrashJazzAssassin on 2007-12-07
I wouldn't have thought it has anything to do with xorg.conf. 

First thing I would do is delete or rename the folder ~/.gconf/apps/panel, log-out then back in and hope the folder is recreated and the panel goes back to it's default state.

I dont know though.

---

### Post by adityakavoor on 2007-12-07
Hit Alt+F2 and type in gnome-terminal
now type in the following to the terminal

```


gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &


```

---

### Post by khurrum1990 on 2007-12-07
If u want help with hibernate then please post in detail about ur system configuration.

Here r some tips though for hibernate if u r using an Nvidia card.

Make sure u have entered: Option     NvAGP         "1"     
Enter this in /etc/X11/xorg.conf under the device section.

There is a bug in Ubuntu/Kubuntu 32-bit kernel 2.6.22-14 that stops suspend/hibernate on some Macbooks and regular pc's as well. You will have to install kernel 2.6.22-12. More information on this can be found at:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151016](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151016)

After this whenever u suspend to ram or suspend to disk make sure Compiz Fusion is turned off. Try these things if u have an Nvidia card though.

Good Luck!

---

