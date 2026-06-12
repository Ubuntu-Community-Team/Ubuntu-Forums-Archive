---
title: "[SOLVED] Start times slow"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by puterboy on 2008-02-07
So I am having some problems with my program start times. Any help would be appreciated. I tried searching, but came upon a lot of boot time problems, but I believe mine is different.

When I freshly installed, everything ran fine. I'm dual-booting, using Gutsy, there have been no kernel updates since I installed, I have upgraded everything in Synaptic, but I am getting a slower boot time, but the thing that's annoying me most is my program start times. It used to be half a second to start Terminal, now it takes at least 10, and that the same with pretty much everything, EXCEPT VLC and some other programs. Would this be a problem with something all the slow programs depend on, and that the quick ones do not? Just a guess. Can anyone point out how to figure this out? Thanks in advance for any help

Puterboy

---

### Post by Crumpets and Jam on 2008-02-07
> **puterboy said:**
> So I am having some problems with my program start times. Any help would be appreciated. I tried searching, but came upon a lot of boot time problems, but I believe mine is different.

When I freshly installed, everything ran fine. I'm dual-booting, using Gutsy, there have been no kernel updates since I installed, I have upgraded everything in Synaptic, but I am getting a slower boot time, but the thing that's annoying me most is my program start times. It used to be half a second to start Terminal, now it takes at least 10, and that the same with pretty much everything, EXCEPT VLC and some other programs. Would this be a problem with something all the slow programs depend on, and that the quick ones do not? Just a guess. Can anyone point out how to figure this out? Thanks in advance for any help

Puterboy

How much RAM do you have in your machine?

---

### Post by jordanmthomas on 2008-02-07
One thing that can mess with program start times is a messed up hostname.
What do you have in this file:
```
/etc/hosts
```
If you don't have a line like this:
```
127.0.0.1       yourcomputername.localdomain   localhost yourcomputername

```
Then programs will have a tough time connecting to your xserver (or so I understand)

It's a shot in the dark, but it would be a good explanation for your troubles.

---

### Post by puterboy on 2008-02-07
@Crumpets and Jam - 1GB

@jordanmthomas - 

  GNU nano 2.0.6              File: /etc/hosts                                  

127.0.0.1 localhost cam-desktop.OURHOME
127.0.1.1 cam-desktop.OURHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Is it the IPv6 stuff?

---

### Post by jordanmthomas on 2008-02-07
It could possibly be it.  If you have no need for ipv6, it doesn't do any harm to remove it.
Look up how on the forums.

Your hosts file looks fine, by the way.  Really all you needed was for localhost to resolve to 127.0.0.1

---

### Post by puterboy on 2008-02-07
Well, I'm not sure exactly why, but it's gone. It's either changing

127.0.0.1 localhost cam-desktop.OURHOME

to

127.0.0.1 cam-desktop localhost cam-desktop.OURHOME


OR

removing IcedTea Java, as I has both Sun Java and IcedTea installed at the same time. Dunno which. Thanks for the help!

---

### Post by puterboy on 2008-02-07
CORRECTION: It was editing the hosts file

---

### Post by JurB on 2008-02-11
Had the same problem, editing hosts did it for me also.
Tnx

---

