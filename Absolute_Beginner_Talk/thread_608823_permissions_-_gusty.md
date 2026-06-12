---
title: "permissions - gusty"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by agpby on 2007-11-10
hi everyone,

Im sorry if this has been asked before,

ive just switched from vista to gusty, i think I can figure out the basics the terminal, compiz fusion etc etc but one thing is making me maddddddddd and that is, permission.

It's my pc, i get the whole root sudo thing but i want to be the boss, i dont want to have to keep typing in passwords and i dont want to get messages saying i dont have permission to do this or that is there a way i can get around all this?

thanks in advance

also: not sure if this is a problem with my graphics card or not since i installed ubuntu, sometimes, with effects on or off, the top left of a window (where the title is) the color sort of fades and distorts?

thanks in advance :)

---

### Post by Sbarton on 2007-11-10
Hi! agpby, as far as the password is concerned you will find with use that this for security.
You can become authorised administrator by typing'sudo' to deal with permissions.
You might have a look here for some further info:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

regards

---

### Post by agpby on 2007-11-10
thanks Sbarton,

i realize you can get around it in the terminal but I was hoping to get some kind of work around for the gui parts, what i mean is that, now for example i tried to copy a folder into /usr/bin something like that and it wouldn't let me, and being a newbie to linux i dont want to have to try figure it out with the terminal yet, i just want to have the permission to do it, if that's possible?

thanks ;)

---

### Post by taurus on 2007-11-10
```
gksudo nautilus
```

---

### Post by chris.m.ball on 2007-11-10
I would place this post in the category "growing pains when moving from Windows to Linux".  Windows users have become accustomed to always using their computer with full administrative rights, even though that wasn't necessary for most of the time.

Part of the price you pay for having a secure OS without the need for virus protection, is having it be more logically locked down.

After you "sudo ...", I believe your sudo rights are available for 15 minutes without you having to type it again.  This typically gives you enough time to accomplish the administrative tasks you needed to do.

---

### Post by mikewhatever on 2007-11-10
Basically, you are the boss. Permissions is a practical tool to protect your system from intruders. 
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

