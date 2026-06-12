---
title: "Beginner with Ubuntu...need help"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by kevipapo1 on 2007-06-08
Hi, I'm new to this whole Ubuntu thing.  I've had a bit of previous experience with ipodlinux.  But onto the problems:

I have a PowerBook 12-inch and just installed Feisty Faun (7.04).  It wiped out my HDD.  But that's not to worry about right now.  I edited the /etc/X11/xorg.conf file so that the trackpad wasn't so sensitive as to clicking with it.  After I changed the wrong section by accident (all I did was add Option "MaxTapTime" "0") I saved it.  It didn't work.  I changed a bunch of other places, I even changed the driver name and all that.  Then I learned that I had to reset the X11 system by pressing ctrl + option + delete.  So I did.  Then the screen went to normal Terminal mode.  There was no more desktop.  I rebooted.  Such a small change comes such a big problem.  I got the Live CD out and opened the file again on the live CD, then the one on the HDD.  The one on the HDD is Read-Only.  So I am currently in the process of opening it in Terminal with gksudo gedit /etc/X11/xorg.conf.  However, that opens the one on the CD, which is the right one.  Now I know that I have to use gksudo gedit /media/disk/etc/X11/xorg.conf.  My computer isn't with me right now, though, so maybe later.  Now here are the other problems.

How do I get an Apple Airport to work with Ubuntu.  It's hidden, the name of it is entropy4, and the password is atabonnesante (WEP).
And of course I'm going to have trouble with Beryl eventually, so I'll be writing about that stuff eventually.
So just correct me if I'm wrong about any of the things I've been talking about.  Thanks for any or all help you can provide:D

---

### Post by kevipapo1 on 2007-06-08
bump?

---

### Post by NeoLithium on 2007-06-08
Did you make a backup copy of the xorg.conf?  If you boot without the liveCD you should be able to reconfigure the xserver with
```

sudo dpkg-configure xserver-xorg

```

It's a good idea to back up the xorg files before you make changes, just do this in a terminal window beore modifying 
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

---

### Post by kevipapo1 on 2007-06-08
I got the xorg.conf problem fixed, and now tapping is dsaebled.  Now the big thing is getting the Apple Airport to work.  I put in entropy4 for the name, atabonnesante for the password (WEP ascii) and it still won't connect.  All I can use right now is my ethernet cable.  Any fixes for this?  All help much appreciated:D

---

### Post by kevipapo1 on 2007-06-08
bump (again)

man, the posts in that section sure do go down fast:-k

And BTW I used the beryl installer located at [http://forum.beryl-project.org/viewtopic.php?f=36&t=4781](http://forum.beryl-project.org/viewtopic.php?f=36&t=4781) and it went through the install ok, until I rebooted and it was still using GNOME.  None of the Beryl effects had taken place.  Any help there?

---

