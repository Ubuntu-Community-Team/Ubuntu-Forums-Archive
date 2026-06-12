---
title: "Stuck at first login..."
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kikapu on 2007-03-03
Hi to all, 

it is really great to be here! I am abandoning Windows and last night i installed Ubuntu 6.10 at my laptop. I make a dual-boot system, following some info that i found on the net and all went well.

I passed the difficult task of repartitioning a hard disk with an existing Windows installation and all the details, and i am stuck in a very, eexmm, easy task: Login at first time in Ubuntu...

The first time i boot to the (install completed) Ubuntu, it asks me for a login.
I remember that sometime during the installation i was asked for a password which i gave 2 times, but wat is the Username that it asks me for ??

I know "root" i not active at this time, what i have to give there so i can (first) login to the system ??


Tanks a lot for any help, it is just too funny (at least...) to not be able to login!


Thanks again!

---

### Post by Tomosaur on 2007-03-03
The installation will have asked you to provide a login username and password. If you can't remember it, boot into recovery mode and type:
```

ls /home

```

There will be a folder in there with the user-name you provided. Hopefully this will jog your memory a bit :P

---

### Post by kikapu on 2007-03-03
Hey, a million thanks!! That was it. I tried that and it gave me "oem".
When i installed Ubuntu, i selected the second choice in the install menu which indeed was saying somethong about "OEM". (i was doing it at 3am, so, bear with me!)

So the username is this and i am able now to login!

For another installations, will i be doing the same thing (choosing OEM) or is it better to install by the first choice of the menu ( i do not remember exactly the label) ?

Thanks again, going back to Ubuntu and read the forum from there...:popcorn:

---

### Post by mcduck on 2007-03-03
> **kikapu said:**
> Hey, a million thanks!! That was it. I tried that and it gave me "oem".
When i installed Ubuntu, i selected the second choice in the install menu which indeed was saying somethong about "OEM". (i was doing it at 3am, so, bear with me!)

So the username is this and i am able now to login!

For another installations, will i be doing the same thing (choosing OEM) or is it better to install by the first choice of the menu ( i do not remember exactly the label) ?

Thanks again, going back to Ubuntu and read the forum from there...:popcorn:

The OEM install is absolutely no use for anything else than pre-installing Ubuntu on computers you are going to sell or something. Use the normal install. This is not windows, where OEM install costs less ;)

Anyway, since you already used the OEM install you should finish it properly: open a terminal and run 'sudo oem-config-prepare' and reboot the machine. Ubuntu will then go through the wizard to create the actual user account for you.

---

### Post by kikapu on 2007-03-03
Thanks, i did it, create a new user and all went fine.
Thanks again!

---

### Post by neu9 on 2007-11-11
thanks very lot for this topic : I found the reason of my first problem, and I discovered the next problem and his solution....
:-)

---

