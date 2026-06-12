---
title: "Understanding system services"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by Valhalla on 2005-12-12
I'm new to ubuntu, though, not linux in general.  Before, I switched I have used Gentoo and SUSE.

I'm trying to understand the ubuntu system services menu.  It seems to be missing a number of scripts that are in /etc/init.d/.  Is this by design, and if so, how would I add or remove things from the runlevels.  The case in point being, I noticed that bluetooth daemons are started by default.  I would like to remove bluetooth, since I do not have any of the necessary hardware on my system and it seem silly to have it up and running in that case.  Can I remove it simply by deleting the link in /etc/rc2.d/ without causing damage, or is there a way of doing it with update-rc.d (when I try remove, it whines at me saying there is still a runlevel script).  

Thanks

---

### Post by Lambert on 2005-12-12
There's an app called bum that's in the repositories that is a little more inclusive of what services you can start and stop. This will manage anything in runlevel /etc/rc2.d

I've actually found the services option in the menu didn't work for me. Tried to stop nptdate through that and it still started.

There is another section (/etc/rcS.d) that bum will not let you manage but there are ways to control this. Becareful of what you do here though. 

From the command line you can use the update-rc.d command. Look at it's man page.

Here is a link to another thread doing something similar.

[http://ubuntuforums.org/showthread.php?t=89491&highlight=howto+startup](http://ubuntuforums.org/showthread.php?t=89491&highlight=howto+startup)

---

