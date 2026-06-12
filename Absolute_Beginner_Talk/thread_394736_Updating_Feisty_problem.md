---
title: "Updating Feisty problem"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-27
Hey guys!

I ve downloadet faisty beta and installed it 2 days ago. Everithing went smoothly.

Then i messed some setings so i reinstalled today. 

Now i have some problems wich i dont know how to solve. And that is when i reboot after installation it doesnt want to update. When i click updater it starts opening than it says i have anothe adept or something open and it wont update.

I dont have any other packet manager open so pls help me install this updates and set things straight.

Thanks!

---

### Post by floke on 2007-03-27
go to system/admin/system monitor and see if you have any processes running from a previous session that look like package managers. You could try turning off the update notifier to see if that helps (make sure you turn it back on later though).

It also helps if you post what errors you have rather than simply saying you have some errors.

---

### Post by Vandorius on 2007-03-27
Im quite new to Kubuntu so be gentle.

Ok i turned off the update manager so it doesnt start next reboot. I rebooted than started adept manager. When it says he is reading state information it stops and shows message: "Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one." When i clock ok it lists me the updates anyway but i cannot update.

Then i press preview changes and i see: foo2zjs - status: broken and kdm - status: broken

I ve installed it 2 days ago and everithing went smooth. Now i reinstalled 2 times and every time this happens.

---

### Post by zvacet on 2007-03-27
I´m not family with kubuntu but I guess **Adept>edit>fix broken packages** 
If it is not exact command it have to be something like that.just search adept for that kind of command.

---

### Post by Xamindar on 2007-04-09
I am having the same problem with the adept manager in kubuntu.  It thinks there is another package manager already running.  Rebooting doesn't fix the problem.  I am thinking it uses a rather bad design idea of looking at lock files to see if there is one running already instead of simply checking the process list to see if there is in fact another one running or not.  

Anyone know how to fix this?

---

