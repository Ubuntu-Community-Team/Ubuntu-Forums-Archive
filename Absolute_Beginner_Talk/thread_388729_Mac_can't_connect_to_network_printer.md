---
title: "Mac can't connect to network printer"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ckrhines on 2007-03-19
Ubuntu (6.10) newbie here....  just made the switch from XP.

I've set up a local printer to my Ubuntu machine, and printing works great - was very easy to set up actually.

I have a small home network in place, but I can't get my Mac to "see" the printer that I have running on my Ubuntu machine.

From the Mac, I can see the network fine, and I can even see and access the few shared folders I've already set up in Ubuntu.

Does anybody know what might be causing my printer to not want to show up on the Mac?

---

### Post by ckrhines on 2007-03-20
Anyone?  Anybody?

---

### Post by charles.g.moore on 2007-03-20
> **ckrhines said:**
> Ubuntu (6.10) newbie here....  just made the switch from XP.

I've set up a local printer to my Ubuntu machine, and printing works great - was very easy to set up actually.

I have a small home network in place, but I can't get my Mac to "see" the printer that I have running on my Ubuntu machine.

From the Mac, I can see the network fine, and I can even see and access the few shared folders I've already set up in Ubuntu.

Does anybody know what might be causing my printer to not want to show up on the Mac?

I think you have to configure the cupsd.conf to listen on a port for printing, once that is done you can use the ip of your ubuntu box along w/the port number in your printer configuration on your mac

---

### Post by charles.g.moore on 2007-03-20
Did you install cups on your ubuntu box?  I'm not sure if it comes pre-installed

---

### Post by ckrhines on 2007-03-20
CUPS is running on the Ubuntu box, yes.  And I've editted the config file to something like:

Listen localhost:631

(That change was made as a result of some random Googling.)  However, I just saw a different post that instructs the user to change the config file to read:

Listen 631

Could that be the problem?  I'm away from my Ubuntu box while at the office, so I'll have to wait until a little later to try it.

---

### Post by ckrhines on 2007-03-21
I believe I answered my own question.  I updated the CUPS config file to say:

Listen 631

(the old line of code was:  Listen *:631)

To be honest, I'm not really sure WHY this worked, but it did.

---

### Post by charles.g.moore on 2007-03-21
> **ckrhines said:**
> CUPS is running on the Ubuntu box, yes.  And I've editted the config file to something like:

Listen localhost:631

(That change was made as a result of some random Googling.)  However, I just saw a different post that instructs the user to change the config file to read:

Listen 631

Could that be the problem?  I'm away from my Ubuntu box while at the office, so I'll have to wait until a little later to try it.

***Clip*** [http://www.ubuntuforums.org/showthread.php?p=1831119](http://www.ubuntuforums.org/showthread.php?p=1831119)
Set it to listen for connections from other machines
In the config file: 

change: Listen localhost:631
to: Listen 631

***********
I think I found the page for you... [http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

Check out section 3 !!!

Good luck

---

