---
title: "port forwarding"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Drew32 on 2006-08-31
hey all,

My friend is in college at the moment and wants to play a game called diablo 2 over battle.net.  Battle.net servers run on port 6112, but that port is blocked at his college.  so i want to allow him to connect to my ubuntu linux server on port 4 (one of the ports i know that is opened at his college) and then have my server send those packets recieved on port 4 to port 6112.  any suggestions on what to you server side?  Since his computer is running windows, im going to have him use FreeCap.

Thanks in advanced.

~Drew

---

### Post by Scorpuk on 2006-09-01
This sounds a tad complicated and I'm not even 50% sure how to do this, but my "theory" is:


You will probably need to use port triggering (if your router supports it)

So that incoming port 4 will be passed onto port 6112. My router options are:

```
                         Triggered Range             Forwarded Range  
Application      Start Port     End Port     Start port     End Port       Enable  

```
 
You would probably then have to forward port 6112 to the server IP address. Now this is the difficult part as your router would have to let you type in the full IP address and not the last digits of the local IP address, ie 192.168.1.xxx.

Oh and it would probably be best to forward UDP and TCP.

Are you sure its just 1 port you need to handle as I've dabbled with game servers on my linuxc box and its a heap of ports I needed to forward.


Anywho good luck.:smile:

---

