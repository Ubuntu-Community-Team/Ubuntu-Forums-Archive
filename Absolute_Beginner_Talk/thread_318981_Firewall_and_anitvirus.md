---
title: "Firewall and anitvirus"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2006-12-14
Hello everyone,

I asked this before and thought I understood the answer. Now I am starting to believe that I might not. I know Ubuntu comes with a pre-installed firewall. Here are my questions:

1) do I need to install a firewall like firestarter?
1) do I need to install a virus screener like clamav?

Thanks, loyaleagle :mrgreen:

---

### Post by loyaleagle on 2006-12-14
from reading this....

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

But coming from the windows XP world... it seems to easy to be true.

of course, that is part of what I like about Ubuntu.

Please, tell me your take on this....

Thanks again, Loyaeagle:confused:

---

### Post by scxtt on 2006-12-14
i installed 5.10 once and right after install (making sure sshd was installed/running) i tried to connect to my box from an outside account (old college one) ... i'd passed port 22 from my router to my boxes IP and i was able to get a login ... i don't think Ubuntu "closes" all ports waiting for you to open them, don't know of many "desktop" linuxi that do ...

i'd do 1 of 2 things, regarding a firewall:

1. don't forward any ports from a router
2. install a firewall (firestarter / kmyfirewall) and turn it on *immediately*

if you're not sure whether iptables is doing anything, run **sudo iptables -L** and post your output ...

---

### Post by STREETURCHINE on 2006-12-14
i switched from windows about 4 months ago ,no problems i have both firestarter and clam av 
installed but have never turned them on .my local computer tech(fixes all my stuff ups)uses linux he is the one who put me on to ubuntu.
now he told me i dont need the firewall or antivirus (and he is god ,so i believe him)
so i dont think it is a thing you should worry about unless you intend to duel boot with windows, and even then highly  unlikly you will ever need them.:-D

---

### Post by aysiu on 2006-12-14
Don't know that much about networking, but wouldn't installing *sshd* open a port?

---

### Post by scxtt on 2006-12-14
if you're behind a router and forward NO (read 0 {zero}) ports - you're fine - especially if you're the only one on the router ... if you're directly connected to your modem, i GUARANTEE "people" will make attempts to connect to "common" ports on your box (i.e. 22 {ssh}, 5900 {vnc}, etc.) ... so if you actually want to use your box remotely (i do from work) you'll want a firewall going after you forward a/some port/ports ... ssh will be password protected and VNC can easily be p/w protected -- personally i block out ALL IPs but my work IP - so the firewall stops all non work-ip users dead in their tracks ...

as for antivirus ... i'll never install A/V software in linux, it's pointless - unless you're sharing files w/ a windows user and care if your linux box d/l some windows virus to pass along ...

sshd won't open a port - but it'll "listen" on port 22 ... just like VNC {vncserver} will "listen" on port 5900/5901/5902, etc ...

---

### Post by loyaleagle on 2006-12-14
I installed firestarter and don't see it in my menu.... should I be able to see it and configure it?

---

### Post by scxtt on 2006-12-14
it's running - all the icon in the system tray does is configure it ... it'll be in your /etc/rc2.d directory to start @ boot ... and once installed / running, it should be restrictive until you open specific ports / IPs ...

---

### Post by loyaleagle on 2006-12-14
Got it... found it under Administration... Thanks everyone!

---

### Post by steve.horsley on 2006-12-15
> But coming from the windows XP world... it seems to easy to be true.
That's because you're used to XP world. The default Ubuntu install really is not listening for incoming connections at all - a firewall would have nothing to do.


> **aysiu said:**
> Don't know that much about networking, but wouldn't installing *sshd* open a port?

Yes indeed it would - TCP port 22 is the normal SSH port.

Once you have done that, you need to either install a firewall to control the addresses that can talk to it, or use /etc/hosts.allow and /etc/hosts.deny do control who can talk to it, or configure it for certificate authenticated access only. Or a combination of these.

---

