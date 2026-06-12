---
title: "not sure what to do with command prob"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Mrpelletier on 2006-11-18
I am trying to install different things but this same thing shows up here is an example code.


mrpelletier@mrpelletier-laptop:~$ deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
bash: deb: command not found
mrpelletier@mrpelletier-laptop:~$ deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
bash: deb-src: command not found
mrpelletier@mrpelletier-laptop:~$ 


Can you guys help:confused:

---

### Post by CatKiller on 2006-11-18
Those aren't commands to be entered into the Terminal; rather, they look like lines to be added to the end of your sources.list.

If that is the case, then you'll want to use ```
gksudo gedit /etc/apt/sources.list
``` and then put your lines at the bottom.

You might want to put a line above them, starting with a **#** (which means that line is a "comment") saying what they are for, so that you can remember, should the need arise.

---

### Post by taurus on 2006-11-18
What are you trying to do here?  Are you trying to add some repos to your /etc/apt/sources.list?

---

### Post by Mrpelletier on 2006-11-18
> **taurus said:**
> What are you trying to do here?  Are you trying to add some repos to your /etc/apt/sources.list?


ok well im trying to install flash 9 but when i do some message shows up also if i go to synaptic it sais this "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

y"

Im not sure why ? i think this may be why i cannot install flash nine package

---

### Post by taurus on 2006-11-18
If you want to install flash 9, use automatix to do that for you.

[http://www.getautomatix.com](http://www.getautomatix.com)

---

