---
title: "Add Service to Startup"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-07-10
How can I add a daemon to start on bootup?  Does it matter which folder the daemon is in?

Thanks for your help.

---

### Post by raldz on 2006-07-10
You could add apps to run at startup in "Sessions".. I'm using Kubuntu right now, so I can't remember it.. If it's not in SYSTEM>ADMINISTRATION it's located at SYSTEM>PREFERNCES... or for daemon you could create a script to startup at /etc/init.d/

---

### Post by frodon on 2006-07-10
Which daemon ?

When you install a daemon the default behaviour is to start on bootup.
In gnome there's a tool to manage services, it's in System > Administration > Services.

---

### Post by StoneMan353 on 2006-07-10
If you're attempting to run a command automatically at startup, I found it useful to add the command to /etc/rc.local.

This is how I set up the wpa_supplicant daemon to start at bootup.

I find it more useful than adding a program to gnome's session manager, because it will still work regardless of whether you're logging into gnome or not.

---

### Post by frodon on 2006-07-10
StoneMan353, the nice way to do that is to put your script in /etc/ini.d then run this command : ```
sudo update-rc.d name_of_the_script defaults
```where default is the priority level. This command make the rc.local symlinks for you depending on the priority level you chose.

---

### Post by Apple 101 on 2006-07-10
I'm trying to install the gnome-clipboard-daemon.  So, should I add it to */etc/init.d* or */etc/rc.local*?

---

### Post by frodon on 2006-07-10
Look first if it appears in the System > Administration > Services window, but as i said before the default behaviour should be "run on startup".
The other way that I and StoneMan353 talked is to run a script on startup, obviously this script can just contain the command to start the daemon (both ways works).

---

### Post by Apple 101 on 2006-07-10
Thankyou for your help everyone - it works!

I copied the file to */etc/init.d* and then ran *sudo update-rc.d gnome-clipboard-demon defaults*.  After a system restart everything worked.

---

