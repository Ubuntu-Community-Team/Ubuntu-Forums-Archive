---
title: "Complete retard needs help with firewall"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Seaniesean on 2008-01-01
Hello, just installed Ubuntu, looks good.  However, i've had problems installing a firewall.  Something about "universe repositary" springs to mind as being useful.  Anyway, if someone could explain, in extremely clear and unambiguous language, how i can install a firewall, i'd be very grateful.  Please help. i'm worried!!!

---

### Post by hyper_ch on 2008-01-01
If you could say what problem you have with the firewall? Do you mean iptables?

---

### Post by Seaniesean on 2008-01-01
IP tables, yeah, that'd be great!  How do i get it?

I mean trouble as in, please could you tell me exactly how to install it?  Thanks very much for the reply, crikey, that was quick!

PS i just installed linux, never used it before.

---

### Post by hyper_ch on 2008-01-01
IPTables is installed by default.. I still fail to see what your problem is.

---

### Post by mmb1 on 2008-01-01
Hi, go to system-administration-synaptic package manager.  Click the search box and enter "firestarter", install the package, and you should be well on your way.

---

### Post by jken146 on 2008-01-01
Firestarter is not a firewall, it is just a GUI tool for adding rules to iptables.  Iptable is installed already and runs in the background, with all ports closed.  You probably don't need to do anything at all.

---

### Post by Seaniesean on 2008-01-01
Installed by default?  Really?  Then i guess i don't have a problem.  I couldn't find iptables anywhere yet, how do i verify i have it?

Quote-"I still fail to see what your problem is."

My problem is that i don't have the first clue about linux.

If i have iptables, i guess i don't need the firestarter thing?  Sorry to sound stupid, i'm a windows user. And not a very good one.

Thanks again.

Quote-"You probably don't need to do anything at all." Thats what i like to hear!

---

### Post by hyper_ch on 2008-01-01
Correction: Ports are not closed by default on iptables - there are just no services listening to ports. That's a difference!

---

### Post by jken146 on 2008-01-01
> **hyper_ch said:**
> Correction: Ports are not closed by default on iptables - there are just no services listening to ports. That's a difference!

My bad!  Thanks for reminding me.


To the OP:  You can check in Synaptic.

---

### Post by p_quarles on 2008-01-01
> **jken146 said:**
> Firestarter is not a firewall, it is just a GUI tool for adding rules to iptables.  Iptable is installed already and runs in the background, with all ports closed.  You probably don't need to do anything at all.
Not so. You can see your iptables rules by running this command:
```
sudo iptables -L
```
You will find that the default installation leaves all ports *open*. They are, however, effectively closed, as there are no services listening on any ports. The distinction between "closed" and "effectively closed" is very important, however. The minute you start running services (including many games) it's a good idea to have a way of filtering packets.

To the OP: I second the recommendation of Firestarter, as it's an easy way to setup a basic firewall. If you were having trouble with the universe repository not being enabled, you can enable it in the "software sources" tab of the Synaptic package manager.

---

### Post by nille on 2008-01-01
From the System-menu, or via Synaptic, you can reach the Repository-settings. There you can make sure Universe is checked. After that you can install Firestarter, which is a graphical user interface as described earlier.

You can install it either using Add/Remove, Synaptic or via the terminal:
**sudo apt-get install firestarter**

---

### Post by hyper_ch on 2008-01-01
> **Seaniesean said:**
> Installed by default?  Really?
Yes it is.

> **Seaniesean said:**
> Then i guess i don't have a problem.
As long as you don't run service like apache or similiar you are well set with iptables.

> **Seaniesean said:**
>  I couldn't find iptables anywhere yet, how do i verify i have it?
You cuold add rules to it and check it. Ypi ,ay want to have a read here: [http://en.wikipedia.org/wiki/Iptables](http://en.wikipedia.org/wiki/Iptables)

> **Seaniesean said:**
> My problem is that i don't have the first clue about linux.
Well, if you encounter a problem, just ask in the forums here... and even better if you first try and research yourself using the forum's search function, google etc ;)

> **Seaniesean said:**
> If i have iptables, i guess i don't need the firestarter thing?
Firestarter is just a GUI to do basic configuration of iptables. Well, I haven't bothered using it at all... I'm behind a router anyway because of my internet connection. Very likely you don't have to bother yourself also.

> **Seaniesean said:**
> Sorry to sound stupid, i'm a windows user. And not a very good one.
Linux is in many aspects quite different from Winodze so it doesn't matter if you're a good windoze user or not... more likely you're more confortable when you are not a windoze guru... Here's quite a good site why windoze gurus have more troubles adjusting:  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

> **Seaniesean said:**
> Thanks again.
No problem, we all started at 0 and we all encounter problems ;)

---

### Post by jken146 on 2008-01-01
Thanks for putting me straight guys!  I guess I spend too much time behind the firewall in my router.

---

### Post by Seaniesean on 2008-01-01
Hey, pretty groovy.  Linux looks great actually, and most of the programs i use like gimp and blender are all on linux too.  I got firestarter installed, i think, so i'm going to have a play around.  I expect i'll be back later with more lackwit questions for you all, thanks very much!

---

### Post by mmb1 on 2008-01-01
> **jken146 said:**
> Firestarter is not a firewall, it is just a GUI tool for adding rules to iptables.  Iptable is installed already and runs in the background, with all ports closed.  You probably don't need to do anything at all.


My bad, thanks for correcting me.  :)

---

