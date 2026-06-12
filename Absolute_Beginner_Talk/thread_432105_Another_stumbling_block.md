---
title: "Another stumbling block"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by leecou on 2007-05-03
Hey everyone,

I've been trying to get an old Compaq to run a media player to play .avi files.

As the link [**[B]here** [/B]]("http://ubuntuforums.org/showthread.php?t=398158")shows I've been having real problems not being connected to the internet on the Ubuntu machine to install the correct packages etc

A fella I work with suggested creating a network connection with my XP machine as the master and the Ubuntu machine as the slave.

I now have an ethernet switch/hub bridging the two machines and I've followed all of the instructions on the forums to create the network share (on both the XP and Ubuntu boxes). Ubuntu has a static IP address 1 higher than the XP machine, the subnet is the same and the gatewayaddress is the same.

But I still con't get on teh internet on teh Ubuntu machine.

Anyone got any ideas

Cheers

L

---

### Post by matburton on 2007-05-03
So your trying to set up XP to share its net connection across the network you've just made correct?
I assume you have some kind of net connection that your ubuntu machine cant use.
If so I think there's a wizard to set up a home network in XP.

Then I'd personally use network manager (are you using Feisty?) as XP will then act as a DHCP server on the network and give you a IP address its self. So it should just then be a case of one click in network manager.

Of course the difficult part is getting XP to actually share its net connection. I've had fun and games with this in the past ;)

Have to admit that Ive never heard the terms master or slave before in networking :S

---

### Post by leecou on 2007-05-04
Yeah,

I've got an internet conection on the Xp machine, but nothing on the ubuntu box. It's that internet connection I want to share (so I can get mplayer to work!)

I have an ethernet switch linking the two boxes.

I've set up a home network on the XP box, it's getting Ubuntu to recoginse the network/ethernet switch/internet connection.

XP I'm comfortable with. Ubuntu configuration and basically getting it to work is the problem. At this point learning Mandarin by living in russia would be easier!!!

L

---

### Post by matburton on 2007-05-05
Hmmm,

Have you another computer to test this internet share with?
Are you using Edgy? Feisty?
If Edgy do you have network manager installed?

There should be NO setup on the ubuntu end! All the network sharing should be on XPs side.
Make sure you haven't changed any IP addressed and ubuntu isn't trying to use a static address!

XP, when set up correctly, should simply pass an IP to ubuntu through its DHCP server.
Hence if ubuntu can't access the net, or can't use the network, then it's highly likely that XP is the cause here.

Hope that helps!

---

### Post by leecou on 2007-05-05
I was running Dapper Drake.

I'm going to install Fiesty and report back

L

---

### Post by leecou on 2007-05-05
Right installed Feisty and am having the same problem.

I've run the Windows network wizardand followed all of their troubleshooting process without results.

Getting very frustrated with Ubuntu now. If I was trying to do this with 2 xp machines it would have been resolved on the day I started the exercise.

What can I possibly be missing on the Ubuntu box to screw up the process.? In the "network setting" box, the DNS tab shows the IP address of the XP box as the DNS server (which is right?) and the name of the MS configured network as the search domain

<Sound of hair tearing>

L

---

### Post by matburton on 2007-05-05
If ubuntu has a DNS and default route set to XPs IP and has its own IP assigned through DHCP then that's right!

I'm 99% sure here that it's XPs fault, I've had loads of trouble with this in the past XP to XP!

---

