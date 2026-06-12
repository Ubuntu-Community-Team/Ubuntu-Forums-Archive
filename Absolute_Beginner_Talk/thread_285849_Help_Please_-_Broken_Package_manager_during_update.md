---
title: "Help Please - Broken Package manager during update"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by xhilyn on 2006-10-27
Hi all. I'm rather new to all of this so I find myself in need of some help.
I was running the update from 6.06 to 6.10 and all went ok untill after it had downloaded everything.

My computer just froze completely at the point of
'Preparing tzdata'
I had no option but to reboot, which the computer did, much to my surprise.

However I now have a problem with the Package manager which gives me an error which says:

A error occured, please run Package Manager from the right click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error: BrokenCount>0'.

When I bring up the Package Manager by right Clicking, it gives me this error message.

E: dpkg was interrupted, you must manually run
'dpkg --configure -a' to correct the problem.

Unfortunatly I dont know how to 'run' the above.

I tried typing it into the terminal but it says I need 'superuser' status even after I type in 'sudo -l'.

So I have reached the limit of my knowledge so could somebody please point me in the right direction. Thanks. Xhi.

---

### Post by flixer on 2006-10-27
Have you tried 
```
sudo dpkg --configure -a
```

---

### Post by podunk on 2006-10-27
To become *the* superuser the code is:
```
sudo su
```

This is sort of an insecure and dangerous way  to run from all I've read. The only way i know to get  out superuser is to close all my terminal windows.

---

### Post by xhilyn on 2006-10-27
Oh thanks for such a quick reply. I should have known to have tried that myself, how stupid. It seems to have worked, I'm just waiting for it to finish updating to see if the update to edgy is complete.
Thanks again. xhi

---

