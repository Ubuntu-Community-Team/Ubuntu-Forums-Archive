---
title: "Kernel Install"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by fuzion9 on 2006-03-27
I seem to have made a mistake when installing Ubuntu on a new server...  The server is a plesk based web server.  The server is a dual xeon 3.0 ghz machine -  and i have noticed only recently ](*,) that i failed to install an smp kernel.  The server is now colocated and I need to get both processors working.

Basically this mistake has been eating away at me for about a week now, and I am hoping to get some advice on the proper way to move forward and install an smp kernel.

What i need to know is what kernel should i actually install, and what can go wrong - worst case scenario's - and recovery should something bad happen.  The system is host to too many clients to suffer any downtime....

I no longer have direct access to the box, and if something goes wrong I will have to schedule a visit to the colocation facility to repair.  I would like to be prepared for all possible situations which may arise.

The system is Ubuntu 5.04 and current version is: 
Linux version 2.6.10-6-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2))

Any advice would be greatly appreciated.

---

### Post by az on 2006-03-27
sudo apt-get install linux-686-smp

That should do it.  It should install the kernel, but you would have to reboot into it.

If it fails to boot the new kernel, you would need someone to boot it into the old kernel (which will not be removed)

---

### Post by fuzion9 on 2006-03-28
Thank you for your reply - Is that really the worst case scenario?  Just choose the old kernel at boot?

I know everything should be smooth, but i'm paranoid.

---

### Post by mdmarmer on 2006-03-28
On a server there should be no problems

Sometimes on desktop system if you install new versions of the video drivers or wireless, etc. to match the new kernel and for some reason things don't work, it can be difficult to downgrade -- maybe the moral of this is to upgrade only the kernel first and make sure that it works OK before upgrading associated modules and drivers

I would say at least 95% of time either new kernel works perfectly or old kernel still works 

Mike

---

### Post by az on 2006-03-28
[QUOTE=fuzion9]Thank you for your reply - Is that really the worst case scenario?  Just choose the old kernel at boot?

I know everything should be smooth, but i'm paranoid.[/QUOTE]
Right.  That is the worst case scenario.

---

