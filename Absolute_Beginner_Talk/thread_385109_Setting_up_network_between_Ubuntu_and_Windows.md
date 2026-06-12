---
title: "Setting up network between Ubuntu and Windows"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by PhosPhoton on 2007-03-15
I'd like some help setting up a connection between my Ubuntu computer and my Windows computer. If I go to Places > Network Servers > Windows Network, nothing appears there. This is a real problem because I'm tired of having to go back and forth between computers with my flash disk if I need to download something. So far I've almost knocked the piano over!

---

### Post by lamalex on 2007-03-15
you need to install samba. here is a good howto
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+peer+howto)

---

### Post by PhosPhoton on 2007-03-15
One small problem, though. Since my Ubuntu computer is not connected to the internet I can't do a direct installation. Is it possible to get a .deb package for samba?

---

### Post by chewearn on 2007-03-15
I think samba is already installed by default; at least it does on my machine.  I am able to see my SMB NAS.
Maybe you have a firewall in your Windows machine blocking the Windows Network. Or your Windows is not properly configured to a home network configuration?

---

### Post by lamalex on 2007-03-15
Phos, can you give a layout of your network? Is your windows computer connected? are you on broadband or dialup? How is your windows pc connected to the network? How is your ubuntu pc connected?

---

### Post by PhosPhoton on 2007-03-15
I have a Windows computer which is connected to the ADSL modem via USB and thus is the internet server. The computer is then connected to the router via ethernet. I have another Windows computer connected to the router via ethernet in the same way. The Ubuntu computer is connected to the router as well. The network between the two Windows computers is fine. However, Ubuntu doesn't see either of them. Firewall is off.

---

### Post by bogolisk on 2007-03-15
> **AstalaVista said:**
> I think samba is already installed by default; at least it does on my machine.  I am able to see my SMB NAS.
Maybe you have a firewall in your Windows machine blocking the Windows Network. Or your Windows is not properly configured to a home network configuration?

I don't think samba server is installed by defaul, only the smb client. Without samba server, you can access smb shares but you cannot serve shares.

---

### Post by lamalex on 2007-03-15
.. why can't the ubuntu computer get to the internet? Is your server computer not passing traffic? Can your other windows computer connect to the internet and just not ubuntu one? was this planned this way? my suggestion would be to plug them all into your router and set your clients default gateway to the server gateway so it is filtering all trafic (assuming you're using it for proxy or something of that sort?).

---

### Post by Malac on 2007-03-15
```
sudo gedit /etc/samba/smb.conf
```
And check that the network name is set the same as the Windows Computer(s). This is usually MSHOME if you left the windows default one.
Also are you issuing I.P's for the computers via DHCP or are they fixed?

---

### Post by PhosPhoton on 2007-03-15
All the windows computers (and laptops connected via wi-fi) can connect to the internet. But I am having trouble connecting the Ubuntu computer to the internet.

I don't know how to change the network settings in Ubuntu

---

### Post by lamalex on 2007-03-15
it sounds like the problem is not with samba but with your nic card. can you ping the router?

---

### Post by PhosPhoton on 2007-03-15
No it can't ping the router. It says network is unreachable.

---

### Post by Malac on 2007-03-15
post the output of ifconfig for the Ubuntu machine and ipconfig on one of the Windows machines.

---

### Post by lamalex on 2007-03-15
Also what type of nic card is it? If you don't know, post the output of ```
lspci
```

---

### Post by PhosPhoton on 2007-03-16
I have a very sad feeling the network card is broken:( Because if I boot up the Ubuntu computer in Windows 98, it cannot see the other computers on the network. However, I can't seem to get Windows to work after I installed Ubuntu, so I can't see what Windows said about the Network card. Might have to buy a new card.

---

### Post by Malac on 2007-03-16
> **PhosPhoton said:**
> I have a very sad feeling the network card is broken:( Because if I boot up the Ubuntu computer in Windows 98, it cannot see the other computers on the network. However, I can't seem to get Windows to work after I installed Ubuntu, so I can't see what Windows said about the Network card. Might have to buy a new card.
You could try swapping the card from one of the Windows machines first.
lamalex suggestion of lspci output should tell you if the card is broken as there will be no output for it.

---

### Post by cloud1494 on 2007-03-16
It might also be a problem with your ethernet cable, it'll be easier to switch that cable with a known-good one before you switch cards.

---

### Post by PhosPhoton on 2007-03-16
The Cable is fine. I swapped cables with one of my Windows computers. No luck. I'm going to try a working card as soon as I can get another one.

---

### Post by lamalex on 2007-03-16
why don't you just power off one of your windows boxes, pull its nic, pop it in, if it works, you found your problem. pop it back into the windows machine, it will never know.

---

### Post by PhosPhoton on 2007-03-18
It's not that easy. My Windows comps both have onboard cards :( . I'll get one tomorrow, hopefully, if my dad doesn't forget again.

---

