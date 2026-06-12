---
title: "DSL Network? Can't get internet to work."
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by KomodoDragon on 2005-10-03
Ok, first of all I've only used linux once before: Mandrake, but didn't find it very complete.  Found Ubuntu, and it looks great.  

Anyway I'm a major newbie.

How do I get a PPP DSL internet connection to work?  I've managed to activate the network card, but I can't figure out how to input all the right usernames/passwords and Pop/Domain/IP address for my ISP.

I am duel booting with windows xp so I was able to get all the information about my connection from my existing windows High Speed connection manager.

I have Server IP/ Device Name and Type/ Server Type/  Transports/ and Authorization. "0.0.0.0", WAN Miniport, PPPoE, PPP TCP/IP and PAP respectively.

I also have all the information for the ISP for the computer connect with.

Anyway a fairly detailed explaination how to do this would be great thanks.
:confused:

---

### Post by adwait on 2005-10-03
Try this command
```
sudo pppoeconf
```

---

### Post by KomodoDragon on 2005-10-03
Thanks, I'll try that, and let you know if it works.
:p

---

### Post by KomodoDragon on 2005-10-03
Ok, the above probably would have worked, except I don't know how to get into "root" admin at the terminal so I can use pppoeconf.  Which is unfortunate.


Again I'm a green newbie who really  wants to learn.  Anyway what command line do I use to get from the terminal default /home/<user> to /root so I can change the necessary things on my computer.:confused: 


Thanks for the help in advance.

---

### Post by KomodoDragon on 2005-10-03
Well no luck so far. I've managed to "learn" some things on my own however. I've learned how to log in as root using su <username> <password> command, giving myself temp superuser powers, but the sudo pppoeconf didn't work.  The only place on my computer I can find pppoeconf is in the man -k (help) file!!!

Ok there has got to be more people out there than just me with ubuntu that have DSL internet connection.  How did you figure out how to get around the Windows Installation CD and just be able to put in the ISP username and password.  Good Grief this can't be that hard can it.:???: 

Anyway I'm stuck, and if I can't get this figured out soon I guess I'm going to have to switch linux distro's.  Other than this really annoying bumb in my linux journey I'm enjoying ubuntu.

All I need is to get from my computer network/ethernet card to my DSL modem and viola onto the net.  It really shouldn't be this hard.  And besides of the 34 people who have viewed this post I'm sure a few of them have DSL set up on their Ubuntu linux.

HELP!:confused: :confused: :confused:

---

### Post by KomodoDragon on 2005-10-03
Well no help yet, so I'm off to try Ark Linux.  I do have Breezy, which from doing so research on the forum seems to have some serious problems with pppoe so I think rather than frustrate myself I'm going to a different distro. 

All the same if someone finds the solution I'd like to know. thanks.

---

### Post by Mustard on 2005-10-03
If I had an understanding of networking I would try to help.  My only suggestion is to type your query into the search function on the forum and read through all the threads that relate to people have issues with pppoeconf.

From the sounds of it, you have conigured a root account during an expert install.  I have found that after I do an expert install that it's necessary for me to edit the **/etc/sudoers** file to give my user account superuser privileges.  I would try to fix up your superuser functions before tackling the pppoeconf problem.  Pppoeconf should be either installed already or available for install through the synaptic package manager.

Here is an example of my sudoers file:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

---

### Post by Mustard on 2005-10-03
I found these links in the wiki on pppoeconf.

[https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28pppoeconf%29](https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28pppoeconf%29)

[https://wiki.ubuntu.com/ISPAuthentication?highlight=%28pppoeconf%29](https://wiki.ubuntu.com/ISPAuthentication?highlight=%28pppoeconf%29)

---

### Post by redfan on 2005-10-03
Hi,
I'm still a beginner to Linux myself, however I have used several distro's on i386 based machines previously over the last few years.  Now I use a PPC machine and it's my first time with Ubuntu on this machine.
Maybe I have not read what you are trying to do correctly but could you confirm are you using a ethernet connection to your DSL modem or USB?
I ask because the configuration problems you talk about sound more USB related.  I had similar issues sometime ago, and to be honest the easiest way around it was to connect via ethernet.
Should your DSL modem not allow a e/net connection then you should be able to find a DSL router that will.  As long as your DSL connection is active and you are connecting with e/net Ubuntu and most other distro's should pick up your connection.
Not sure if that helps but hey, I'm trying ;)

---

