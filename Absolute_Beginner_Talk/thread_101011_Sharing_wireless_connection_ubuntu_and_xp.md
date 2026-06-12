---
title: "Sharing wireless connection ubuntu and xp"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by chess_at on 2005-12-08
Sorry for reposting it, as no one had replied thought its probably the heading.. your help is appreciated.

Problem:
I got an ubuntu computer connecting to a windows xp machine through cable lan. The xp machine is connected to the rest of the network (including internet) through a wireless connection.

Question:
How can share the wireless connection with the linux desktop so the linux will be part of the network as well?

I could make the linux with the wireless and windows through cable to linux if thats easier to do!

Appreciate your help guys. I have no idea where to even start from.

Thanks.

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=chess_at]Sorry for reposting it, as no one had replied thought its probably the heading.. your help is appreciated.

Problem:
I got an ubuntu computer connecting to a windows xp machine through cable lan. The xp machine is connected to the rest of the network (including internet) through a wireless connection.

Question:
How can share the wireless connection with the linux desktop so the linux will be part of the network as well?

I could make the linux with the wireless and windows through cable to linux if thats easier to do!

Appreciate your help guys. I have no idea where to even start from.

Thanks.[/QUOTE]

Is the Ubuntu machine plagged directly into the XP machine with a crossover cable, or is it plugged into a router, or something else?

---

### Post by tokyovigilante on 2005-12-08
Sharing networks through computers (which would involve bridging connections on XP) rarely works well, a better solution would be to bypass the XP machine and plug your Ubuntu machine's cable into a router or hub directly. 

If this isn't an option due to the physical layout of your network, then try the following: (Im assuming your XP machine has two networks plugged in, one wireless and one wired, and that there's a DHCP server elsewhere on your network)

1. Open Network Connections in Control Panel.

2. Click on the wireless connection, hold down Ctrl, and click on the wired connection (the one you have your Ubuntu machine plugged into) so that both are selected.

3. Right click and select "Bridge Connections."

4. A network bridge will be created, which hopefully will achieve what you're after.

---

### Post by adduds on 2005-12-08
Could you just buy a wireless card for your ubuntu machine to also receive the signal?

---

### Post by chess_at on 2005-12-08
thanks very much guys i'll give the bridge connection a shot.. 

so it was actually the heading :)

---

### Post by chess_at on 2005-12-08
[QUOTE=cwaldbieser]Is the Ubuntu machine plagged directly into the XP machine with a crossover cable, or is it plugged into a router, or something else?[/QUOTE]
Yea it is plugged straight to the xp machine using crossover.. thanks.

---

### Post by tokyovigilante on 2005-12-08
[QUOTE=chess_at]Yea it is plugged straight to the xp machine using crossover.. thanks.[/QUOTE]
Do you not have access to a router to plug a cable into?

---

### Post by tokyovigilante on 2005-12-08
> I could make the linux with the wireless and windows through cable to linux if thats easier to do!

More like impossible with Windows and simple with Linux ;) You could set it up that way using the Firestarter firewall, but it would be much easier to just have both computers plugged directly into the network.

What does the rest of the network look like? Are you just working with your own home network? Or are you using a public wireless network?

---

### Post by chess_at on 2005-12-15
the bridge thing on xp worked, i couldn't belive it too... but then come to think abt it i might buy a wireless card for the ubuntu as well. 

anyway thanks guys for your help...

---

### Post by DouglasAWh on 2007-12-25
I know this is a long forgotten post, but how long is this bridging thing supposed to take?  I've been waiting on XP forever.  Does anybody know if having another program like a Linksys utility control the wireless on XP cause bridging not to work?  I just need the bridging in order to download the downgrade packages for whatever I updated that broke my wireless!  I do NOT have physical access to this router.  Thanks!

---

