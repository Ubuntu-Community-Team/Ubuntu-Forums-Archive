---
title: "[SOLVED] The Debian Menu is not showing up!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-15
Hello,

Following someone's advice in one of the wikis, I downloaded the app to allow the Debian menu to show up in the menu bar.

Unfortunately, it doesn't show up! I restarted X, and even rebooted the computer to no avail. When I select properties, the Debian is there but in italic and the suystem won't allow me to select it.

What could I do next?

---

### Post by jhenager on 2007-04-15
It wasn't straightforward for me, either. Look at this post and see if it helps.
[http://ubuntuforums.org/showpost.php?p=2450064&postcount=5](http://ubuntuforums.org/showpost.php?p=2450064&postcount=5)

I just installed it last week, but I already forgot how I did it.

---

### Post by the8thstar on 2007-04-15
> sudo aptitude install menu menu-xdg
sudo update-menus


Hmm... the computer I'm using doesn't have Ubuntu on it. I have to wait until tonight to try that solution. At first glance, it seems to me that the 'Menu update' hasn't happened yet on my system. I'll let you know how this is going.

Thank you for your good help **jhenager**. :)

---

### Post by the8thstar on 2007-04-16
It didn't work. 

The console returned me this message:

> root@the8thstar-laptop:/home/the8thstar# sudo aptitude install menu menu-xdg
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@the8thstar-laptop:/home/the8thstar# sudo update-menus 
sudo: update-menus: command not found

What is going on?

---

### Post by Skidpad on 2007-04-16
^^  That error comes up when you try to install something from the terminal while at the same time have Synaptic open. I just tried it with Synaptic open, and got the same message.  

I closed Synaptic,and it works fine.  Try it, let us know how it goes.  :)

---

### Post by the8thstar on 2007-04-16
**Skidpad**, you are a wise person. :D It worked!

---

