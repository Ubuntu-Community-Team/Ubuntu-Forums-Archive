---
title: "OhBoy! Another dialup thread!"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by MrChips on 2006-03-23
Yes, this will be my fifth and FINAL request for dialup help.  I really want to run Linux as the primary OS.  But this is impossible as long as I have to rely on Windows Internet connection sharing to surf with Linux.

So then...I have run wvdial and have established a connection with my ISP.  Or so this sample from the terminal seems to say:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT3180110
--> Waiting for carrier.
ATDT3180110
CONNECT 49333/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
STATION ID - kvltn03rh02hp011,kvltn41ev
Welcome
Please Sign-on:
--> Looks like a login prompt.
--> Sending: 

(PERSONAL LOGIN INFO DELETED)

--> PPP negotiation detected.
--> Starting pppd at Thu Mar 23 18:22:12 2006
--> pid of pppd: 15634
--> Using interface ppp0
--> local  IP address 12.77.160.9
--> remote IP address 12.77.160.1
--> primary   DNS address 204.127.129.3
--> secondary DNS address 12.102.244.1

So I'm guessing I have a connection...Right?  Well the browser still cannot find any pages.  But will still connect through my Windows comp.  Which is where I am typing this from right now.  Ubuntu>WinXP>internet

This is my last chance!  DSL may never be available in my area and cable is over my family budget, and I don't want them digging a 200ft trench across my front yard either.  

I think this is a browser issue.  I believe the connection is there but the browser isn't looking in the right place for it. 

I have been using Ubuntu for a while now and I really like it.   This issue is really preventing me from going one step further and I would like not to be reliant on Windows for the internet. ](*,)

---

### Post by MrChips on 2006-03-23
Alright now I am on with the modem.  But I had to turn off the eth0 interface to do so.  And the modem connection has to remain inactive or it cuts off the wvdial connection.

Ok I'm getting confused...

Also the connection doesn't last.  It may go dead to the browser even though it says it is connected.  Really confused...

---

### Post by djheadley on 2006-03-23
Who is your ISP?

---

### Post by hajk on 2006-03-24
You seem to have two interfaces on your computer, ppp0 and eth0. The problem is most likely a routing problem: you should have ppp0 as the default route. What is the output from the "sudo route" command?

---

### Post by MrChips on 2006-03-24
ISP=ATTworldnet

And I think changing the default gateway would be the route to go.  But the Network settings window only gives the eth0 option.

Can this be changed in the terminal?

---

### Post by eriefisher on 2006-03-24
Change eth0 to static IP not DHCP and redial. I had the same problem and this is the only way I could maintain a connection.

eriefisher

---

### Post by MrChips on 2006-03-24
Actually my connection is steady for now.  The connection held for 8 hours last night downloading the updates from the repository.  But of course now it won't stop dialing, everytime I disconnect it dials up again.  ](*,)  Eh, that's another prob...for now I need to be able to activate the eth0 connection while I try to connect.

Everytime I activate eth0 while I have  ppp0 connected it interrupts and disconnects the dialup/ppp0.

I really need to change the default gateway...

---

