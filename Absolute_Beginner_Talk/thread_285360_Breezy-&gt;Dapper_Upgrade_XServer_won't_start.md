---
title: "Breezy-&gt;Dapper Upgrade: XServer won't start"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by justjuice on 2006-10-26
Have just upgraded my Breezy to Dapper, kernel 2.6.15.27.386.
When it boots up, all I get is a command line login ie. X-server and gdm don't start, so I have no access to the GUI.

However, if I log in via recovery mode and then type gdm -start, it starts up (with a Power Manager error), or if I do /etc/init.d/dbus start and then gdm -start, it all starts normally and I can use Ubuntu normally.

So what do I have to do for my system to boot up normally and give me the login page without me having to select recovery mode and type in a bunch of commands?

Oh, the other way I can start it is by doing dpkg-reconfigure xserver-xorg.  This has been done a number of times, and the driver that is currently selected in vesa.

Thanks in advance.

---

### Post by ilushkin on 2006-10-27
my ati on laptop is nothing but regular card. is it suppose to kill xserver and ubuntu? apparently, it did :) screw 6.10

---

### Post by justjuice on 2006-10-27
Well, I fixed it by installing kdm instead.  Although it seems like overkill to me. The install of kdm must've reset the default display manager. Wish I knew how to do that by just editing a file or something.

Now my internet connection doesn't work, so I'll start another thread.  This upgrade to Dapper is proving to be a big mistake.

---

