---
title: "Azureus/Ports"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by ZelasMetallium on 2006-04-28
Hope I spelt it right.  Umm, when configuring the program I got a NAT Error when testing the port and now I just got a pop up warning:

"If you have a router/firewall, please check that you have port 21016 UDP open."

Any help?

---

### Post by user1397 on 2006-04-28
do you have a firewall, if yes, what is it?

---

### Post by ZelasMetallium on 2006-04-28
Unless there's one automatically with Ubuntu then no.  I just installed it yesterday.

---

### Post by user1397 on 2006-04-28
i think firestarter comes automatically with ubuntu, but just the firewall, not the gui part (i'm not really sure at all). but w/e, just go to add applications and you'll find firestarter under system tools.  
when it's installed, open it and go to the policy tab. there, click on the white space under allow service, and pick bittorrent (yes, in the part where it says "when the source is", leave it as "everyone").  then click apply changes and it should work.

---

### Post by jazzmuzik on 2006-04-28
Most likely you have a modem or router that is blocking ports. This is good because it keeps you safe from outside attack, but in this case you need to open that one port needed by Azureus. Log into your modem (or router) with Firefox and see if you can set up "port forwarding" on port 21016. If you have a modem AND a router may need to port forward on each device -- like a chain -- so the packets can get all the way through from the Internet to Azureus.

I didn't think Firestarter is installed by default, but if a firewall script is being used you will ALSO have to tell your firewall software to open the same port.

---

