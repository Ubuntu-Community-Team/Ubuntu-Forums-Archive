---
title: "Opening port 80 with Firestarter for Apache"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-22
How is this done?  I browsed around the Firestarter program but I really dont want to mess it up.  I just want to open port 80 for Apache.

---

### Post by wieman01 on 2006-09-22
> **YeahBuntu said:**
> How is this done?  I browsed around the Firestarter program but I really dont want to mess it up.  I just want to open port 80 for Apache.
Have you got the GUI? If yes, this is how you open up port 80...

1. Open terminal.
2. Type 'sudo firestarter'.
3. Go to 'Policy' tab.
4. Choose 'Inbound traffic' and press "Add rule".
5. Now select 'Name' = HTTP and 'Source' = Anyone.
6. Press 'Add'.
7. Do the same for 'Outbound traffic'.
8. Last but no least press 'Apply Policy'.

That's it for port 80. See snapshots.

---

### Post by YeahBuntu on 2006-09-23
Thank you very much

---

### Post by wieman01 on 2006-09-23
[QUOTE=YeahBuntu]Thank you so much for helping me sorry it took me so long to respond I was at work.  I do have the GUI  (right now anyway)

on a side note can you tell me what all those samba things in the log are for .. what should I do with them?

Thank you soo osoooo much for answering me about how to open the ports.. you can respond to me in [this thread]("http://ubuntuforums.org/showthread.php?t=263162").[/QUOTE]
You're most welcome.

I am afraid I cannot follow your question... What "Samba" things are you referring to? Are there entries in you log file ("Events" tab) stating "samba"? 

If so then somebody has been trying to access your computer via these ports or has done a port scan. If this is a local network IP address than it probably one of you own computers, if it's a public IP address (Internet), then there is a chance that somebody from outside has done a port scan on you.

Not sure where you're located but this happens frequently to me while I am traveling in China. Don't worry about it, that's why you have a firewall! :-) While this is a hassle, it's not critical.

---

### Post by YeahBuntu on 2006-09-23
These are the logs I was talking about .. sorry I thought I put them in there 

```
Time:Sep 20 22:56:08 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.11 Destination:192.168.2.255 Length:242 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 22:56:14 Direction: Unknown In:eth0 Out: Port:137 Source:192.168.2.38 Destination:192.168.2.255 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 22:59:49 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.38 Destination:192.168.2.255 Length:243 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:02:44 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.11 Destination:192.168.2.255 Length:233 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:08:14 Direction: Unknown In:eth0 Out: Port:137 Source:192.168.2.38 Destination:192.168.2.255 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:11:51 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.38 Destination:192.168.2.255 Length:243 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:17:44 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.11 Destination:192.168.2.255 Length:233 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:20:14 Direction: Unknown In:eth0 Out: Port:137 Source:192.168.2.38 Destination:192.168.2.255 Length:78 TOS:0x00 Protocol:UDP Service:Samba (SMB)
Time:Sep 20 23:23:53 Direction: Unknown In:eth0 Out: Port:138 Source:192.168.2.38 Destination:192.168.2.255 Length:243 TOS:0x00 Protocol:UDP Service:Samba (SMB)
```

Hmm I am behind a router so these would be the other two computers on my network trying to break into my linux box?  Does that mean I have nasty software on my other two pc's?

Hope your still here and can answer.

---

### Post by wieman01 on 2006-09-23
Oh yes, there are two computers in your local network that are trying to connect to the one with the firewall through ports **138** and **137**:
> 192.168.2.38
192.168.2.11
I reckon your own IP address is:
> 192.168.2.255
Are you **"sharing folders"** with other computers? If so this is by no means unusual. **Samba** is a common file server & client program that is used for file sharing, in particular between Windows computers & Linux machines.

So I take it that you network's computers are trying to access your through these ports. That's all. If you open up these ports and have Samba installed on your own machine, you can share files if you want.

---

### Post by YeahBuntu on 2006-09-23
> **wieman01 said:**
> Oh yes, there are two computers in your local network that are trying to connect to the one with the firewall through ports **138** and **137**:

I reckon your own IP address is:

Are you **"sharing folders"** with other computers? If so this is by no means unusual. **Samba** is a common file server & client program that is used for file sharing, in particular between Windows computers & Linux machines.

So I take it that you network's computers are trying to access your through these ports. That's all. If you open up these ports and have Samba installed on your own machine, you can share files if you want.

Oh... I really dont want to share files yet.. I just use my thumbdrive to transfer things if I really need it.  I didnt think my computers were actually sharing files .. I currently dont share folders between these other two computers.

I think 192.168.2.255 is the ip address of my router... not sure.. I'd have to log into the router and I cant seem to find the password for it .. which is another problem i'll have to deal with when im ready to put this sucker live ... but im gettin closer with your help thank you very much sir

---

### Post by wieman01 on 2006-09-23
You're welcome. Please don't call me "sir". We're all buddies in here. :-) 

And let us know how it goes.

---

