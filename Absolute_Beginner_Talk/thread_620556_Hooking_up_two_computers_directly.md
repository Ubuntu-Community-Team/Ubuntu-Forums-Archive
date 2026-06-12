---
title: "Hooking up two computers directly"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Joushlol on 2007-11-22
How would I go about configure/establish a direct link via ethernet between my two machines? one is running feisty fawn and the other gusty.

---

### Post by Dr Small on 2007-11-22
You have the wrong terminology on the title.
You would need a crossover ethernet cable for it to work.

---

### Post by Joushlol on 2007-11-22
assuming i have a crossover ethernet, is there anything special i would need to do in order to establish a direct connection.

---

### Post by Dr Small on 2007-11-22
I don't know, as I have never had a crossover cable to test it myself, but it shouldn't be too hard to figure out. Probably need to select eth0 on both of them, though.

---

### Post by bluepowder7 on 2007-11-22
i think you'd need to set static IP addresses, no?  i seem to recall running into that hurdle when i was working with crossover cables at work one time (laptop to optical switch).

---

### Post by Joushlol on 2007-11-22
and what? just set the IP address to 0 or something. srsly i need some more details, i am so flunking computers in general right now because I'm in the process of switching from windows to linux and i'm like a retard at the moment.

---

### Post by bluepowder7 on 2007-11-22
haha!  no worries, i'm no genius by any stretch either.

i THINK i had to set up a static IP on the laptop to something like 192.168.1.100 and the "other piece of equipment" to 192.168.1.101   you might be able to use other addresses (the first three sets of numbers), as long as the only difference between the two computers is that last number (.100 and .101 in my example)

i think they also had to have the same subnet masks (like 255.255.255.0).  i'm not sure if i needed to use a cross-over cable or a straight cable, but i had both at my disposal and got the two pieces of gear to talk to each other.

lemme see if i can google some stuff that confirms this (or gives more accurate guidance)


EDIT - here ya go.  found this tutorial.  seems that what i was doing and remembering was mostly right.

[http://www.wikihow.com/Connect-Two-Computers](http://www.wikihow.com/Connect-Two-Computers)

---

### Post by L Campbell on 2007-11-22
> **Joushlol said:**
> How would I go about configure/establish a direct link via ethernet between my two machines? one is running feisty fawn and the other gusty.

I'm kind of a dummy, so I may have understood your question but I have 4 computers hooked up to the same DSL modem internet connection.

Each has its own crossover cable from the modem.

That was ALL there was to it.

---

### Post by ByteJuggler on 2007-11-22
> **Joushlol said:**
> How would I go about configure/establish a direct link via ethernet between my two machines? one is running feisty fawn and the other gusty.

The easiest is if you have a hub to connect them both to, that can serve IP addresses to both machines via DHCP.  Then you also don't need a crossover cable, but only normal patch cables. Simply connect both machines to the hub.

Alternatively, as has been mentioned, get a crossover cable and cut out the hub, but then you have to take care of assignning static ip address yourself.  You can do that in the networking dialog.  Let us know if you need more information on that.

Then to make the machines talk to each other, find their ip addresses using "ifconfig" and then install secure shell and tools on both machines to allow them to easily connect to each other.  The Gnome file manager can also use ssh to connect/make a mapping to another server so you can use it to map to a remote folder using SSH, you don't have to use command line tools unless you want to.

---

### Post by ByteJuggler on 2007-11-22
> **L Campbell said:**
> Each has its own crossover cable from the modem.


Umm, that would presuambly be patch cables and not crossover cables (there is a difference.)  I presume by "modem" you actually mean modem-router, as in one of these cable modems with 4 ethernet ports that you can connect several computers to (so hence includes a hub/router in the modem.)

---

### Post by brn on 2007-11-22
I connected my desk and laptop machines through the DSL modem/router like this:
1.  From a command line on the target machine, run ifconfig to identify it's inet address.
2.  **Applications > Internet > Terminal Server Clien**t (if not there, install from repository)
3.  Complete the form with  the inet address and user name/password of  the target computer, and VNC as the protocol.  Then Connect

I'm pretty sure that's all it takes but it's been awhile.

---

### Post by L Campbell on 2007-11-23
> **ByteJuggler said:**
> Umm, that would presuambly be patch cables and not crossover cables (there is a difference.)  I presume by "modem" you actually mean modem-router, as in one of these cable modems with 4 ethernet ports that you can connect several computers to (so hence includes a hub/router in the modem.)

Thanks for adding your words of wisdom here.

Its been a while since I did it and I'm not a whiz with computer terminology.

The modem is the one that came with the DSL service and I had always thought of 'modem' and 'router' being separate pieces of equipment.

Kind regards.

---

### Post by mellowd on 2007-11-23
Crossover cable. Both would need a static ip or one of them could be a dhcp server and the other gets an ip via dhcp. They would then be able to communicate with each other.

A crossover cable is essentially the same as a patch cable except that on one of the ends the transmit and receive cables (Tx/Rx) have been swapped around. This allows for full duplex communication without a hub/bridge/switch/router inbetween.

---

### Post by natehatewindows on 2007-11-23
well sometimes they are but if your "modem" has like say four ethernet ports it is also a router.

---

### Post by natehatewindows on 2007-11-23
very well said mellowd!

---

### Post by AlanRogers on 2007-11-23
To answer the OP succinctly:
[LIST=1]
[*]Obtain a cross-over ethernet cable, not a simple patch cable
[*]Allocate a static IP address to the Feisty machine, say 192.168.0.5 or 10.0.0.5
[*]Allocate a static IP address to the Gutsy machine **in the same subnet**, say 192.168.0.10 or 10.0.0.10
[*]Share the necessary folders[/LIST]Bingo, you're good to go. As others have suggested, a router makes connecting them together easier, using DHCP, but this is the answer to the question actually asked.

---

### Post by mellowd on 2007-11-23
> **natehatewindows said:**
> very well said mellowd!

thanx :)

---

### Post by Jimmey on 2007-11-23
Install firestarter on each of the computers, and select to "share" the internet connection. I find if you don't do this, it won't work.

---

### Post by mellowd on 2007-11-23
> **Jimmey said:**
> Install firestarter on each of the computers, and select to "share" the internet connection. I find if you don't do this, it won't work.

That's wrong. Why would you install a firewall and then open it for these two? It has nothing to do with the original request

---

