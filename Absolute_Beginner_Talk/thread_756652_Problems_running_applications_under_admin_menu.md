---
title: "Problems running applications under admin menu"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by trippnk on 2008-04-16
Okay, I've done lots of reading as I don't like being the one told to search!  I'm new to Linux but have a pretty good grasp on it so far.  I'm running 7.10 FYI.  My problem right now is that I can't seem to run most of the applications under the Administration menu for instance "User and Groups", Synaptic, Software Sources, and Sbackup.  When I click on an app it shows "starting administrative application" in my window list then closes.  I don't know how to fix this and its kinda annoying!  I can just use terminal to run most of these but its slow and less convenient.  Any suggestions would be much appreciated.

Thanks, Kendal

---

### Post by ryanhaigh on 2008-04-16
These application should be trying to run as administrator by using a program called gksudo (sudo for graphical stuff) which will show a little popup asking for your password, is this happening? It should happen at least once and then you wont have to do it again for 10minutes, basically it knows your admin for 10mins after you put the password in. 

You could try running gksudo synaptic or some other admin task from the command line and check the output as well.

---

### Post by trippnk on 2008-04-16
well I tried that and it did the same thing as going thru the menu.  I also never got a password request.  Strange.....

---

### Post by ad_267 on 2008-04-16
Did you get any output in the terminal? Something like an error message

---

### Post by erginemr on 2008-04-16
To complement the above post, try running the following command from the terminal:
```
gksudo synaptic
```
and please report back the error message.

---

### Post by trippnk on 2008-04-16
there is no error message after I type the code in terminal.  I think I'm just going to do a fresh install.  This was my first install of Ubuntu and I didn't get the partitions all setup how I wanted and also I did alot of tinkering to get the display working right and probably messed up somehting along the way.  Anyone have a recommendation on how to back everything up on a regular basis.  I installed Simple Backup... is that an okay program?

---

### Post by ad_267 on 2008-04-16
Instead of reinstalling everything you could just try reinstalling gksu, libgksu and libgksuui

---

