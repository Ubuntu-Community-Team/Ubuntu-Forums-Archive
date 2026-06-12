---
title: "Possible? 2 routers, 1 cable modem"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by feap on 2006-09-25
I have perhaps a strange question: I'd like to connect 2 routers to 1 cable modem. The problem is, the cable modem has only 1 connection for a router, so I would have to connect the 2nd router to the 1st one. Is this possible? How do I set up the 2nd router to tunnel to the internet?

---

### Post by bodhi.zazen on 2006-09-25
Depends on your router. My router(s) work out of the box, the cable (beteen the two) needs to be in the first position on the second router.

Just connect 'er up and c what happens.

---

### Post by rccharles on 2006-09-25
> **feap said:**
> I have perhaps a strange question: I'd like to connect 2 routers to 1 cable modem. The problem is, the cable modem has only 1 connection for a router, so I would have to connect the 2nd router to the 1st one. Is this possible? How do I set up the 2nd router to tunnel to the internet?

It's possible.

Perhaps you want to check with the networking people on:
[http://www.ubuntuforums.org/forumdisplay.php?f=136](http://www.ubuntuforums.org/forumdisplay.php?f=136)

Robert

---

### Post by superjet on 2006-09-25
feap,
 You should be able to plug your wan connection into the cable router, then plug the lan interface into the wan interface of the second router then plug your internal network into the lan port of the second router. 
 Please be advised you will (more than likely) need to change the IP scheme on one of the routers. Home routers usually come with the 192.168.1.X scheme.

 I hope that helps.
 Jamie

---

### Post by David Corrales on 2006-09-25
I had to do this for my home network (POS netgear router screws up msn video conferences... sigh). It's possible but if you don't know a bit about networks it's going to get funny. Especially trying to share files from computers in one network to the other.

---

### Post by deadgobby on 2006-09-25
If you are using a wire router, mine worked right out of the box. If you going to use wireless router, you may need to do some more work.
Gobby

---

### Post by GJS on 2006-09-25
Please describe what you want to acheive by connecting two routers to a cable modem as I cannot think of a situation where this would be required.

You can use a switch or hub between the cable modem and two routers but only if your ISP provides more than one IP address, which is unusual if you have a residential type service from them.

---

### Post by civic_si on 2006-09-25
> **GJS said:**
> Please describe what you want to acheive by connecting two routers to a cable modem as I cannot think of a situation where this would be required.

You can use a switch or hub between the cable modem and two routers but only if your ISP provides more than one IP address, which is unusual if you have a residential type service from them.

i have done this with a switch between the cable modem but you need multiple ip addresses because each router is going to want a seperate address. i dont think the ISP is going to let you get multiple DHCP addresses from them but i havent tried it with home service. i am guessing that is what you are using.

---

### Post by feap on 2006-09-25
I've disabled DHCP in the 2nd router as that's what many websites recommend. I still can't connect to the internet through the 2nd router, though. What kind of IP settings should I put on the 2nd router? I'm trying to connect my Nintendo DS wifi with the 2nd router as the DS doesn't work with the 1st one.

---

### Post by wildseven on 2006-09-25
i'm not quite sure, this being my first semester at college taking networking lol so don't tease me if i'm wrong, but can't you disable both dhcp on both routers and set a static ip for both routers and other nodes?

---

### Post by DyaruM on 2006-09-25
Well let me tell u something, I got RoadRunner 100mbps... I have one connection and 2 routers in my house. How I did it? I took one of those little things that the satelite TV uses and divided the line in two. Next, I bought a regular modem at Walmart hahaha and Put one modem in each router. I'm having a lot of fun doing that :D what I am trying is to make a Ubuntu network, but I am still working very hard :D

---

### Post by chrisfay on 2006-09-25
> I've disabled DHCP in the 2nd router as that's what many websites recommend. I still can't connect to the internet through the 2nd router, though. What kind of IP settings should I put on the 2nd router? I'm trying to connect my Nintendo DS wifi with the 2nd router as the DS doesn't work with the 1st one.

Does your router #2 have the option to switch between 'Gateway' and 'Router' mode? If you have router #1 as 'Gateway' and router #2 is also configured as 'Gateway' then their will be conflicts in your routing table. 

I know my linksys WRT54G has the option to add aditional routers within the network and disable the 'Gateway' function on each one except the actual router connected to the net. ie. router #1.

This is what my router says about the subject:

> Operating Mode : If the router is hosting your Internet connection, select Gateway mode. If another router exists on your network, select Router mode

---

