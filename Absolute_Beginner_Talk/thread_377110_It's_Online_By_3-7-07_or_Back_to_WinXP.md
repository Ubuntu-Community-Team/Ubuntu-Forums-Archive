---
title: "It's Online By 3-7-07 or Back to WinXP"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Carewemust on 2007-03-05
Hello Everyone,

I talked my wife into letting me put Xumbuntu on my 11 year old son's computer this past weekend, because Microsoft wanted $99 to upgrade his 2000 Dell from WIN98 to XP.   

Getting the Xubuntu image burned onto a CD using another computer and then putting it on my son's PC was simple enough.  Very easy.  But for the past 3 days I've been pulling my hair out trying to get his computer online to our home network. Three days ago, I found this link here in the Ubuntu support area: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear) , so I went to Best Buy and purchased a NetGear WPN311 PCI Desktop Card and installed it in his PC.  This community document says that the NetGear WPN311 is one that would work  "Right Out of The Box", but I get the feeling that there's something else I need to do, because Linux's "Right Out of The Box" doesn't seem to mean the same thing as Windows "Plug and Play".   I've read several topics here that talk about an NDSWrapper, Typing Commands into some kind of Terminal, etc..  The LinkSys USB thing that I had plugged into the back of his computer worked great with Windows98/XP, but not with Linux, which is why I purchased the NetGear WPN311.

I have roughly 36 hours to get Nathanael's PC onto our home Network, or my wife is going to cough up $99 and force me to convert back to WinXP.  I really would prefer not to do this, but I'm getting fatigued.  Is there any manual which shows SCREEN SHOTS of the steps for getting a Linux compatible PCI Card online with a home network?   Pictures are worth a thousand words.  Any help is appreciated.  -Bert in Chicago

---

### Post by crispy_420 on 2007-03-05
Ok first of all is your network card, the new one, even seen in Ubuntu?

> System -> Administration -> Networking

Is the hardware seen?

> lspci or dmesg

If not install linux-restricted-modules for your setup (CPU & kernel). This should add the atheros driver you need. Here is the run down of it:

> This package provides restricted modules for Linux version 2.6.15 on
Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)

These modules are "restricted" because they are not available under a
completely Free licence.

OK if all seems functional, try to access the network with all security turned off.

Let's just start there for now.

I actually have the same chipset in my laptop. And I love it. For me it worked right of the bat, but I may have had those drivers already installed. As a side note, this chipset is great with network-manager. But since you have a desktop you may not need it but is a nice feature.

Here are some links that may help too:

[http://doc.gwos.org/index.php/MadwifiDriver](http://doc.gwos.org/index.php/MadwifiDriver)

[http://doc.gwos.org/index.php/Network_Manager_with_WPA](http://doc.gwos.org/index.php/Network_Manager_with_WPA)

[http://doc.gwos.org/index.php/WirelessMadwifiNG](http://doc.gwos.org/index.php/WirelessMadwifiNG)

I've always found the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page") a good bet for guides.

---

### Post by Carewemust on 2007-03-05
Thanks Crispy420.  I'll print this out and take it with me tomorrow when I go back over there to work on my son's computer.   I'll also figure out what those two little commands were you were referencing.  I've always lived in a "plug and play" world and have no idea about where to type commands.  Guess I'll need to learn if we're staying with Xumbuntu.  Since a search of the entire web is not turning up a Diagnostic program that I can burn to CD and stick in his computer to help guide me towards what's missing, this is looking more and more like a brief affair.   Maybe if my son was 2 years older, he would take the time to figure this all out.  I'm too busy..  But God I hate  to give Bill Gates $99.   That's the only thing that's driving me to perservere on this frustrating quest to get Nate hooked up to the Home network.   Thanks again Crispy420 and have a superb week sir!!  
-Bert in Chicago

---

### Post by Amenemhet on 2007-03-05
Some good advice there, and I will keep an eye here solely to prevent $99 going to Bill.
I am sure that a lot of people here feel the same. Let's get your son's pc fixed!!!

---

### Post by user1397 on 2007-03-05
> **Carewemust said:**
> Thanks Crispy420.  I'll print this out and take it with me tomorrow when I go back over there to work on my son's computer.   I'll also figure out what those two little commands were you were referencing.  I've always lived in a "plug and play" world and have no idea about where to type commands.  Guess I'll need to learn if we're staying with Xumbuntu.  Since a search of the entire web is not turning up a Diagnostic program that I can burn to CD and stick in his computer to help guide me towards what's missing, this is looking more and more like a brief affair.   Maybe if my son was 2 years older, he would take the time to figure this all out.  I'm too busy..  But God I hate  to give Bill Gates $99.   That's the only thing that's driving me to perservere on this frustrating quest to get Nate hooked up to the Home network.   Thanks again Crispy420 and have a superb week sir!!  
-Bert in Chicagoby the commands " 			 				lspci or dmesg ", he means to run a terminal (go to XFCE menu > Terminal) and first type:
```
lspci
```and copy/paste the results of that here.  after that, in the same terminal type: ```
dmesg
``` and copy/paste the results here.  don't worry about figuring stuff out, we're always here to help.

PS If you're still deciding where the terminal is, here's a picture guide to finding the terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

---

### Post by maniacmusician on 2007-03-05
> **ubuntuman001 said:**
> by the commands " 			 				lspci or dmesg ", he means to run a terminal (go to XFCE menu > Terminal) and first type:
```
lspci
```and copy/paste the results of that here.  after that, in the same terminal type: ```
dmesg
``` and copy/paste the results here.  don't worry about figuring stuff out, we're always here to help.

PS If you're still deciding where the terminal is, here's a picture guide to finding the terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)
I have to ask, is there any particular reason you chose xubuntu? Is your son's computer excessively slow or old? while xubuntu is an awesome system to use, I feel it's easier to use Ubuntu or Kubuntu for a brand new user, until one is more experienced with Linux.

Believe me, if the community docs said it works out of the box, it works out of the box :) what you have to do, as someone else mentioned, is find the Networking applet in your menu, and "enable" the card and the wireless network. Then, you should be good to go.

---

### Post by lamalex on 2007-03-05
hang in there buddy!!! Your kid will thank you when all of his friends have viruses and all he has are hot chicks following him around due to his linux skills. [projected outcome when he's old enough of course].

---

### Post by Arisna on 2007-03-05
Okay, let's back up a bit here.  Are you 100% sure that you inserted the network card all the way into the PCI slot?  I installed one of these for a client recently.  I had forgotten how much force is required to get them in all the way.  A good indicator of this is how well the slot in the metal plate attached to the card lines up with the chassis where it is secured with the small bolt.

---

### Post by crispy_420 on 2007-03-07
It does not take much force to insert a PCI card. If even not all the way, you will still have contact points. As far as the case screws lining up, that will depend on the quality of the case.

---

