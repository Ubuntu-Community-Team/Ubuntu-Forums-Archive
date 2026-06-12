---
title: "How to start up *any* daemon automatically upon boot?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by jngnyc on 2007-01-29
Hi all,

Completely ubuntu newbie here :)

Anyway, I recently installed hamachi, a peer to peer vpn that requires a daemon called tuncfg in order to run.

My question is, how can I edit some configuration file so that this daemon tuncfg starts up automatically?

right now, I have to type sudo tuncfg to start the daemon, and then I can go on to start my other pgoram that requires it.

Another followup question, would also be, how can I start up a service automatically as well? Right now, I have to start up the daemon, then type 'hamachi start' to start everything.

It's a super big hassle considering I have to constantly reboot for various reasons.

Thanks everyone!

---

### Post by Pelham123 on 2007-01-29
I have used sysv-rc-conf to speed up the boot process by stopping programs running at start-up. I'm guessing that this could be used to start daemons at boot-up as well? Take a look at these links..

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process)

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Hope this helps!

---

### Post by kerry_s on 2007-01-29
For the "tuncfg" since that need root access you can start that with rc.local

For "hamachi start" stick that in the session start up.

Here the directions:
sudo gedit /etc/init.d/rc.local

put the command> tuncfg & <right under the #!/bin/sh, see pic->

Now for the second part, i'm not using gnome so i'm not sure of the location for the session startup apps is, look under administration. when you find it just click the last tab "startup apps" and add  your "hamachi start".

---

### Post by jngnyc on 2007-02-07
Haven't gotten a chance (school and working are ripping me apart) to try your two suggestions... but I wanted to thank you anyway for responding. I'll be sure to update here whether they worked or not. Thanks again!!!

---

### Post by jngnyc on 2007-02-07
That thumbnail is aweesome. thanks so much!

---

### Post by kerry_s on 2007-02-07
Update: The proper place to put it now is /etc/rc.local, there's now a file for startup apps, but it will still work in both places, just letting you know the option.

gksu gedit /etc/rc.local

tuncfg & 

So now it looks like->

---

### Post by mlwalla on 2007-03-30
hey all,
do thumbnails expire after a week or two?  This post is extremely helpful, but I'm a little shy of messing with these config files and it seems like the pictures would be helpful... could someone repost?

---

