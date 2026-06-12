---
title: "Setting up Xbox Live w/Ubuntu"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by joeca0304 on 2006-03-04
ok, I have 2 Ethernet NIC cards in my machine.  In windows it was a Windows ICS setup.  So I have my one ethernet card running directly to my cable modem.  My other ethernet card is run to my xbox 360.  I need to setup a sharing of the internet connection between my 2 NIC cards.  I did a search and came across this
[http://ubuntuforums.org/showthread.php?t=91370]("http://ubuntuforums.org/showthread.php?t=91370")

First note that eth1 is my internet connection, and eth0 is my card running out to my xbox 360.

the first step sets up a static ip it looks for the card.  However when i type this in:

joe@ubuntu-linux-ws:~$ ifconfig eth0 192.168.0.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied

Thats what I get... What does this mean?  Do i just need to add a sudo before the cmd?  It says in the tutorial not to use sudo... so....how do i get a root terminal?

---

### Post by WackToMack on 2006-03-04
Try a sudo and see what happens...

Edit: Are you sure that 192.168.0.1 is your server ip address?

---

### Post by joeca0304 on 2006-03-04
well the 192.168.0.1 is just the private IP address I'm assigning to that ethernet card.  Anyway, I found out you can just do a

sudo bash 

at the CLI and it changes over to a root terminal basically

So anyway I set up my 360 ip and subnetmask and default gateway and dns server.  Everything works

Except my NAT is set to moderate, which is ok, except I may not get voice chat, or be able to join certain games.  I believe the problem now is opening some ports on the firewall to get my NAT setting to be "Open".

I'm gonna browse around and see if I can find what ports to open up, if anyone has experience with opening ports in linux and/or which 360 ones specifically let me know, thanks.

---

### Post by joeca0304 on 2006-03-05
Can anyone recommend a good firewall program to allow me to edit which ports I want to open?

Or

Anyone have any actual experience setting up Ubuntu to work with Xbove live, like I said I've got it to see my xbox 360.  The only problem is the 360 reports the nat as moderate.

---

### Post by woedend on 2006-03-06
i run xbox live through ubuntu.  you don't need a firewall, you'll see why if you go that way.  just bridge the connection and use dhcp on the xbox.

---

### Post by modest moose on 2007-03-01
i have done everything i can find on bridging with ubuntu (6.10) and none of it works. im trying to do ISP>UBUNTU>XBOX and have both the computer and xbox connect to the internet. but every tutorial i've seen doesnt help me. even this one. the computer always says eth2 (xbox) not ready. i have dhcp enabled on everything. i've tried bridge_utils, Firestarter, and some other stuff and none of it worked. i know its not the network card, because i've switched the cables in the computer and it still worked. and i know its not the xbox because it works going straight to the modem. so tell me whats wrong.

---

### Post by Nextgen.IT on 2007-03-08
Hi my name is davide i'm from italy and don't know very well english but i have connect ubuntu at xboxlive you can see how to there

[http://notiziexbox360ps3wiisfondivideogiochi.blogspot.com/2007/03/xboxlive-ubuntu-xbox360-how-to-sharing.html](http://notiziexbox360ps3wiisfondivideogiochi.blogspot.com/2007/03/xboxlive-ubuntu-xbox360-how-to-sharing.html)

The live work fine and i can play games on xboxlive whit ubuntu shared connection,download from marketplace ecc.

The only problem is XBOX360 in the TEST write to me the NAT is MODERATE (whit windows is OPEN)
Nat MODERATE is not good for SpechVoice in xboxlive,and low speed in-game live...

If anyone know how to resolve this,and can make a guide to "OPEN" this nat please help us.

---

### Post by Nextgen.IT on 2007-03-08
> **woedend said:**
> i run xbox live through ubuntu.  you don't need a firewall, you'll see why if you go that way.  just bridge the connection and use dhcp on the xbox.

Please can you explane to us how to do this point to point? whit the command line in termina etc. becouse i'm noob and the only way for connect 360 whit my ubuntu i know and work is firewall but after the nat is moderate...

how to "Just bridge the connetion" ?!?

---

