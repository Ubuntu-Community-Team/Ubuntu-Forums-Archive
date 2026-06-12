---
title: "Live CD login"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by ammunition on 2007-05-07
Hi, I wonder what the password for Ubuntu 7.04 in love mode is.
Thanks for answer. :)

---

### Post by fakie_flip on 2007-05-07
What is "love mode"? I'm sorry. I don't know what you meant.

---

### Post by ammunition on 2007-05-07
Oops, sorry, i mean live mode.

---

### Post by croxi on 2007-05-07
the password is what you set it as, when you installed the OS you needed to specify a password and your name so that you will have administrator rights too. 

Without it you're pretty screwed, I was too, so I decided that since I didn't have any programs or files saved anywhere, that I would just reinstall UBUNTU 7.04 and rather simply write the password  on a handy piece of paper until I could remember it without a cribsheet. 

Anyway, I hope that you've not got anything really important saved on your UBUNTU because my solution won't help, but if you've not got anything saved, my solution might be of some worth to you. 

I hope its going to be good for you...

---

### Post by fakie_flip on 2007-05-07
There is no password in live mode, but if you want one, give the command.

passwd

or for a root password

sudo passwd root

and then you can login as root on the live cd

su - root

---

### Post by Cypher on 2007-05-07
> **fakie_flip said:**
> There is no password in live mode, but if you want one, give the command.

passwd

or for a root password

sudo passwd root

and then you can login as root on the live cd

su - root
And unless you take some extra steps to persist these changes, they will be wiped out the next time you reboot into the Live CD..

---

