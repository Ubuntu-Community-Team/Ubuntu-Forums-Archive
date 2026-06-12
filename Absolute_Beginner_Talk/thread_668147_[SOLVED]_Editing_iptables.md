---
title: "[SOLVED] Editing iptables"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-15
Hi. I am (trying) to learn about iptables as used in Ubuntu (I'm running gnome by the way). In the process I have looked at Guarddog and Firestarter, and ended up preferring Firestarter.

Having used Guarddog once, and then moved over to Firestarter I am interested in learning how to  configure iptables myself, perhaps with a view to writing something of my own as a front end to it. After a little hunt about I found that the file I need to look at is /etc/rc.firewall

I looked briefly at it using gedit (Don't worry, I didn't change a thing!) and the thing that concerns me is that at the very top of the file is a message that suggests that the file is owned by Guarddog, although I have configured the file far more with Firestarter.

Now for a few questions:
1)
Is this file the right one? I know that guarddog was used (Once), but I now use firestarter, so I just want to check that I'm actually dealing with the right file.

2)
Assuming that I am looking at, or that I find the right file, is it permissible to edit it manually, and if so how would I have any edits taken into account without a reboot?

3)
If I actually edit the file will those edits be visible in Firestarter? I'm asking this one because having edited the firewall with firestarter I then opened guarddog (Not in admin mode - I just wanted a look) and the changes that were made by firestarter are not visible (Or at least not readily apparent).

Any help you can give here would be much appreciated. Iv found a whole bunch of tutorials about iptables, but so far (And Iv not read everything yet) Iv see nothing about manual editing, or about how the programs (Firestarter, Guarddog) actually interact with the file. I'm a little concerned that the two do not seem to be reading the same file.

Thanks

Max

---

### Post by MaxVK on 2008-01-15
Bah! I was getting confused with the configuration files. Doh!

I like the way Firestarter works, but it has a nasty bug and keeps dropping out, which is the reason why I'm looking to write something myself. Its really just a front end for the console commands that I would normally want to type in if I were adding a port etc.

Anyway, all firewalls are removed and iptables are reset.

---

### Post by carverj on 2008-01-15
Did a quick 'man iptables'
right down the bottom it refers to:-
[http://www.netfilter.org/](http://www.netfilter.org/)
hours of fun.....
but yeah, got a bit excited.... firestarter is great!

---

### Post by frodon on 2008-01-15
I have written 2 tutorial on the topic, perform a search in the tutorial section with me as author and iptables as keyword, you should find them directly. You will see, it is not that complicated for someone interested.

---

### Post by MaxVK on 2008-01-15
Thanks frodon - Ill look through those later tonight.

---

