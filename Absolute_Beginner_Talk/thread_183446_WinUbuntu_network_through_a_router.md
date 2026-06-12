---
title: "Win/Ubuntu network through a router?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-05-28
Hi all,

Here's a bit of a tricky setup I'd like to do and need your help:

I've got two computers on my desk, one is running Windows XP Pro, the other running Ubuntu 5.10.  Both computers are connected to a Westell router/modem which is connected to my ADSL provider.  Both computers can access the internet without any problems.

Here's what I'd like to do:
I would like the Windows machine to be able to do file sharing with the Ubuntu machine -but- I don't want the Windows machine to have Internet access.  I would like the Ubuntu machine to have the shared folder and have internet access.

How do I set this up (I'm assuming it can be done)?  THANKS!!!

---

### Post by dmizer on 2006-05-28
couple of ways that you could do this.

this is a bit tricky ... most networks have a seperate router and modem, whereas you have a modem/router combination.

you could add a network card to your ubuntu box, and connect your ubuntu box to your windows machine with a crossover cable.  as long as you don't have ics enabled on your ubuntu box (it is not enabled by default) you shouldn't have to do any other configuration.

if you have access to the configuration for your westel modem/router, you should be able to configure it so that it blocks outbound traffic by ip.  you will likely have to set up static ip for your local network to make this work.

as far as sharing files is concerned ... you'll need to install and configure samba.

---

### Post by joshrobinson on 2006-05-28
yeah intall samba(smb) on the ubuntu machine.. in my router i have settings to where i can block the mac address on a computer from the internet, so i can still share files over the network, but the computer cant get internet or be seen on it

so install samba, select what you want to share, and add a user account on your ubuntu computer, so you can login with a password on the windows box

---

### Post by bigkahuna on 2006-05-28
[QUOTE=dmizer]you could add a network card to your ubuntu box, and connect your ubuntu box to your windows machine with a crossover cable.[/QUOTE]
I think this might ordinarilly be the easiest way, -except- that my Ubuntu box is a notebook computer, which means I'll have to use a PCMCIA NIC, and I've heard that can be tricky to install?  Is that all PCMCIA nic's or just wireless?  I would have to use a -wired- nic.

I did a Samba install once before (when I was using Kanotix) so I think I'm mentally prepared for the worst ;)

---

### Post by dmizer on 2006-05-28
lol ... you could ask around to see if anyone has any old computers they don't need anymore.  i've gotten several fantastic server boxes that way.

300mhz pII and 128m of ram and you can do a server install.  might be a bit tricky to learn how to manage, but you're likely to get away with a free fix for your problem.

keep in mind, linux will still boot your box on a 300gig (for example) hard drive even though the mainboard bios won't support it, so you could free up your limited space on the laptop.

if you can't get someone to give you one, you can usually obtain one for an extremely reasonable price.

all this is assuming that you are unable to gain access to your router/modem config page because your isp owns it.

my pcmcia network adapter works fine.  i had to edit a config file to make it work, but it wasn't too difficult.  i doubt you'll be able to find it anymore except used though ... it's a linksys (network everywhere) model np100.

if you take a bit of time and do some searching, you will be able to find a card that works right out of the box.  if nothing else, you can post a question about it ... i'm sure someone on this forum has one that's more current.

---

### Post by bigkahuna on 2006-05-28
I've got an "ancient" pentium I33 notebook that I installed DSL (damn small linux) that I could use, but can't because there are no nic's that will work with it any more.

As I shopped for a PCMCIA nic I remembered that I have one someplace laying around.  I'm pretty sure it's an older linksys, it would be funny if it's the same model as yours ;)

---

### Post by dmizer on 2006-05-28
[QUOTE=bigkahuna]I've got an "ancient" pentium I33 notebook that I installed DSL (damn small linux) that I could use, but can't because there are no nic's that will work with it any more.

As I shopped for a PCMCIA nic I remembered that I have one someplace laying around.  I'm pretty sure it's an older linksys, it would be funny if it's the same model as yours ;)[/QUOTE]
holler at me if it is.  mine has a dongle, hope you can find the card and dongle together ... lol.

---

### Post by bigkahuna on 2006-05-28
Just found it (glad I didn't throw it a way ;) ), it's a Netgear FA511.  No idea if / how it works, never used it before...  No dongle necessary...

---

### Post by Jussi Kukkonen on 2006-05-28
before you start installing new equipment, check if your modem/router has a web configuration interface ([http://192.168.0.1/](http://192.168.0.1/) is a popular choice, I think), and if you can add firewall rules in there...

---

### Post by bigkahuna on 2006-05-28
[QUOTE=Jussi Kukkonen]before you start installing new equipment, check if your modem/router has a web configuration interface ([http://192.168.0.1/](http://192.168.0.1/) is a popular choice, I think), and if you can add firewall rules in there...[/QUOTE]
Thanks Jussi.  Yes it does have a config interface, I'm just afraid to mess with it (I am still a noob when it comes to networking).  I'll check into it though.

---

### Post by dmizer on 2006-05-29
[QUOTE=bigkahuna]Just found it (glad I didn't throw it a way ;) ), it's a Netgear FA511.  No idea if / how it works, never used it before...  No dongle necessary...[/QUOTE]
plug it in, connect it to your modem/router, and see if it will connect.  if so, you're most of the way there.

---

### Post by bigkahuna on 2006-05-29
Yup, everything seems to be up and running now.  Thanks!

---

