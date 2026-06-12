---
title: "Cannot initialize HAL!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by johnh289 on 2007-10-21
i just installed ubuntu 7.04 on my computer and then ran the upgrade to install 7.1. after i installed 7.1 whenever i login it comes up with an error saying "failed to initialize HAL!" 

also, i am not sure if they are related in any way, but i cant connect to the internet, which i was able to before off of 7.04 and i can also connect to it when i go into xp (dual boot)

if i have to i suppose i can just do it all over again and install everything over but i would rather not because it took a while!  :)


any help would be extremely appreciated!!!!!!!


thanks 
John

---

### Post by johnh289 on 2007-10-21
oh! and one other thing

it probably has nothing to do with either of the above things, but when i click the little green running guy to shutdown the computer it takes about a minute to bring up the "shutdown,restart,switch user, etc) window

any ideas!?

thanks!

---

### Post by oilchangeguy on 2007-10-21
> **johnh289 said:**
> i just installed ubuntu 7.04 on my computer and then ran the upgrade to install 7.1. after i installed 7.1 whenever i login it comes up with an error saying "failed to initialize HAL!" 

also, i am not sure if they are related in any way, but i cant connect to the internet, which i was able to before off of 7.04 and i can also connect to it when i go into xp (dual boot)

if i have to i suppose i can just do it all over again and install everything over but i would rather not because it took a while!  :)


any help would be extremely appreciated!!!!!!!


thanks 
John


since you just installed 7.04 only to do the upgrade to 7.10, is there a special reason why you can't burn a 7.10 cd and install it that way?

---

### Post by johnh289 on 2007-10-21
i just used the "wubi" program which only has 7.04 on their website right now because i was having some trouble installing it normally.

---

### Post by oilchangeguy on 2007-10-21
> **johnh289 said:**
> i just used the "wubi" program which only has 7.04 on their website right now because i was having some trouble installing it normally.

wubi is beta software. and when using beta software if it breaks something, you get to keep both pieces. i'd suggest removing any trace of wubi, and dual boot the correct way. see this;
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by rookie_paul on 2007-10-21
Have you tried to boot in recovery mode?

---

### Post by johnh289 on 2007-10-21
no i havent how would i go about doing that?

---

### Post by rookie_paul on 2007-10-21
I assume you have a dual-boot system. When it asks for the OS to boot, you should choose the (usually) the second choice (it ends with "recovery" or something similar). It should boot without starting the GUI.

---

### Post by johnh289 on 2007-10-21
when it gets to the dual boot menu it just shows windows xp and ubuntu


im probably doing something wrong... im pretty new at this  :)

---

### Post by rookie_paul on 2007-10-21
Don't worry: I felt like an absolute stupid during my first days in linux! Now it's a little better but I am still a newbie.
You could try to open a terminal window and hit:

> sudo apt-get -f install

or

> sudo apt-get dist-upgrade

what does it say?

---

### Post by johnh289 on 2007-10-21
the only trouble i have installing it normally is when i get it fully installed it doesnt show up on the dual boot menu. but when i install it using wubi it worked fine.

---

### Post by alzie on 2007-10-21
I installed feisty using WUBI also and when I upgraded I ran into the same problems.  

Being new at this I don't know if the url will work but it explains how to update to gutsy from a wubi install.  Good luck.

[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

I ended up doing a clean install of 7.04 using an alt386iso cd

---

### Post by aktiwers on 2007-10-21
Its a bug, and its been here for a while. Looks like they found a fix for it now :)
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

---

