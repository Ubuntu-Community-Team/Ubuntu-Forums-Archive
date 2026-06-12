---
title: "Linux Black Screen of Death"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by jgitz on 2006-07-01
I have had Ubuntu 6.06 on a laptop for a couple of weeks. The laptop has only Ubuntu on it and was a clean install (no upgrade). It has worked very well until now. 

Today, while trying to boot up, the laptop stalls, goes to a black screen, and says:

acpid: can't open socket /var/run/acpid.socket: Read-only file system
Starting system log...

after which the computer is dead in the water. I pull the power cord out, yank the battery to shut it off, and try again. These repeated attempts yield the same behavior.

Any ideas on what is happening? Is this a common problem with Linux or just with Ubuntu? I am still at a position where I can revert back to Windows XP or perhaps another version of Linux. 

Thanks!

John

---

### Post by David_T on 2006-07-01
Can you post some info about your laptop?

---

### Post by jgitz on 2006-07-02
It is a standard Toshiba Satellite 1805-s207 with 512 MB memory, 30 G hard drive. Ubuntu 6.06 was installed "clean", wiping out everything else that was on the system. All the updates (lots of them) were applied. It was working well for a while and then poof! Linux Bl-SOD! 

This morning, I did yet another clean install of 6.06 and it now boots and runs again. However, I'm wary of doing anything serious with the laptop for fear of losing everything if it dies yet again.

Thanks.

John

---

### Post by catlett on 2006-07-02
Why don't you disable acpid and see if that helps. It is easily done through "boot-up manager". It will be under System<Administration<Boot-Up Mnager. If it isn't there you will have to install it ```
sudo apt-get install bum
```
Acpid performs power management on your system so if it isn't the cause you may want to re-enable it because you have a laptop..

Just a thought, sorry I don't have a solid answer to give you.
Good luck.

---

### Post by jgitz on 2006-07-04
Thanks for the ideas.

Unfortunately, this made the situation worse. The Black Screen of Death now sporatically appears with no writing on it at all. Other times, the CPU seems to go nuts with no apps open, running out of control and letting nothing interfere.

I don't recall these problems showing up a while back when I did a quick test of the older 5xx version. Maybe I didn't use it long enough. But these problems with 6.06 are a real deal breaker. A lot of work is required, its like running an alpha version. 

I'll recommend to the group to pay the cost of Windows XP (FWIW, runs fine on this laptop) for now and try Linux in another year or so when it has has more time to mature.

Cheers!

---

