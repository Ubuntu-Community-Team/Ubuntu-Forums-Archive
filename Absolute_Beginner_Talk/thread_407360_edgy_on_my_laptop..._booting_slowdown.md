---
title: "edgy on my laptop... booting slowdown"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by KsR on 2007-04-12
hello everyone,
just installed edgy on my toshiba satellite.  The good thing was that everything worked fine, apart from a booting problem.
I am not always online though my laptop.  Usually when i am not ubuntu takes a very long time to boot, infact I had to restart several times.  I found out where the problem occurs by booting in tet mode,(by removing the instances of 'quiet' in the /boot/grub/menu.lst).  The delay is caused when the os is 'checking for network interfaces'.
  There must be a way to disable ubuntu from checking network interfaces on startup.  Any idea on how to do it.  Also i would like to start the network(for example if i plug in the network cable  in between a session) whenever I want.
What are the various files i need to edit and commands to start the network(maybe some sort of script which i can run on the fly)
thanks..

---

### Post by octoberdan on 2007-04-12
You may want to take a look at [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
Happy geeking.

---

### Post by jimw on 2007-04-12
> **octoberdan said:**
> You may want to take a look at [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
Happy geeking.

Just looked at this.  Unfortunately, it's aimed at those with a lot more knowledge of the workings of linux than I.  I'm using Edgy on a desktop, and particularly recently the bootup time has become horrible.

The injunction to not just do things, but know what you're doing pretty well lets me out altogether.:)

JimW

---

### Post by houstonbofh on 2007-04-13
This is a major bug on Launchpad right now.  Mostly Feisty, which got it even worse.  [https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/102675)

Patches are coming down.  Probably when you upgrade to feisty, it will go away.  The backport may take longer.

---

### Post by octoberdan on 2007-04-14
The fix has been released. Are you still having trouble? Do you need assistance updating your laptop or have any other questions?

---

### Post by KsR on 2007-04-23
hi again
sorry for the late reply
actually what I eventually did was comment all the lines in the /etc/network/interface file, it was a quick way out since i had an emergency presentation that needed to be completed.  now that all that is over I started reading the link you given for a more in depth explanation.
Will ugrade my system and see if it works
thnks...
incidentally I have also heard that there is some problem in the wireless connectivity for my laptop with ubuntu.(something to do with WPA... not really sure).  Will test that out as well
thanks

---

