---
title: "what's my name on the LAN and how do i set it?"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by brallan on 2006-07-20
I have two machines in a network that seem to jam the router when i boot them up, and i need to go up to the roof and reset it, which is a major pain. in looking inside the router's DHCP table, I see that neither machine has a name. Could this be the issue?

I thought I assigned names to both during the dapper install and when setting up samba. does anyone know what my name is on the LAN and how to set it?

---

### Post by wahman143 on 2006-07-20
Hi,
To see your hostname, open a shell and issue the following commands:

```

$ sudo hostname
$ sudo hostname -f (gives you your FQDN)

(if you need to edit)
$ sudo nano -w /etc/hostname

```

Are your pc's getting an IP Address from the router (DHCP) or did you statically set their addresses?

W.

---

### Post by djsroknrol on 2006-07-20
Go to:
System>administration>Networking...you can see and change it in there..

---

### Post by crroush on 2006-07-25
>  Are your pc's getting an IP Address from the router (DHCP) or did you statically set their addresses?

I have the same issue, I set my router up as both a static IP and DHCP in both cases I could not get the router to determine what my hostname is.  I have been googling around for a while, but have yet to find a solution.

---

### Post by JimmyBEng on 2006-07-29
try this thread and see if it helps your problem.

[http://ubuntuforums.org/showthread.php?t=55564](http://ubuntuforums.org/showthread.php?t=55564)

---

### Post by brallan on 2006-08-01
well, the strange thing is, all the machines which appeared blank on the DHCPclient table DID have hostnames. When they appeared on the hosttable, they appeared with no name. Sometimes didn't appear at all but were connected to the internet. Other times I simply had to reboot the router, then plug in each switch waiting 10 seconds between each. 

Thanks for the thread, JimmyBEng, that seemed to do the trick.

---

### Post by brallan on 2006-08-03
oops, well actually, when i turned on the machines this morning the router once again froze. 

Can someone please help me diagnose this issue with the router? I'd really like to know if this is an issue with the router or my configuration of the network.

(I am going a little crazy having to run up to the roof to unplug the router each and every time any ubuntu machine gets turned on....)

---

