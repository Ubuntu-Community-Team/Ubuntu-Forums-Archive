---
title: "Seting up an Ubuntu box+WinXP box using crossover (twisted pair) cable"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by Spoo on 2005-12-20
Hello ALL of you wonderfull guys who made  possible for me to set up an actually runing a Linux machine for the first time. Thank you.

This is my first post EVER on a forum (any forum, any time) so... please forgive any mistake or any sign of more "newbieness" than you can stand ;-). Also English is not my natural language, so.... 


My set:
- I have a WinXP machine and a spare K6 AMD 400Mz, 10Gb HD box.
- I successfully instaled (actually I am using it at this moment) Ubuntu on the AMD
- I am connect to the Internet using a CABLE Thomson modem linked to my Ubuntu.
- I have an HP printer hooked to the windows box.
- There is NO Hub, switch or router and there is NO MONEY to buy any of these at the moment.
- The Ubuntu box has two interface cards, one (eth1) linked to the modem and the other (eth0) I was thinking  to link it to the ethernet card on the windows machine through crossover cable (I have one already).

My needs:
- I want the windows box runing for the wife to use, she needs the printer and the Internet but she knows even less than me about computers and even less (if possible) of Linux, so any solution of HER running Linux is out of consideration.
- I need to share files to and from BOTH boxes ( I know I must have partition types recognizable on both machines) and I need to use the printer from the Ubuntu;
- I can have both machines ON all of the time and I was thinking of keeping the modem hooked directly to the ubuntu.

Aditional problem(s):
- I have only one display monitor (I know I will have to buy at least a kind of a display switch to share the monitor) but, to compensate, I have two wireless optical keyboard+mouse sets;
- I want to keep the Internet coming through the Ubuntu box;
- I want the Ubuntu as a firewall for both machines


In a word (yeah, right!) 

- What do I have to install either on the Ubuntu and the Windows boxes;
- Where do I find detailed instructions on how to set both machines for the network;
- What and How to configure whatever you may think necessary.

If this is too much ... at least please point me to some links.

THANK YOU In advance.

---

### Post by Spoo on 2005-12-20
BUMP

(sorry guys but I do really need urgent help!)

---

### Post by Gandalf on 2005-12-20
Hello

One question, can you afford to get a junk PC? i mean, 50$ maybe much less old PC? if yes you can build your own powerfull router using ipcop ( [http://www.ipcop.org](http://www.ipcop.org) ) 

about files sharing, you need samba, check [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Spoo on 2005-12-20
@ Gandalf

[QUOTE=Spoo]
- ...there is NO MONEY to buy ... at the moment.
[/QUOTE]

Thank You for the answer. Really, at this moment, there is no money to spend on computer stuff. I will have to do with what I have at the moment, besides that screen display thing.

I have a windows box all setup and running for a long time, I steped into Ubuntu and I thought to give it a try. Either it is possible with what I have and what I need... or not. that's the question. And the incoming question will be: Am I capable of doing it or not.


Anyways... thank you

---

### Post by Gandalf on 2005-12-20
well you can use your linux as a router anyway, i'm not sure what you have to do in order to get a bridge between two netword cards as i dont have knowledges on things that i haven't done yet, but am sure googling a bit can help you,

as for file/printer sharing, you are looking for Samba server which can share files and printer just like u do on windows using windows share...

---

### Post by cwaldbieser on 2005-12-20
[QUOTE=Spoo]Hello ALL of you wonderfull guys who made  possible for me to set up an actually runing a Linux machine for the first time. Thank you.

This is my first post EVER on a forum (any forum, any time) so... please forgive any mistake or any sign of more "newbieness" than you can stand ;-). Also English is not my natural language, so.... 


My set:
- I have a WinXP machine and a spare K6 AMD 400Mz, 10Gb HD box.
- I successfully instaled (actually I am using it at this moment) Ubuntu on the AMD
- I am connect to the Internet using a CABLE Thomson modem linked to my Ubuntu.
- I have an HP printer hooked to the windows box.
- There is NO Hub, switch or router and there is NO MONEY to buy any of these at the moment.
- The Ubuntu box has two interface cards, one (eth1) linked to the modem and the other (eth0) I was thinking  to link it to the ethernet card on the windows machine through crossover cable (I have one already).

My needs:
- I want the windows box runing for the wife to use, she needs the printer and the Internet but she knows even less than me about computers and even less (if possible) of Linux, so any solution of HER running Linux is out of consideration.
- I need to share files to and from BOTH boxes ( I know I must have partition types recognizable on both machines) and I need to use the printer from the Ubuntu;
- I can have both machines ON all of the time and I was thinking of keeping the modem hooked directly to the ubuntu.

Aditional problem(s):
- I have only one display monitor (I know I will have to buy at least a kind of a display switch to share the monitor) but, to compensate, I have two wireless optical keyboard+mouse sets;
- I want to keep the Internet coming through the Ubuntu box;
- I want the Ubuntu as a firewall for both machines


In a word (yeah, right!) 

- What do I have to install either on the Ubuntu and the Windows boxes;
- Where do I find detailed instructions on how to set both machines for the network;
- What and How to configure whatever you may think necessary.

If this is too much ... at least please point me to some links.

THANK YOU In advance.[/QUOTE]

Use the Ubuntu machine as the router:
1) Get the firestarter package with apt-get or synaptic.  If you are unfamiliar with how to get packages for Ubuntu, it is really easy.  Here is a link:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")
2) In the firestarter GUI, Edit -> Preferences -> Firewall -> Network Settings.  This form has everything you need to set up "Internet Connection Sharing".  You choose the ethernet cards and tick the checkbox.
3) On the Windows machine, you must set it up so that the Ubuntu box is your default gateway.  I don't have Windows in front of me, so I can't tell you where this is exactly, but it is under Network Settings and TCP/IP somewhere...

That should more or less establish connectivity and let the Windows machine surf the web.  I am guessing your Internet card is configured via DHCP.  It is probably easiest if you configure the other network card with a static IP address like 192.168.0.7, or something similar.

---

