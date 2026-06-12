---
title: "Xubuntu Hangs on Runlevel 2"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by yawny on 2007-07-22
I'm a BSD guy, but am a Debian/*ubuntu noob.

The good news: I installed Feisty Fawn (7.04) Xubuntu successfully on an old Compaq Presario 1675 laptop (192 RAM) using the Alternate CD.

The bad news: it boots most of the way, but dies hard while loading X.

Now, if I boot into recovery mode and then run startx, root gets an X session just fine. But if I boot into recovery and then telinit 2 | 3 | etc. I get a hang. The console shows it choking just after the printing stuff loads (cups and then the HP Linux stuff). 

I don't know enough about boot process on these distros to be very smart about this. Like what typically loads after HP Linux printing services? 

I thought maybe I should go into /etc/rc.2 and disable some services by lowercasing the S on services I don't need, but that seems awfully groping-in-the-dark. Can someone help a little?

Thanks - 
John

---

### Post by tist on 2007-08-01
Dear John

To troubleshoot this, see what the login manager gives from the recovery console. Run ```
/etc/init.d/gdm start
```

If that fails, check in /var/log/gdm/ what went wrong.

Basically, all startup script go into /etc/init.d and /etc/rc#.d just contains symbolic links to /etc/init.d with the code in front whether to start or stop and priority. So if you go for the awfully groping-in-the-dark option, work your way down from S99 to the culprit!

Cheers
tist

---

