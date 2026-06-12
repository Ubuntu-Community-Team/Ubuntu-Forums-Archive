---
title: "[SOLVED] Firestarter not on Ubuntu!?!"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-06-09
Okay, another question.....  Why isnt my version of Ubuntu showing Firestarter????

I'm running Dapper Drake 6.06....

When I type:

[COLOR="Red"]sudo apt-get install firestarter
[/COLOR]
I get:

[COLOR="Red"]Building dependency tree... Done
E: Couldn't find package firestarter
[/COLOR]
What am I doing wrong?


thanks
john

---

### Post by kevdog on 2007-06-09
Try typing:

sudo aptitude update
sudo aptitude install firestarter

If this doesnt work, you might have to edit your /etc/apt/sources.list to include additional repositories -- universe, multiverse.  I cant for remember for the life of me what group firestarter belongs to.

Do this with
gksu gedit /etc/apt/sources.list

---

### Post by jimrz on 2007-06-09
> **john wagner said:**
> Okay, another question.....  Why isnt my version of Ubuntu showing Firestarter????

I'm running Dapper Drake 6.06....

When I type:

[COLOR="Red"]sudo apt-get install firestarter
[/COLOR]
I get:

[COLOR="Red"]Building dependency tree... Done
E: Couldn't find package firestarter
[/COLOR]
What am I doing wrong?


thanks
john

you probably need to enable additional repositories
it is available through Synaptic in the universe repo , at least in feisty.
firestarter is a gui frontend for iptables which is your actual firewall.
I checked my dapper dvd and it is not on it, though I am sure it was available and iptables is there.

---

