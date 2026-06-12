---
title: "internet connection w/live cd of 6.10 doesn't work"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by doron387 on 2007-01-15
i have laptop : hp pavilion dv6102ea, with processor : amd mobile sempron, i am trying to connect to the internet w/ubuntu 6.10 live-cd but it doesn't work.
my connection to the web is threw : B-FOCUS ROUTER 312+ of ECI which is now configured to have inner firewall (i hope i describe it well, as i am a newby....)
i want to check and learn the ubuntu o.s. b4 i download it to my machine so i am using live cd.

questions :
1. can i connect to the web w/live cd ?
2. how to do it ? (and please, if somebody has graphic way to explain it, it will be great !!!)

i will be on the the web in the next 2 hrs.
thnx all of u
doron
](*,)

another important 2 questions :
3. when i am booting with the live cd, should i choose (1) start or install ubuntu  or  (2) start ubuntu in safe graphic mode 
4. when i am quiting the session it usually freezes after i am being asked to take off the cd and after i am taking it out, and i am sure that it is wrong.

---

### Post by ferg on 2007-01-15
First I suppose we should establish... wired or wireless? :p

---

### Post by clint1010 on 2007-01-15
Did the internet connection work OK on you laptop with the other OS you are using?

---

### Post by doron387 on 2007-01-15
wired

---

### Post by doron387 on 2007-01-15
yes

---

### Post by clint1010 on 2007-01-15
have you use DHCP or a static IP address with other OS on your laptop?

---

### Post by ferg on 2007-01-15
System > Administration > Networking

There should be a "Wired Connection" or "eth0" under the connection tab... check that is enabled... then click properties and configure anything you need to. 

Hope that goes some way to helping :)

+ what clint says... if you use DHCP then it should, in theory, just work. If not enter those settings!!

---

### Post by doron387 on 2007-01-15
> **clint1010 said:**
> have you use DHCP or a static IP address with other OS on your laptop?

i am not totally understanding your question, 
yesterday i tried DHCP and static IP with the 6.06 and it didn't work in neither of the ways.
with the windows os i am using DHCP but i dont know how to check it in windows.

---

### Post by ferg on 2007-01-15
In Windows go to Network Connections then right click your ethernet connection and view status. On one of the tabs you will find the three fields (IP, Subnet and Gateway) that you can enter in the network settings on Ubuntu. Scribble those down and try them out on the live CD.

Long time since I used Windows but essentially that's how you find it out :)

---

### Post by doron387 on 2007-01-15
> **ferg said:**
> System > Administration > Networking

There should be a "Wired Connection" or "eth0" under the connection tab... check that is enabled... then click properties and configure anything you need to. 

Hope that goes some way to helping :)

+ what clint says... if you use DHCP then it should, in theory, just work. If not enter those settings!!


does eth0 mean wireless ?
when i last tried it it wad enabled on wired connection and i tried both DHCP and STATIC IP, in bothcases the "orange line" was moving and it was saying that it is configuring...
but, connection - none

---

### Post by clint1010 on 2007-01-15
To check it in windows =>start=>settings=>control panel. Double click the network settings icon (or named similar). You should have there a LAN connection there, double click and look at the properties. Highlight TCP/IP and click properties. There you will either see blank fields in grey, or white fields with numbers in. If it is grey, you are using DHCP, if white with numbers, it is static. If it is white with numbers, write them down, you'll need them for ubuntu setup.

---

### Post by ferg on 2007-01-15
eth0 is the name assigned to your first ethernet port. Your second would be eth1 and so on. My wireless is name ra0.

---

### Post by doron387 on 2007-01-15
> **ferg said:**
> In Windows go to Network Connections then right click your ethernet connection and view status. On one of the tabs you will find the three fields (IP, Subnet and Gateway) that you can enter in the network settings on Ubuntu. Scribble those down and try them out on the live CD.

Long time since I used Windows but essentially that's how you find it out :)

yeterday, with help of somebody who understands a bit more than me in windows, he showed me how to get these three numbers (ip, gateway, etc...) and it was threw the terminal of windows.
but
i tried to write these info and it did not work.

---

### Post by clint1010 on 2007-01-15
> **doron387 said:**
> does eth0 mean wireless ?
when i last tried it it wad enabled on wired connection and i tried both DHCP and STATIC IP, in bothcases the "orange line" was moving and it was saying that it is configuring...
but, connection - none

eth0 is your network device, be it wired or otherwise. Make sure it is enabled

---

