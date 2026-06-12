---
title: "vnc - What is syntax for host computer name ???"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-02-16
I am trying to setup VNC between 2 computer on in my home network which are connected to the internet thru a Westell 6100 router (per my Verizon DSL account).

When I run xvnc4viewer on one of the machines, it prompts me for the name of the computer that I want to connect to/view.

Is the name of that computer simply the name that I assigned to the Ubuntu computer during the setup/installation of Ubuntu (and apparently NOT since when I put that into the box, it says that it can not connect) or is the syntax for the name of the computer the name of my Verizon DSL Westell 6100 internet connection user name followed by the name of the Ubuntu computer ?  I have tried this in various syntax formats and so far, I have not been able to get it to work.

When I was running all of my computers with M/S windows O/Ss, I could get this to work using tightVNC, fairly simply but this sure does not seem to be very straight forward !!!

Thanks.

---

### Post by asmoore82 on 2008-02-16
vnc client and server are all ready built into Ubuntu 7.10
to configure the server, open "System -> Preferences -> Remote Desktop"

to run the client(to control a computer), open a terminal and run
```
vncviewer *<IP address of other computer in X.X.X.X format>*:0
```
example: ```
vncviewer 192.168.1.11:0
```
(the ":0" part tells it which desktop session to connect to,
which, on most single user Desktop machines, will always be ":0")

---

### Post by wpshooter on 2008-02-16
Is the information that I have read about using port forwarding necessary under these circumstances ?

Thanks.

---

### Post by wpshooter on 2008-02-16
One more question.

When you run the remote desktop command from the Preferences menu, what program is actually being run ?  Is it the "VNC_**4**_SERVER" program or something else ?

Thanks.

---

### Post by Peter09 on 2008-02-16
You will most probably need to use port forwarding if you are using a router with a NAT firewall and you wish to connect to your machine across the internet.

The 192.xxx.xxx.xxx form of I.P is  used for internal addresses on your LAN. Across the internet your IP address will be that designated by your ISP and will be different. The IP  that external machines see is the ISP address not the internal one.

Your NAT router changes any internal IP addresses  to the external one for you, and can keep track of conversations being held by many machines on the internal side with those on the external side.

If you are using a modem, then your IP address will be the same as that given to you by your ISP.

Port forwarding tells your NAT firewall/router to direct all traffic from an external source (using that port) to an internal IP address (one machine).

You will not need port forwarding if you are only using your internal LAN.

---

### Post by wpshooter on 2008-02-17
> **Peter09 said:**
> You will most probably need to use port forwarding if you are using a router with a NAT firewall and you wish to connect to your machine across the internet.

The 192.xxx.xxx.xxx form of I.P is  used for internal addresses on your LAN. Across the internet your IP address will be that designated by your ISP and will be different. The IP  that external machines see is the ISP address not the internal one.

Your NAT router changes any internal IP addresses  to the external one for you, and can keep track of conversations being held by many machines on the internal side with those on the external side.

If you are using a modem, then your IP address will be the same as that given to you by your ISP.

Port forwarding tells your NAT firewall/router to direct all traffic from an external source (using that port) to an internal IP address (one machine).

You will not need port forwarding if you are only using your internal LAN.

Thanks.

I finally got the VNC to work internally on my LAN.

Now on to the outside world.

Am I understanding Port Forwarding correctly, in that, this needs to be done only on the router of the machine/location that is to **BE** viewed and NOT necessarily on the machine that is going to be **DOING** the viewing ???

And, in the instructions that I have found at portforward.com, is it really necessary to forward all 3 of the ports that are mentioned (5500,5800, & 5900).  And what is the significance of the services names (VNC1, VNC2, & VNC3) that are used there ?  Do those service names have to be used any where else in the VNC process as a routing parameter to get the VNC to function ?

[http://portforward.com/english/routers/port_forwarding/Westell/Westell6100/VNC.htm](http://portforward.com/english/routers/port_forwarding/Westell/Westell6100/VNC.htm)

Thanks.

---

### Post by wpshooter on 2008-02-19
Anyone have an answer to my last posted questions regarding port forwarding.

And also, if I am wanting to use VNC outside of my home/internal LAN over my Verizon DSL to a computer outside of my home network, do I have to have a name descriptor that is more than that which is given by the vncserver/remote desktop function program  (which is basically the name of my Ubuntu machine followed by **myhome.westell.com:0**) under the System/preferences menu of Ubuntu ?   I.E. that descriptor worked fine internally between 2 of my LAN machines, will it work over the Verizon DSL connection ?  

I called Verizon about this and their reply was that they could not give support for VNC program.  But they did volunteer that the **myhome.westell.com **was NOT a unique descriptor.

Thanks.

---

