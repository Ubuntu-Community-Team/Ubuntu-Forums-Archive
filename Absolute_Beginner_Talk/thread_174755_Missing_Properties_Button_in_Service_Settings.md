---
title: "Missing Properties Button in Service Settings??"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by weiyang on 2006-05-12
Hello, any information will be appreciated. When I click System---> Adminstration----> Services ------> Service setting panel is open after the password is verify. 

All my running programmes are listed but I cannot find the Properties Button to configure them. I can only tick or un tick them. Only the Help, Cancel and OK buttos are available. Anyone knows whats going on????

---

### Post by mlind on 2006-05-12
[QUOTE=weiyang]Hello, any information will be appreciated. When I click System---> Adminstration----> Services ------> Service setting panel is open after the password is verify. 

All my running programmes are listed but I cannot find the Properties Button to configure them. I can only tick or un tick them. Only the Help, Cancel and OK buttos are available. Anyone knows whats going on????[/QUOTE]

Services view is only for enabling/disabling _certain_ services.
You can install BUM to gain some more control for services, but for modifying
service configuration files, you must edit them manually from /etc/ directory.

Could you explain why do you want to modify certains service's configuration settins?

---

### Post by mgmiller on 2006-06-05
I also noticed that the window displayed looks nothing like the one in the help pages.  I found a nice utility that is pretty intuitive to use.  I used this to turn off the pcmcia services on my desktop machine that always showed a fail on bootup.

first you need to install a package to let you edit the running services:
sudo apt-get install sysv-rc-conf

next you run the program:
sudo sysv-rc-conf

you put an x next to the service and runlevel you want it to be active in.
Or remove x from service you don't want to run.

When done q to quit.

That's it.  Changes should be there on next reboot.

---

