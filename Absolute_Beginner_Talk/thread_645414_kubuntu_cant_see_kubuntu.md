---
title: "kubuntu cant see kubuntu"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by phantalon on 2007-12-20
Hi....I am a complete novice and i have two computers with kubuntu but i cant get them to see each other...how do i set up networking so that these two will see each other?

---

### Post by jbt on 2007-12-20
> **phantalon said:**
> Hi....I am a complete novice and i have two computers with kubuntu but i cant get them to see each other...how do i set up networking so that these two will see each other?

What do you mean "they can't see each other" ?

I assume that you have the network cables correctly installed, and they have different IP addresses.

Can you ping one from the other ?

eg to ping machine with IP address 192.168.0.1

1) get a console window.
   (Applications->Accessories->Terminal) in the gnome menu.

2) type:
   ping 192.168.0.1

What do you see ?

should be something like:

$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.270 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.225 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.230 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.236 ms



Regards
JohnT

---

### Post by phantalon on 2007-12-20
thanks for responding...sorry it took so long to get back...I did what you suggested and received back the first line but not the rest...they do have different ip addresses....by the way we have a windows box set up in another room and both the kubuntu boxes see that one fine, they just wont see each other...by see I mean they dont show up on either box anywhere...ive shared files but cant 'see' them on either box...all the proper 'nfs' files are installed but no luck

---

### Post by jbt on 2007-12-20
Seems odd that they can both see the windows box, but can't ping each other !

Do they have wireless AND wired, or two ethernet cards ?
are all the machines (windows and linux) on the same network ?

---

### Post by phantalon on 2007-12-20
....thanks again for responding........wired only and yes all on same network.

---

