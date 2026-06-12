---
title: "How to open port on Modem SpeedStream 5200 (5242-Series)"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Pierrot Lafouine on 2008-04-04
Hi
I'm new to Linux.

I have installed Ubuntu 7.10, and I have a SpeedStream modem (all black, 5242 serie).  It has a DHCP server, and a basic web page at 192.168.2.1.  This is the symptom of the problem :

+ When I'm connected to Internet in DHCP mode, my friend is not able to open a SSH session on my computer, and also, I'm not able to do Remote Desktop under Windows.
+ When I'm connected to Internet in PPPoE mode, I'm able to do Remote Desktop under Windows.



I called and chat all day with Sympatico (my internet provider) to open the port 5800 for remote desktop and port 22 for SSH.

Sympatico are saying that the modem doesn't bloc any port.  According to them, there is no firewall, no DMZ and no port forwarding functionality in the modem.  It just forward all packet, and bloc none of them.

Also, I was told by level 2 technician at Sympatico, they replace modem's original firmware with there own firmware (what a shame).  So Efficient Network's user manual is useless for me.

Sympatico finally claims that I should add a router to the modem to fix my issue.  Maybe I'm not on the good forum, but I'm asking you guys (because I know your are good), if I add a router, would this fix my problem ?

What else should I try ?
Sorry for the long post
Thanks

---

### Post by neurostu on 2008-04-04
Do you have openssh-server installed? If you don't inbound ssh connections cannot be made.

To install it type:
```

sudo apt-get install openssh-server

```

---

### Post by neurostu on 2008-04-04
Regarding the "do remote desktop", what do you mean by this?  Are you trying to connect to a windows machine from ubuntu?

---

### Post by Pierrot Lafouine on 2008-04-04
> **neurostu said:**
> Do you have openssh-server installed? If you don't inbound ssh connections cannot be made.

To install it type:
```

sudo apt-get install openssh-server

```

I have done that, SSH is working fine
Need to open port 22 on modem to start SSH session

What is the next step ?

---

### Post by Pierrot Lafouine on 2008-04-04
> **neurostu said:**
> Regarding the "do remote desktop", what do you mean by this?  Are you trying to connect to a windows machine from ubuntu?

I tried to do Remote Desktop under windows to see if modem was problem.

I failed to perform :
1) remote desktop under Windoze XP (port 5800)
2) SSH session under Linux (port 22)

Both OSes are on the same computer (2 differnt HDD), using same modem (Ethernet wired modem SpeedStream 5200)

What can I tried next ?

Thanks

---

### Post by Pierrot Lafouine on 2008-04-04
What do you suggest me to try ?

Thanks!

---

### Post by Pierrot Lafouine on 2008-04-05
Any ideas to find out whats wrong ?

Thanks!

---

### Post by neurostu on 2008-04-05
The modem it self does not close ports. It is the firewall that is built into your OS that is closing ports. You should learn how to manage the built in firewall.

---

### Post by Pierrot Lafouine on 2008-04-05
> **neurostu said:**
> The modem it self does not close ports. It is the firewall that is built into your OS that is closing ports. You should learn how to manage the built in firewall.

I shutted down my firewall and didn't change anything.
Couldn't access SSH / remote desktop

Also I was able to do remote desktop with modem connected in PPPoE instead of DHCP.  So firewall doesn't seams to be the problem.

Thanks.

---

### Post by Pierrot Lafouine on 2008-04-06
Any ideas to open port on the SpeedStream ?
Thanks,

---

### Post by Pierrot Lafouine on 2008-04-07
If I add a router between the modem and the computer, can I create a PPPoE connection between modem and router, and open desired port in router ?

Thanks

---

### Post by Pierrot Lafouine on 2008-04-07
<<
 If it says Speedstream, Speedtouch, Westell, or Zyxel strongly suspect that it's a "combination modem/ROUTERS".  There ARE other brands that can be set up as a router, and these can sometimes be configured as "just a modem", so the brand isn't conclusive. 
>>

From : 
[http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841]("http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1139203841")

Hummmm look likes my provider is lying to me...
What do I do with that ?
Any suggestion ?

Thanks,

---

### Post by neurostu on 2008-04-07
Sorry man, but I can't help you anymore. I would suggest posting in a more advanced forum. Try looking around on this site for a Networking forum or check around on google for more advanced linux forums. You will be more likely to find someone there who can help you with your problem.

---

### Post by Pierrot Lafouine on 2008-04-07
> **neurostu said:**
> Sorry man, but I can't help you anymore. I would suggest posting in a more advanced forum. Try looking around on this site for a Networking forum or check around on google for more advanced linux forums. You will be more likely to find someone there who can help you with your problem.

Thanks

---

