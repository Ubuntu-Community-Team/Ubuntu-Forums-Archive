---
title: "[SOLVED] Need help with XChat"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by mytwobears on 2007-07-07
Hello - I have been using Ubuntu for about 2 months now and I recently decided to join the Ubuntu IRC Channel, this will be my first time using IRC as well.  I have successfully installed XChat but am unable to connect to the Freenode Network, or the Ubuntu Servers in the xchat Network list.  I receive the following output and error in the xchat client:


 [COLOR="Red"]Python interface loaded
 Perl interface loaded
 Tcl plugin for XChat - Version 1.60 
 Copyright 2002-2005 Daniel P. Stasinski
 [http://www.scriptkitties.com/tclplugin/](http://www.scriptkitties.com/tclplugin/)
 Tcl interface loaded
 xchat remote access loaded successfully!
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (204.11.244.21) port 6667...
* Connection failed. Error: No route to host
 Cycling to next server in FreeNode...
* Disconnected ().
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (204.11.244.21) port 6667...
* Connection failed. Error: No route to host[/COLOR]


I have allowed the port in Firestarter.  I am using Ubuntu Edgy (6.10).  I appreciate any help that can assist me in understanding the above error and hopefully  a solution as well.  Thanks in advance :D.

---

### Post by felicity on 2007-07-07
Weird. Did you try /server irc.freenode.net from the prompt in xchat? Did you try turning off firestarter while you try it?

---

### Post by mytwobears on 2007-07-07
> **felicity said:**
> Weird. Did you try /server irc.freenode.net from the prompt in xchat? Did you try turning off firestarter while you try it?


I tried your suggestion with the firewall on and with the firewall off, unfortunately I received the same results.  Thanks for trying to help :).

---

### Post by felicity on 2007-07-07
Have you tried connecting to any other networks? Though it seems to be another problem.. are you behind any router or using a proxy?

---

### Post by mytwobears on 2007-07-07
> **felicity said:**
> Have you tried connecting to any other networks? Though it seems to be another problem.. are you behind any router or using a proxy?

I did try to connect to the Debian Servers in the list and received the same error.  I have a direct connection, no proxy.

---

### Post by felicity on 2007-07-07
Try this command from a terminal (not in xchat): telnet irc.freenode.net 6667

Does your ISP not allow certain ports to be used? Are you able to use any p2p programs for instance?

---

### Post by RomeReactor on 2007-07-07
Hi. Have you tried using **Gaim** to connect to IRC? Is this the only program with connection problems?

---

### Post by mytwobears on 2007-07-07
I have no problems with other p2p connections.  I have Ktorrent running right now.  I have not tried Gaim but I just downloaded the Chatzilla addon and was able to connect to the Chatzilla irc channel but still no luck connecting to FreeNode.

I will try your suggestion now felicity :), thanks.

---

### Post by mytwobears on 2007-07-07
> **felicity said:**
> Try this command from a terminal (not in xchat): telnet irc.freenode.net 6667

Does your ISP not allow certain ports to be used? Are you able to use any p2p programs for instance?

Tried your suggestion, no luck, here is the result:

Trying 204.11.244.21...
Trying 207.158.1.150...
Trying 208.71.169.36...
Trying 209.177.146.34...
Trying 213.92.8.4...
Trying 64.161.255.20...
Trying 82.96.64.4...
telnet: Unable to connect to remote host: No route to host

---

### Post by felicity on 2007-07-07
hmm, weird that your able to connect to the chatzilla channel though. I'm not sure, I've ran out of ideas! Perhaps someone else can help answer this one...  have you tried any other ports? /server irc.freenode.net 6666 or /server irc.freenode.net 6668 for instance

---

### Post by eternalsword on 2007-07-07
try port 8001 instead of the default 6667.  I had to do that to avoid some dcc bug on my router.

---

### Post by mytwobears on 2007-07-07
Yes, I've tried 6666.  I do think, however, that it may be a connection problem with my network because I can't seem to connect to any other channels with Chatzilla and I couldn't connect to Chazilla's channel just now.

Thanks for your help, I am sure it will resolve itself, I am overseas in Asia at the moment and my network connection is unreliable the majority of the time.  i am just happy that I have Internet and P2P connections going right now :D.


Edit:  I am now connected to the moznet irc channel.  I will try your suggestion eternalsword, Hope it works,  I would really prefer to use Xchat.

---

### Post by mytwobears on 2007-07-07
> **eternalsword said:**
> try port 8001 instead of the default 6667.  I had to do that to avoid some dcc bug on my router.

Hey great!  That port worked perfectly.  Thank you all for your help :D.  I have marked this thread as resolved.

---

