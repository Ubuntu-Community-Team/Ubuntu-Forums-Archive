---
title: "Simple Ubuntu/WinXP network"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2006-05-17
Hi,

Absolute first time with linux. I've been browsing the forums, but I'm afraid I don't understand much.

I'm trying to use my WinXP box as an Internet gateway (modem) for my Ubuntu box. I had previously used the machine on my school network using DHCP, so I know there's no hardware problem.  According to Win, the ethernet cable is unplugged, but I know Win uses this message for various different problems. I'm wondering if the cable itself is bad which I inherited from a friend; this is my first time using it. Unfortunatley, I don't have another computer to test it on or another cable. No LEDs are blinking.

Before I buy another cable, what are the other possibilities?

Also, the command "mii-tool eth0" outputs "no link" 

~ Ephilei

---

### Post by iand675@gmail.com on 2006-05-17
to interface with windows computers through linux, you need samba, which can be accessed using synaptic package manager.

[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

this appears to be a fairly good article on configuring it. good luck!

---

### Post by skinnygmg on 2006-05-17
are you using a router, or are you trying to network them adhoc?  what kind of internet connection does the xp box have

---

### Post by Ephilei on 2006-05-17
Thanks, I'll look at samba. I'm connecting directly from ethernet port to ethernet port. The XPs on dialup.

---

### Post by skinnygmg on 2006-05-18
i could be wrong, but i don't think you can do what you are trying to do.  if you want to share an internet connection, you need to set up a network.  you will need to connect both boxes to a router/hub/switch.  then you can dial up with the linux box, and use the connection from the win box.  you can "ad hoc" a wireless connection, but not a wired one.  someone please correct me if i'm wrong.

---

### Post by dmizer on 2006-05-18
if you have ethernet cable running directly from your windows box to your linux box, it has to be crossover cable in order for you to get a signal running between the two.

there's some good how to's on internet connection sharing for windows at [http://www.homenethelp.com/ics/index.asp](http://www.homenethelp.com/ics/index.asp) ... i used it a while back to set up a network at my parents place.

edit to change my answer because i completely overlooked the fact that the physical connections were already mentioned.

---

### Post by Ephilei on 2006-05-18
Wow, can someone tell which binary package of samba to install? 
[http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/]("http://us1.samba.org/samba/ftp/Binary_Packages/Debian/samba/")

---

### Post by zerhacke on 2006-05-18
You don't need Samba to share the internet connection.  Samba is for sharing files and printers between computers, not the internet connection.

You said Windows is getting the internet connection and is sharing it with the Ubuntu machine.  You also know the configuration with Ubuntu is fine, as it works with your school LAN.

Check the cable.  Take it to any mom and pop computer shop and have them put it in a cable tester.  If it comes back fine, check the settings on your XP setup.

On XP, you have to share the NIC that gets the connection, not the NIC you want to give the connection.

---

### Post by dmizer on 2006-05-18
zerhacke is correct, you don't need samba to share internet connection.  you only need samba to share files.

but since you do have a direct ethernet to ethernet connection you will need a crossover cable.  i suspect this is why you are not getting a connection.

---

### Post by skinnygmg on 2006-05-18
Do it yourself Ethernet Crossover Cable
[http://www.makeitsimple.com/how-to/dyi_crossover.htm](http://www.makeitsimple.com/how-to/dyi_crossover.htm)

7 ft Cat5E Crossover Network Patch Cable - $1.39
[http://www.microbarn.com/CrossoverCable_NCB-C7--51-164-100131.html?source=gadwords](http://www.microbarn.com/CrossoverCable_NCB-C7--51-164-100131.html?source=gadwords)

Ethernet Crossover Adapter
[http://www.thinkgeek.com/gadgets/tools/7470/](http://www.thinkgeek.com/gadgets/tools/7470/)

---

### Post by Tortanick on 2006-05-18
What did you do on the windows box to make it share the connection? 

on windows open command prompt and type 'ipconfig' it should give you two diffrent IP's one being a network IP and the other being a local are network?

You'll probobly need to give the ubuntu box an IP adress manually. 

I'm not sure but this setup is worth a try.

System>administration>networks.

open ethernet propoties.

Set it to static. 

IP address: ***_***_***_%%% where *** is the same as the windows box's local area network IP and %%% is diffrent.
subnet mask: 255.255.255.0
Gateway address: the windows box's local area network ip.

Now for DNS:

If you know your IPs DNS server address use that, if not you can use an OpenNIC one. 

[http://www.opennic.unrated.net/public_servers.html](http://www.opennic.unrated.net/public_servers.html)

make sure you ping them to find out if there up. Sadly OpenNIC seems to be stable yet half dead.

---

### Post by dmizer on 2006-05-18
[QUOTE=Tortanick]on windows open command prompt and type 'ipconfig' it should give you two diffrent IP's one being a network IP and the other being a local are network?

You'll probobly need to give the ubuntu box an IP adress manually. [/QUOTE]
no ... according to what he's written, there is no physical link.  both ubuntu and the windows machine are showing that no cable is connected.
[QUOTE=Ephilei]According to Win, the ethernet cable is unplugged ... snip ... Also, the command "mii-tool eth0" outputs "no link" [/QUOTE]
as of right now, this is only a physical connection issue, not a configuration issue.

---

### Post by Ephilei on 2006-05-19
Wow, thanks for all the help!

It never occurred to me that the cable might be a direct connector - which it was. I got a crossover and things are starting to work. I'll post when I hit another (probably in the next hour).

---

### Post by Ephilei on 2006-05-19
Thanks - everything's working now!

---

