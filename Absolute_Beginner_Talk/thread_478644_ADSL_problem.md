---
title: "ADSL problem"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-06-19
when  used PPPOE on terminal to configure my ADSL i got following error ---->


Sorry, I scanned 1 interface, but the Access             &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason      &#9474;          
          &#9474; for the scan failure may also be another running pppoe   &#9474;          
          &#9474; process which controls the modem.

---

### Post by Alex&amp;Linux on 2007-06-19
> **ferronica said:**
> when  used PPPOE on terminal to configure my ADSL i got following error ---->


Sorry, I scanned 1 interface, but the Access             &#9474;          
          &#9474; Concentrator of your provider did not respond. Please    &#9474;          
          &#9474; check your network and modem cables. Another reason      &#9474;          
          &#9474; for the scan failure may also be another running pppoe   &#9474;          
          &#9474; process which controls the modem.

Hey man!
Im assuming youre trying to connect to the internet (not "configure my ADSL [modem]")
Looks like in this case the problem is somewhere between your computer and your home gateway.
PPPoE connections are very strait forward when setup on your PC, and im sure the problem isnt whit that.

First thing to do would be to powercycle (powerdown for a minute) any networking infrastructure in your home (adsl modem, any routers/hubs/physical firewals)
Check all rj-45s and the rj-11 (connecting your DSL modem to phone line)

Next, the lights on your modem will indicate the status of its functions. There will be any of the following to indicate that you have sync with your ISP's hardware

Sync, Link, ADSL, DSL, Line ect.

That needs to be solid! If no, contact ISP!

Next check LAN or Ethernet lights, usually blinking. If off, theres likely a problem with the cable.

If youre connected to a router, or any other device before your linux box, try bypassing it for a direct connection to your PC, and then use your PPP connection again

If you get the same error...well, depending on the network youre attached to (on the WAN side) you could require a bridged modem with PPP layer established through your next device (router, PC), but in a lot of cases, your ADSL modem can be configured for a few different network protocols (that is to say that you can have it do the work :))

In that case, you can contact ISP and set that up 
Usually:

Network protocol: PPPoE/ATM
Data encapsulation: VC-MUX/LLC/LLC-SNAP
Vci = 0/8
Vpi = 35/100
ISP username
ISP password

If this cant be done through your ADSL modem, then if you have virtually any router on the market, you could use that to establish PPP, no problem!

I hope that any of that can help!
Saludos!

---

### Post by ferronica on 2007-06-20
i am using ADSL modem which work on Phone line, i have to set user ID and PASSWORD. Do i need to use IP address, DNS,subnetmask and gateway if yes then why in windows no need to use all these IP, these all are set to acquire automatically.

---

### Post by Alex&amp;Linux on 2007-06-20
You said:
"i am using ADSL modem which work on Phone line, i have to set user ID and PASSWORD. Do i need to use IP address, DNS,subnetmask and gateway if yes then why in windows no need to use all these IP, these all are set to acquire automatically."

The answer is no, you should not have to do anything different when establishing PPP via your Ubuntu machine (as far as I know :))

With windows, setting up a PPPoE dialer (broadband dialer) doesnt require you to specify any IP addressing (you get this automatically after connecting to the "access concentrator")
Is everything working at the moment when you use windows?
If so that would localize the problem to your Linux box!

As I said before, it is usually possible to configure your ADSL modem, or a router to make the PPP connection for you!
In this regard, you would contact your service providor, no problem!

If there is a problem with your technical support not supporting a router to set this up, than I would be happy to help you take a stab at it, or you could call the suport for the router (if you have one :))

buena suerte!

---

### Post by bugmenot_user on 2007-06-21
I experienced same problem. with network-admin, I can connect successfully. but pppoeconf gives same error.

---

### Post by S15_88 on 2007-06-21
set the wired connection to roaming mode, then do pppoeconf, it will ask u for ur username and password in the setup.  then use: pon dsl-provider to start the connection then poff dsl-provider to end connection.

---

### Post by bugmenot_user on 2007-06-21
There is no "roaming mode" (dapper). But when eth0 is not activated and not enabled, I'm trying pppoeconf and the result is same
Isn't there any other solution to connect automatically?

---

