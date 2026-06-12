---
title: "Cannot access the internet."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by quicksilver1234 on 2007-06-28
I'm trying set up Ubuntu 6.06 LTS as a server. 
I have done something bad so I cannot access the internet out.  My webserver is working. I dial in my ip address and I see my site. So the outside world can get into the machine. but from my Ubuntu box, my firefox no longer has a connection out. Ping doesn't work. I seem to have messed up a firefire table or another config to  access the internet. 
Any thoughts on what I need to do?

---

### Post by lintoon on 2007-06-28
Hi quicksilver,  I think we need more info.  When you say you can dial in your IP address do you mean type  the IP address into your browser on the PC which cannot connect to the internet or into the browser of another PC on the network, or "dial in" (using a modem) from somewhere outside the building.

When you say ping does not work do you mean you ping from the "faulty" pc and cannot get a reply or ping from another PC to the webserve and cannot get a reply.  If this is the case I would look at your IP address.  Is it manually configured or assigned by DHCP.   Could it be a faulty cable.  Is your network port enabled.  Have you got a link light on your modem/router.

Have you changed any firewall settings.

---

### Post by quicksilver1234 on 2007-06-28
On another machine I can type in the IP address of the Ubuntu server box 12.34.56.78 and I get the apache web site on that address.
However, if I go sit at that box and try to use firefox, it tells me that I don't have a connection.
It feels like I have done something to block access going out.

---

### Post by quicksilver1234 on 2007-06-28
>>Have you changed any firewall settings.
I may have broken firewall settings. How would I check that?

---

### Post by quicksilver1234 on 2007-06-28
ahhh. I can type the working computers's ip address 98.76.54.32 from the linux box and get a response.

---

### Post by quicksilver1234 on 2007-06-28
I'm trying to install ISPConfig.  Could that be the problem?

---

### Post by quicksilver1234 on 2007-06-28
Does ISPconfig have a firewall?

---

### Post by lintoon on 2007-06-29
Hi Quicksilver,  I'm not an expert with ubuntu or anything.  You can ping the webserver and you can ping from the webserver this would imply that your IP settings are ok.  

If you cannot access the internet I would check DNS settings, default gateway setting or firewall settings.

I don't know anything about ISPConfig but a quick search brought up this link.
[http://ispconfig.org/downloads/manual_en/manual_admin_en_src.htm](http://ispconfig.org/downloads/manual_en/manual_admin_en_src.htm)

Section 2.4.3 mentions a firewall within ISPConfig.  

Sorry, I'm not much help.  Hopfully someone more linux literate can help you more.

---

