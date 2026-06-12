---
title: "Bought a new computer."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by facthemighty on 2007-06-16
Delll dual core processor, 80 gb of hard drive. DVD-RW.

It doesn't come with modem. :( I'm trying like heck to, but I have no idea how to network computes. On my older Dell and the newer one there's a symbol that has a lines attached to a box. This is the newtwork port? Do I plug a phone line between the two for direct connection? Or is a special plug needed? 

I"m totally clueless.

---

### Post by skymera on 2007-06-16
so u want to connect to internet?
or computers?

---

### Post by facthemighty on 2007-06-16
I dual booted the dual core with Ubuntu and XP. The old Dell has XP. I want to network the two together (preferably wihile the dc is running Ubuntu) so that the Ubuntu computer can remotely connect to the internet. And share files. And share the printer. The older Dell has dialup.

---

### Post by skymera on 2007-06-16
so... dual boot...
u got 1 computer and u want to share files between ubuntu and XP?

sorry if im wrong

---

### Post by facthemighty on 2007-06-16
I have two computers.

Dell 4600 with XP.

Dell dual core with XP and Ubuntu.

---

### Post by JacobRogers on 2007-06-16
It's going to be extremely hard and impractical to have two computers share a dial up connection while one of them is running of a LIVE CD.  Sorry but since you're an absolute beginner like you said in your first post, then this project might be beyond you.

---

### Post by facthemighty on 2007-06-16
Okay, but how do I network the computers together to do other stuff?

---

### Post by dwhitney67 on 2007-06-16
1) Have you installed Ubuntu onto your new PC?

2) Does your old PC have a NIC (network interface card)? Look to see if it has a port that is wider than the typical telephone jack.  If it does, and presumably your new system does too, then you can network them together.

3) Do you have a router (i.e. Linksys)?

If yes, then procure yourself two CAT-5 cables and connect both systems to the router.  Voila, you are networked.

If not, then procure a **straight-thru** CAT-5 cable (these can be bought at major electronics stores).  Do not confuse this type of cable with the typical cross-over type.  Once you have the cable, you can connect each system to directly to each other (presuming of course the systems have a CAT-5 ethernet port).  Ensure both systems have a fixed IP address.  Ok, I know, the previous statement is a little advanced.  Just so you know, it is much easier to network two systems if you answered "yes" to both questions 2 and 3.

Anyhow, if you have managed to network your two systems, and the old PC is doing the dial-up connection to the internet, I recall there is a way to share your connection, but since it under windows, I cannot remember how to do this.

As for dial-up under Ubuntu, I'm sure it is doable, but I am not the one to consult on this.  I personally have always used either DSL or Cable-Modem service.

---

### Post by facthemighty on 2007-06-17
Ooops. My post disappeared. 

4600 has:
Intel Pro 100 VE Network Controller

The newer Dell has:
INtel 82562V 10/100 Network Controller

Are the propriety? Are they compatible with Cat-5 cables. I know one time I bought a couple Cat-5s for work and it cost me $50.

---

### Post by candtalan on 2007-06-17
Both machines have network interface card (NIC) functions, so ther will be an ethernet cable connector at the back of each. It is RJ45 style. An image of the cable end example is here
[http://static.flickr.com/90/272877017_3959ef24e8_o.jpg](http://static.flickr.com/90/272877017_3959ef24e8_o.jpg)

If you connect the two computers through a router box the cable to each is a standard straight through cable (a patch cable).

If you do not use a router box and use a single cable to go between the two then I believe the cable has to be a 'crossover' cable (direct connection)
see
[http://compnetworking.about.com/od/homenetworking/a/connecttwocomp.htm](http://compnetworking.about.com/od/homenetworking/a/connecttwocomp.htm)

hth

---

### Post by Dedoimedo on 2007-06-17
Hello,

See if this helps you:
[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

Dedoimedo

---

### Post by facthemighty on 2007-06-18
Okay, the dude at Best Buy said "a network adaptor is a network adaptor is a network adaptor" and assured me that I wouldn't fry my computer by connecting an older network card to a wired router. SO I networked my computers together. 

The dual core while running XP will open everything in the older Dell's Shared Folder. It will even follow links to various other places on the computer. 

The dual core while running Ubuntu will open the shared folder but refuses to follow Windows links. :( So I gotta move files around while both computers are running XP. So now my network consists of D-Link wired router, three cat-6 cables, an Xbox, and two computers. Next month I might just get DSL.

---

### Post by facthemighty on 2007-07-10
Okay, finally got Verizon DSL. How do I set up the internet connection on the newer Dell (the one with Ubuntu and XP)?\


NM! I got home and after dickering with the setup files with the D-Link router, I managed to get both Ubuntu and XP to hook up to the network AND the internet on my Dual core. :D FINALLY!!!!!! :popcorn:

---

### Post by facthemighty on 2007-07-15
Darn. Never mind. I just turned on both computers. The Dual Core is recognized by my Windows network software as being onllne. But it doesn't let it get online when in Ubuntu.

I'm using Network Magic for XP. Here's a basic run down of the map it shows:
Internet
DNS  ***.***.0.1
IP Address: ***.***.1.47


To the right of that is the Router.
IP ***.***.0.1

Below that is the 4600
IP ***.***.0.100

To the right of that is the Dual Core'
IP ***.***.0.3

:confused:

I omitted the first six digits because they are constant throughout. I haven't changed them in the setup. 

I have the computers networked together though, so even though one can't get online, the other can & is able to send files to the other.

I've got Verizon DSL now...

---

### Post by Vague on 2007-07-15
> **dwhitney67 said:**
> 1)If not, then procure a **straight-thru** CAT-5 cable (these can be bought at major electronics stores).  Do not confuse this type of cable with the typical cross-over type.

It's not a big deal, but you have those backwards.  The standard type is straight through.  To connect two computers directly, you need to use a crossover cable.

Edit: Didn't even realize that post was 4 weeks old.  Oh well.

---

