---
title: "HELP!! I can't figure out how to connect to SBC DSL!"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Linuxnewbie2006 on 2006-04-14
I'm just starting out on Ubuntu Linux. I have a DSL modem hooked up to my other Windows XP computer but I don't know how to set up my Ubuntu compter to run off the modem. Can anyone help me?
Thanks 
R

---

### Post by aysiu on 2006-04-14
[QUOTE=Linuxnewbie2006]I'm just starting out on Ubuntu Linux. I have a DSL modem hooked up to my other Windows XP computer but I don't know how to set up my Ubuntu compter to run off the modem. Can anyone help me?
Thanks 
R[/QUOTE] It sounds as if you need a router. That's the only way I know of to get one connection on multiple computers.

I use SBC DSL as well, by the way... with a router.

---

### Post by rubrboots on 2006-04-14
This is how I have mine set up. My XP box is connected the internet. Then I have a crossover network cable running from the XP box to the Ubunbu box supplying internet to it.

You will need to have a free network card in the XP box, and a "crossover" (very important) network cable. If you dont already have at least one of these you are probably better off buying a cheap router than spending money on buying a NIC(Network Card) and a crossover cable. A crossover cable should be about $10.

If you go the crossover route follow these instructions.

1- Temporarily turn of any firewalls you may have.
2- Connect the crossover cable from the free XP NIC to the NIC in the Ubuntu box.
3- In XP go to Network connections, right click the connection that supplies the internet to the XP box, Properties---->Advanced Tab , then check the box that allows other users to use this comps internet connection.
4-The make sure your NIC is active in Ubuntu. Now you should have internet.

If you dont have internet on Ubuntu, then go to the NIC settings and make sure you have DHCP enabled. I dont know why but I could not this setup to work with a static IP set on the Ubuntu box.

Good luck

---

### Post by Linuxnewbie2006 on 2006-04-14
I figured out that Umbuntu does not run off PPPoE and has to be "filtered" through a router to get the required DHCP configuration. Thanks for your help. After adding a router I'm enjoying the internet using Umbuntu.

---

### Post by Mustard on 2006-04-14
[QUOTE=Linuxnewbie2006]I figured out that Umbuntu does not run off PPPoE and has to be "filtered" through a router to get the required DHCP configuration. Thanks for your help. After adding a router I'm enjoying the internet using Umbuntu.[/QUOTE]

Hehehe..'Umbuntu'.

That's got a cute sound to it. :D  I think that should be a candidate for the Ubuntu equivalent of the AnonymOS distro. :)

Glad to see you got it working, btw.

---

