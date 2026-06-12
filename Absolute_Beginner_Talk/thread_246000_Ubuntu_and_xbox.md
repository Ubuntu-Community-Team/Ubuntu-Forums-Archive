---
title: "Ubuntu and xbox"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by s1k3st on 2006-08-28
I've been trying to get my xbox to have internet access through my pc, but I'm not really sure where to start.  I've got a wireless connection to the net, then my xbox is connected to my pc through an ethernet cable.  In windows I had to enable connection sharing, so is there something similar in ubuntu?  If so, how do I go about setting it up?

---

### Post by FizDev on 2006-08-28
Hmmm... this is only a wild guess but, try following this thread :
[http://www.ubuntuforums.org/showthread.php?t=91370]("http://www.ubuntuforums.org/showthread.php?t=91370")

...or you could buy a router ;)

---

### Post by s1k3st on 2006-08-28
I have a wireless router that sends my connection to my pc. From there I would like it to go to my xbox (for xbmc scripts).

---

### Post by Toxicity999 on 2006-08-29
By connecting an Xbox to an Ubuntu PC you undo all that is the fabric of time!

Now that the warnings out of the way shouldn't it work like any other share? Or does it use the typical Microsoft route with some kind of specific software to setup a link between the best and the PC?

What your actually trying to do is to get the router to conect the PC which is happenning then the PC forwarding access to the Xbox right? Why not just get the Xbox working with the router directly and worry about file transfers later (I assume thats what you were after otherwise?)

---

### Post by jamesr316 on 2006-08-29
the xbox probably isnt close to the router or he/she would just do that. Since he/she said that the PC uses a wireless connection, i would assume the PC isnt near the router. And since the xbox is near the pc (via ethernet cable) i assume it isn't near the router either. 

sorry about the issue though, i have no clue how to fix that. i am a beginner myself.

---

### Post by s1k3st on 2006-08-29
Yes, jamesr316's right, my pc and xbox are upstairs and my router is downstairs.  Anyone got any ideas?

---

### Post by steven43126 on 2006-08-29
Sorry i just read through this quickly are you trying t get internet access from your xbox? but routing it through your pc? If so you need to use NAT search for linux NAT or ip masquerading.

An example script here [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES)

Alternatively you could give the xbox it's own ip address and get your pc workas a transparent router, this way you could access your xbox without having to mess around with any port forwarding issues, you'll have to look for how to do this on the net it's been a whie since i did anything like it.

The other option if you have a fast machine, is to run a virtual machine, and install a dedicated router distro like [http://www.zebra.org/](http://www.zebra.org/).

three options to consider but the easiset is probably the first one. ;)

---

### Post by rupert on 2006-08-29
maybe just install firestarter and enabled the routing there, should work out of the box.

---

### Post by wdcrls on 2006-09-23
i have ubunu and Xbox to, but the internet works just fine. i only had to make an internet sharing on my pc and set the ip's on the xbox. my computer and Xbox are linked together through a switch.
i don't think that the problem is the distance from your wireless conection since u have conetion to the internet on your computer.
I have another problem. i want to share my windows partitions with the Xbox but i dunno how. i can acess some of the files on my compter (from the linux partition) but with other files it says that i don't have permision, and i can't see the windows partitions at all. :(  help [-o< .

---

