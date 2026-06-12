---
title: "Command Line Update Notification?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by cjl on 2007-05-23
UB:

I am running Ubuntu Server (Fiesty Fawn) and mostly access it using a Putty terminal from my Windows XP desktop.  

I would like to be notified at the command prompt when I log in if updates are available.  I know I can run 'sudo apt-get update' then 'sudo apt-get upgrade'  but I think it would be cool if when I logged in I could see something like "Updates are available.." .  

Any ideas?

I am using the bash shell.

-CJL

---

### Post by lazyart on 2007-05-23
Wondering to myself if you can even impersonate su within a script without asking the user for the password, which is ugly.

A thought would be a cron job checking for updates every x hours and dumping the output into a text file, then checking that text file upon logon?

As soon as I'm due for an update I'm game to play with it.  Looks like fun.

---

### Post by earobinson on 2007-05-23
you cant impersonate su with a script however you can make a script as root then alow the normal user to run it (this will let the normal user run that sricpt as if they where root with out the password) note only root will be able to change the script

---

