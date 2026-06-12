---
title: "Connect to a remote pc via the internet"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-19
Hi I have just returned home from my dad (he lives in Denmark me in England). I would like to ssh into his computer so that I can help him with different tasks. He is behind a router and his server that has the local ip address 192.168.0.124 and when I was connected from his local network I could without a problem ssh into that using ```
ssh username@192.168.0.124
```
I could also just type it into my web browser and I had access from there.

However now when Im back in the uk I would like to connect via the internet insteat of the local network. I have got his external IP address which he found at myip.dk but nothing happens when i type it into my browser

I followed the instructions here
[http://rubbervir.us/projects/ubuntu_media_server/part3.php](http://rubbervir.us/projects/ubuntu_media_server/part3.php)

Is it because I have to change something in apache  to allow external connections or?

Another thing that confuses me: When I get it to work how do i controil which PC on that external IP address that Im connecting to? My dad has three pc's on that local network and every one of them returns the same external ip address! And then they have different local ip addresses, Im interested in conecting to the pc on the external ip address that has a local ip address ending in on .124

I'm CONFUSED!!

---

### Post by kelnage on 2007-09-19
Hey there,

What you have to do is at your Dad's end you must configure the router to do "Port Forwarding" for your SSH connections. How to do that depends on the model of the router he uses. However, if you can find out what router he uses, we can probably help.

Port Forwarding will allow to you connect to the IP address though a port of your choice and connect to a specific PC. For instance, you might configure it like this:

Connecting on port 22 from outside forwards to 192.168.0.1:22
Connecting on port 23 from outside forwards to 192.168.0.2:22

And so on.

You'll have to do a similar thing for connections on port 80 to make Apache work.

---

### Post by kasperbs on 2007-09-20
Hi hes got a Dlink DI-54 router. I found this guide on how to configure SSH on it:
[http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-514/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-514/SSH.htm)

I think I'm starting to understand it a bit, but could you please clarify how I know which of the three pc's Im connected to. In otherr word elaborate a little bit on this:
> Port Forwarding will allow to you connect to the IP address though a port of your choice and connect to a specific PC. For instance, you might configure it like this:

Connecting on port 22 from outside forwards to 192.168.0.1:22
Connecting on port 23 from outside forwards to 192.168.0.2:22


Let's say hes got two computers Im interested in. His Desktop with local IP of 192.168.0.149, and his Server with the IP of 192.168.0.124

Thanks
Kasper

---

### Post by hyper_ch on 2007-09-20
he will need to setup the port forwarding seperately to each computer in the lan on the router...

e.g. incoming port 22 on the router shall point to: 192.168.0.149 Port: 22
incoming port 23 on the router shall point to: 192.168.0.124 Port:22

---

### Post by mattmole on 2007-09-20
Hi,

Lets say you Dad's router has the IP address .1, and the internet IP address is w.x.y.z

When you ssh to w.x.y.z you actually are trying to access port 22 (assuming default SSH settings) on the router.

If you want to connect to the desktop then you need to tell the router to forward all connections to itself on port 22 to port 22 on the desktop (.149)

If you then want to connect to the server then you can tell your machine at home to use port 23 instead of port 22. Then when the router received a request on port 23, it will forward it to port 22 on the server (.124)

Does that help at all? It probably isnt very clear, typically, things clear in my head dont make sense to others.

mattmole

---

### Post by kasperbs on 2007-09-20
Ok yes it is starting to make sense now. So lets say I open port 22 on my router to the desktop ip 192.168.0.149

And i forward port 23 to the server 192.168.0.124

And now on my pc I want to connect to my dads desktop. Would I then type this in terminal:
assume his external ip is: 11.22.33.444
ssh dad@11.22.33.444:22

and for the server:
ssh dad@11.22.33.444:23

Am i completely wrong?

---

### Post by mattmole on 2007-09-20
Yes, I am sure you are correct.

mattmole :)

---

### Post by kasperbs on 2007-09-20
Hi I had him open the port 22 to the ip: 192.168.0.124 which is the server, but when i try to access his server from my terminal i get the following error:
> ssh dad@11.22.33.444
ssh: connect to host 11.22.33.444 port 22: Connection refused

---

### Post by mattmole on 2007-09-20
Hi,

So you/he told the router to forward port 22 to port 22 at the desktops IP?

Weird, I can only assume the wrong port is forwarding to the desktop.

Try using the network tools under System->Administration to do a portscan of your Dad's internet IP address and see if port 22 is open.

mattmole

---

### Post by darren1270 on 2007-09-20
I've just installed crossloop under wine... real easy to use in windows haven't tried it in ubuntu but it does appear to work.

Good Luck
Darren

No port forwarding issues down through a secure internet connection

---

### Post by kasperbs on 2007-09-20
> **mattmole said:**
> Try using the network tools under System->Administration to do a portscan of your Dad's internet IP address and see if port 22 is open.

mattmole

That scan take forever and doesn't find anything

---

### Post by mattmole on 2007-09-20
hmmm, weird.

It sounds to me like the port hasnt been forwarded on the router correctly. If no ports are showing on the scan then the router must still be blocking port 22.

Also try in a terminal:

telnet w.x.y.z 22

If you get connection refused or similar then port 22 is closed.

---

### Post by kasperbs on 2007-09-20
> telnet w.x.y.z 22
Trying w.x.y.z...
telnet: Unable to connect to remote host: Connection refused

I guess the port isn't opened

But I actually now got a result after scanning his internet ip for 30 minutes, it says that port 2033 and port 2121 is opened.

I dont now what could be wrong because I walked him through forwarding the ports on his Dlink router.

I followed from here [http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-514/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-514/SSH.htm)

and told him to set the following:
> 
Enabled
Name: SSH1
Private IP: 192.168.0.149
Protocol Type: Both
Private Port: 22
Public Port: 22
Scheduled: Always

Can he do anything else?

EDIT: If it makes any difference, he can ssh into my computer

---

### Post by mattmole on 2007-09-21
Hi again,

He can SSH into yours? I take it you have forwarded the SSH port on your router? Is it the same model?

Also, you said that you could SSH when you were connected to his home network? That means that locally it works.

I can only think the router is playing silly games if the port is not showing as open. Because port 22 is so low down it should only take a few means to see if your port 22 (the routers port) is open.

If that works, then I really can only assume his router is at fault.

mattmole

---

### Post by PreviousN on 2007-09-21
YOU FOOLS!!!

His dad's computer doesn't have ssh installed. tell your dad to type
sudo apt-get install ssh

actually. I'm wrong. he was sshing into it earlier...can I still call you all fools?

Hmm..you might want to check the router to make sure the settings saved/are enabled. On my router there's a checkbox next to the port forward that needs to be ticked in order for it to be "enabled". 

Other than that you could try turning on ssh on the ROUTER.. That way you could ssh into your dad's router, and then ssh from that into the local computer. Kinda like taking a stopover when traveling.

---

### Post by mattmole on 2007-09-21
Nope, no fool comments allowed ;).

It is a curious fault isn't it. I really think the port must be shut on the router.

---

### Post by hyper_ch on 2007-09-21
The port forwarding was not setup correctly on the router.

---

### Post by Herman on 2007-09-21
Does it need to be able to go through some kind of a broadband modem-router from the internet as well, before you even get to the D-Link router?

I know mine does. I have a Thompson Speedtouch 530 Broadband modem-router at my place, that is teed into the phone line coming in. (For ADSL). That has a Linux firewall like IPTables, but it's accessible via firefox, and can be configured that way, to allow an external (incoming) connection. That needs to be port-forwarded first before I even get to the D-Link. 
Thanks kasperbs, for the great links here in this thread. Now I know what I need to do too. I have been interested in doing the same thing but until now I haven't bothered looking into it very well. I found the page I need now, in my case it's: [http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch530/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch530/SSH.htm)

Then after the broadband modem-router there is an ethernet cable to my D-Link DL-524. That's probably very similar to the one you have, kasperbs, but a slightly different model, it is configured exactly the same way. [http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-524/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-524/SSH.htm) Thanks again for the great links, kasperbs. :)

kasperbs, might your father you need to configure some other piece of equipment that may be in between the D-Link and the internet?   Could that be any help for your problem?

Regards, Herman :)

---

### Post by kasperbs on 2007-09-21
Hi I just spoke to my dad, and actually he has a router in between the Dlink router and the internet. It's a Zyxell Prestige660R-61. We did the same portforwarding on that one the forward port 22, but it still doesn't work, and when he does the port scanning it seems like none of the ports we open from that router is open at all, only two ports are open and they have been open all the time. We have tried forwarding the apache ports 443 and 80 plus the port 22 on both router but the portscan doesn't show any of the as being open.

I guess the problem is the Zyxell router it won't forward the ports. From what I understand on your replies and thank you everyone the only problem can be the router. I will try and work on this and see if I can crack the zyxel code for forwarding ports.

---

### Post by kasperbs on 2007-09-22
Ok the problem is finally solved, it was a problem with the zyxell router. The problem was that the zyxell router had a client IP for the Dlink router which I had to forward

Thank you everyone for all your replies, very helpful indeed.

---

### Post by hyper_ch on 2007-09-24
good the problem is sovled :)  two routers in a (private) lan... haven't seen that before.

---

### Post by kasperbs on 2007-09-25
No me neither actually, but its because he's got broadband telephony and for that he need the router from the ISP to plug his phone into

---

