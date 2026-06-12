---
title: "Can't start administrative applications"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Ottery on 2006-09-06
I had to reconfigure my wireless.  Being the bungler I am, I somehow managed to lose access to administrative functions (Networking, network tools, etc.) after trying to reconnect to my router (it's tricky for me--I'm a biologist, not too savvy with the hardware).  

Anyway, I can't even get the administration login window to load; it starts, the tab appears in the status bar, then quits and the tab vanishes.

I honestly have no idea.  Read the tutorials for connecting to the internet but couldn't find anything that resembles my problem.

Any ideas?

Thanks!!

---

### Post by arkangel on 2006-09-06
what happens when typing 
sudo -H -s
if you get 
sudo: unable to lookup via gethostbyname() 


you have to edit the /etc/hosts and /etc/hostnames

[http://www.ubuntuforums.org/showthread.php?t=222012&page=3](http://www.ubuntuforums.org/showthread.php?t=222012&page=3)
for more details

---

