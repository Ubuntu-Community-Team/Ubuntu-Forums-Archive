---
title: "ubuntu firewall"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Eddie002Fast on 2007-10-29
how do i find the ubuntu firewall so i can enable/disable it ? 
                                                                                                                                    Thumbs up  Bean Count?
OK, what is the bean count thingy? I think that it is my post count... but I'm not sure. Also, whats with the actual beans? I started with 1 green bean, and now have 2. Is it just a meter to show visibly how many posts you have? (1-40 posts =1 green, the rest brown, 40-70 posts =2 green, the rest brown...... 10000-20000 posts =5 giant creme coffees...)  <---LOL!

---

### Post by Eddie002Fast on 2007-10-29
Just so everyone knows in my last thread i copied a thing that someone else said on these forums that i thought was very funny LOL!..........but still curious on how to find my firewall so i can enable/disable it......also any ubuntu security programs you guys recommend? Thx!!!! :D

---

### Post by santiagoward2000 on 2007-10-29
> **Eddie002Fast said:**
> how do i find the ubuntu firewall so i can enable/disable it ? 
                                                                                                                                    Thumbs up  Bean Count?
OK, what is the bean count thingy? I think that it is my post count... but I'm not sure. Also, whats with the actual beans? I started with 1 green bean, and now have 2. Is it just a meter to show visibly how many posts you have? (1-40 posts =1 green, the rest brown, 40-70 posts =2 green, the rest brown...... 10000-20000 posts =5 giant creme coffees...)  <---LOL!

About the firewall, you should install Firestater. It's in Synaptic. Then run it, and you'll be able to disable it.

---

### Post by Lord_Dicranius on 2007-10-29
iptables is used for the firewall in linux.  It's basically a text file, and can be a little hard to manage for beginners.  As for a GUI to configure iptables, there's a couple that I would recommend: firestarter (gnome - good, easy to use), guarddog (kde - good, easy to use), shorewall (gnome - a little harder to setup, but once you get the hang of it, very good).

---

### Post by Eddie002Fast on 2007-10-29
Thx guys !!! I'll try it out now :D

---

### Post by hyper_ch on 2007-10-29
by default you should not need to alter iptables and hence no need to install firestarter...

---

### Post by julian67 on 2007-10-29
The firewall is disabled by default. You do not need to do anything. iptables is unconfigured on a default Ubuntu install and allows all traffic.

---

### Post by skymera on 2007-10-29
iptables is your packet filer :wink:
thus your firewall

you can get a GUI for this:

sudo apt-get install firestarter

:D

---

