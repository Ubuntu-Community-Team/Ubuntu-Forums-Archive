---
title: "[SOLVED] enabling repositories"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-08-31
hello everyone
trying to enable repositories by following guide in [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
problem is when i update list for fiesty i got the following output;

E:Could not get lock( /var/lib/dpkg/lock )- open (11 resource temporarily unavailable)
E:Could not lock the administration directory ( /var/lib/dpkg/ ) is another process using it?

how do i overcome this very simply.

also in sorces.list(/etc/apt)-gedit
"uncomment the following two lines to fetch updated software from the network" 
what does that mean?

---

### Post by jackocleebrown on 2007-08-31
Halo!

You get that error because there is another program open that can install programs from these repositories - you can only use one of these at a time so that Ubuntu does not get confused about what you have installed. These programs are "Synaptic" "Update Manager" (there are also some others) if you shut any of these that are running your error should disappear.

Jack.

---

### Post by bodhi.zazen on 2007-08-31
> **jon zendatta said:**
> hello everyone
trying to enable repositories by following guide in [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
problem is when i update list for fiesty i got the following output;

> E:Could not get lock( /var/lib/dpkg/lock )- open (11 resource temporarily unavailable)
E:Could not lock the administration directory ( /var/lib/dpkg/ ) is another process using it?

how do i overcome this very simply.

This error message either means you did not run as root (**sudo** apt-get update[/code] or you have another package manager open (add/remove programs, update manager, synaptic ...)

> also in sorces.list(/etc/apt)-gedit
"uncomment the following two lines to fetch updated software from the network" 
what does that mean?

The # at a beginning of a line = comments

So,  remove the #

(actually # can be used anywhere to add commnets, not just at the beginning of a line)

---

### Post by jon zendatta on 2007-08-31
awes0me got it thank you

---

### Post by Irihapeti on 2007-08-31
Greetings, fellow kiwi! 

Irihapeti

---

