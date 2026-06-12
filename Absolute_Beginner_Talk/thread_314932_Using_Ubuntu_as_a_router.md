---
title: "Using Ubuntu as a router"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by chelseapete on 2006-12-08
I'm not sure if this is the right place to ask but...
I've never used Linux before but now have need to set up a dedicated machine to route between three networks (not the Internet) Would I be able to use Ubuntu for this? Would it be possible to get simple instructions on how to do this somewhere?
TIA
Peter

---

### Post by brt on 2006-12-08
check this out:

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

---

### Post by Cryptic1911 on 2006-12-08
Although Ubuntu is pretty easy to setup, I think you'd be better off using something dedicated for that task.. trying to setup a system like that as your first linux machine probably wouldnt be the easiest task. Try looking up IPCop or Clarkconnect.. that seems more along the lines of what you would want to use

---

### Post by civic_si on 2006-12-08
the first thing that you would need is to install three network cards in to the box. setup the three cards on the networks that you wanted them to be on.

then turn on routing 

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

this will have to be done each time the computer restarts because of the way the /proc part of the system works. 

then you would have to write a routing table and for the routes between the networks. I have not done this in a while so i cant remember but i think you can put all of this into a script and the set it to start at startup. 

the commands to add routes is route add but you may want to check and see if Ubuntu added the routes for you

route -n

will show all of the routes on the box. the one starting i 0.0.0.0 is the default route.

I will have to try and remember what needs to be added for the script to make the machine route to the other networks.
I am at work now and will post more for you later.

---

### Post by chelseapete on 2006-12-09
> **brt said:**
> check this out:

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

Thanks - Thats a useful link, It will take me a while to make sense of the info though.

---

### Post by chelseapete on 2006-12-09
> **civic_si said:**
> the first thing that you would need is to install three network cards in to the box. setup the three cards on the networks that you wanted them to be on.

then turn on routing 

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

this will have to be done each time the computer restarts because of the way the /proc part of the system works. 

then you would have to write a routing table and for the routes between the networks. I have not done this in a while so i cant remember but i think you can put all of this into a script and the set it to start at startup. 

the commands to add routes is route add but you may want to check and see if Ubuntu added the routes for you

route -n

will show all of the routes on the box. the one starting i 0.0.0.0 is the default route.

I will have to try and remember what needs to be added for the script to make the machine route to the other networks.
I am at work now and will post more for you later.

Thanks for this - I'd like the info whenever you get the time to send/post it.

---

### Post by Bobtheknight on 2006-12-09
I don't have any information to help but I do have a question.

I have always heard of using linux boxes as a router.  And I always wondered what advantage that would be to using a commercially bought router.  

Assuming I have already a linux box, but I only have 1 network card.  Under what circumstances would I buy more network cards to make a router?  Also assuming I can set up both linux box and the commercially bought router as well as they can function.

Thanks :D

---

### Post by beefcurry on 2006-12-09
> **Bobtheknight said:**
> I don't have any information to help but I do have a question.

I have always heard of using linux boxes as a router.  And I always wondered what advantage that would be to using a commercially bought router.  

Assuming I have already a linux box, but I only have 1 network card.  Under what circumstances would I buy more network cards to make a router?  Also assuming I can set up both linux box and the commercially bought router as well as they can function.

Thanks :D

there are many types of commercial routers, industrial grade big fat juicy onces with loads of RAM CPU etc, those can function as a firewall as well as a router for BIG networks, but for small networks of less then 5-10 computers a small home one is sufficient. The advantages of a linux one (depending on the system specs) would normally be faster, able to handle more connections, more advanced functions, more customizable (i.e. using Gigabit lan unlike the majority of megabit lan out there). They depend on your hardware. AND you CAN by commercial linux routers (with what i just described), most people dont go around building their own. I am under impression that the "commerically brought" router you can talking about are the small puny ones that you plug 3-4 pc's into.

---

### Post by civic_si on 2006-12-09
it would be easier for me to tell you how to do this if i could have the network addresses and subnet masks for the networks that you want to route to. The setup for making a Linux box as a router is pretty easy but you have to know how routing works. if you can give me those addresses i can pretty much write the file for you and explain how it works.

---

### Post by chelseapete on 2007-01-03
Sorry for the delay in accepting your offer - it was a very difficult December but thankfully thats finished with. I just want to route between 192.168.5.0/24 and 192.168.52.0/24
Thanks
Peter

---

