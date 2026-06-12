---
title: "HELP Desktop is gone...."
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by satrich on 2007-02-15
I did not shut off my computer the right way.
Now when I start up, the system hangs, after login with my normal user account.
I just see a mouse cursor and a blue screen....

I can start up a terminal and then 'sudo su' and then do 'startx'. But how do I recover my normal user account?

PLEASE HELP....

---

### Post by Sqwishy on 2007-02-15
Probobly you updated your kernel and you need to reinstall your graphics drivers.
If your using nvidia you can try to use envy.
[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

### Post by anaconda on 2007-02-15
could also be filesystem corruption.. not likely, but I had once.

I boooted from the liveCD and run fsck on my ubuntu partition and it fixed my hd!!

I think the command was
fsck -f /dev/hda2
,where hda2 is my ubuntu partition. Just run the command on your partition.. you dont even have to mount it..

---

### Post by satrich on 2007-02-15
No that is not the case. 
I can login as root, and everything is ok. That is what I am doing now, writing this message as root on my system. So I suppose that xorg.conf is ok and the drivers are ok too. And also no corrupt kernel or something like that, otherwise I could not log in at all.

It is just a little unsafe to work as root on my system.

I think it has something to do with sessions. But I don't know that much about linux to solve it.

---

### Post by satrich on 2007-02-15
Ok, I am back in business. But not with my original login.
In terminal I could log in as root. Then I started X with startx.
Then I made a new user account, and now all my desktop settings are gone but it is working.

Is there some way to recover the old account?

---

