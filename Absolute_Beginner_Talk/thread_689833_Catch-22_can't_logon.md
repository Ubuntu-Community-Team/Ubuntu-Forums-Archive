---
title: "Catch-22: can't logon"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by brake16 on 2008-02-06
Help!

I can't log onto my machine.  I was trying to skip the wireless network password logon, so I modified /etc/pam.d/gdm at the end with the following line:
@include common-pamkeyring

(originally suggested here: [http://ubuntuforums.org/showthread.php?t=577641](http://ubuntuforums.org/showthread.php?t=577641))

When I rebooted to try it out, I got to the logon screen and I was instantly greeted with an error message that says "Authentication Failed".  I clicked on the 'OK' box and the same error message repeated (infinitely).  I can't even ctrl-alt-del my way out.  I have to hold the power button to get out of it.

I'm using the live-cd to post this message.  I can get to the modified /etc/pam.d/gdm using the live-cd, but it won't let me delete that extra line because I don't have the right permissions.  Is there someway to login with my normal (administrator) account starting from the live-cd?  Is there some other way to change this back?

Any ideas (short of deleting the partition and reloading Ubuntu)?

brake16

---

### Post by jordanmthomas on 2008-02-06
You should be able to edit it on the liveCD if you do a 
```
gksudo gedit /wherever/you/mounted/your/ubuntu/etc/pam.d/gdm
```

---

### Post by Rocket2DMn on 2008-02-06
I had this problem as well, as have other users recently (must be a recent update)
At the login screen to CTRL+ALT+F1 to get to a tty and login.
```
sudo nano /etc/pam.d/gdm
```
Go down to the line and delete it.  Exit nano (ctrl+x?) then get back to the login screen with CTRL+ALT+F7 and click OK one more time, then you can log in.

PS: The LiveCD works, too :).  Just make sure you have the partition mounted and you aren't fiddling the one on the LiveCD (if you even can).

---

### Post by randomnote1 on 2008-02-06
When you boot off the live cd, you don't want to edit the /etc/pam.d/gdm as it is in a temporary file system and will accomplish nothing.  When you boot off the live cd run a df -h from the terminal to find out what drives are mounted and where.  From there you should be able to edit /<hard drives mount point>/etc/pam.d/gdm and that is the file that is actually on your hard drive.  When you edit that make sure you do it as sudo.  Good luck!

---

### Post by brake16 on 2008-02-07
> **Rocket2DMn said:**
> I had this problem as well, as have other users recently (must be a recent update)
At the login screen to CTRL+ALT+F1 to get to a tty and login.
```
sudo nano /etc/pam.d/gdm
```
Go down to the line and delete it.  Exit nano (ctrl+x?) then get back to the login screen with CTRL+ALT+F7 and click OK one more time, then you can log in.

PS: The LiveCD works, too :).  Just make sure you have the partition mounted and you aren't fiddling the one on the LiveCD (if you even can).

Thank you so much.  I was hoping that there would be some sort of "side door" to login through.  This was exactly what I needed.

I think I may actually fall in love with Ubuntu.:D

brake16

---

