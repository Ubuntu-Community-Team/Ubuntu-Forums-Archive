---
title: "Do i install the desktop or the server for a LAMP setup, and the ability to browse?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by bowie101 on 2006-11-04
completely new to ubuntu. love the sounds i've gotten from it (6.10) so far. Just googled to figure out how to get the root password. although i sware i tried my user password, and it didn't work,  but that was more with the su -p . it didn't work. anyway, 


i just put ubuntu on a very old laptop that has not networking /internet access possibilities as of right now. it has no ethernet, so MAYBE dialup, but that's not tested and no ISP for it anyway, yet. (Now writing from my w2k desptop with the help of netzero dialup.) 

i installed ubuntu server, but then i didn't see any gnome or anything like that. what gives? says i. 

I need a LAMP set up , but in addition, I need to be able to browse the site with firefox from the same machine. this is for testing only.    i need a mysql server and client on the same machine, as I need to use it all on one machine. 

So do i install the desktop ubuntu or the server? Seems the desktop is L without the AMP. And server maybe AMP (unconfirmed) but without the ability to look at a localhost website. 

I only have the 1 Ubuntu 6.10 disk too. 


Thanks, b

---

### Post by K.Mandla on 2006-11-04
Yes, there's a straight server edition that comes without the AMP part. There's a page in the wiki that talks about putting those last three parts together.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Or you might try this howto.

[http://www.ubuntuforums.org/showthread.php?t=223805](http://www.ubuntuforums.org/showthread.php?t=223805)

If you want the Gnome desktop, you get it all with *sudo aptitude install ubuntu-desktop*. If you want something lighter than that, you might try *xubuntu-desktop* or even an Openbox, Fluxbox or Blackbox installation.

Have fun!

---

### Post by bowie101 on 2006-11-04
well, ok. so i have the desktop configuration installed now. is it easier at this point to install the AMP part of it (and if so, how?) 

or is it better to do a reinstall with the CD , from the beginning, this time, choosing the server ? 

and btw, the option i get doesn't say lamp server, it just says server. 

but if i'm reinstalling for the server config, what the easy, from-the-disk way to install a desktop and firefox with it as well? 

asking this question from 2 many angles leaves us all confused and incoherant. i know. sorry about that.
thanks, b

---

### Post by nereid on 2006-11-04
The L is just Linux. To get the rest (AMP) you have to install Apache, PHP5 (or 4 if you still need the older version), MySQL (version number corresponding to your PHP installation).

If you do this from the server or the desktop version from Ubuntu doesn't matter. The server version is nothing else than the desktop version without X. The howtos are for booth versions (in the server version you'll have to use the command line instead of the graphical installer).

---

### Post by bowie101 on 2006-11-04
ok, so then, (since i deem to be going around the question but not right at it)...


assuming i have the LAMP server setup installed. 

how do i install the desktop and firefox from that point, using only the install cd? (no internet connection on there)


    or

assuming i have the desktop setup, how do i install the AMP , using only the cd?

---

### Post by bowie101 on 2006-11-04
it is possible that i didn't read the first reply's related links for longer than 2 seconds... 


](*,)

---

### Post by bowie101 on 2006-11-04
well, I did the reading, and the sleep required...

seems as though if i go for the desktop option, I have to go online to the respository to get the MP (mysql , php), and I can get the A  (apache)from the CD. If I go the server route, it isn't clear how to then install the X  and Gnome graphical environment, firefox, and not to mention an adobe reader. 

i'm a bit ionvested now in keeping the desktop set up i have, as I've put afew thingson there from disks and such. but this isn't to say that I can't reverse course given a clear direction from one of you members out there.


All the documentation previously referred to refers to getting the packages from an (online) repository. Again, the laptop in question has no online / networking abilty, and this lovely machine that I now have is on dialup. 



 again, please advise. 

thanks.

---

