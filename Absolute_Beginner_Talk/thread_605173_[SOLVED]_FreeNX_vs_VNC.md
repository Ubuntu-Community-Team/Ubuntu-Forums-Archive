---
title: "[SOLVED] FreeNX vs VNC"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-11-06
I have been using VNC to connect to my ubuntu machine by setting up properties under System>>Preferences>>Remote Desktop. It works when I am within the network.

I, now want to access it from the internet. I read that there could be 2 ways of doing it
1) FreeNX
2) SSH over VNC

I know that option 2 needs a DynDNS account, but does FreeNX need something similar. Basically, I want to understand the differences between the two.
Which would be a better option? What are the pros and cons of each if any?

Also, could someone tell me the differences between them?

Applications>>Internet>>Terminal Server Client. It has options of RDP RDPv5 and VNC. Is this the same as System>>Preferences>>Remote Desktop ?

---

### Post by Dr Small on 2007-11-06
I myself, like you, have only used VNC also.
I would suggest trying out FreeNX and see if you find any advantages over it.

And, setting up a DynDNS account isn't that hard ;)
That reminds me... I need to update my IP address on mine :p

Dr Small

---

### Post by Inxsible on 2007-11-06
I used vnc  but the problem is that it was quite slow even in the same network. So I am assuming it will be a sloth over the internet.

That's why I wanted to see if FreeNX provides something better. There is also Hamachi, as I recently discovered, but I have no clue as to how to use it.

I guess if someone could point out a link describing the pros and cons of all it would be great.

Just trying to get a feel for all of them.

Thanks

---

### Post by maybeway36 on 2007-11-06
I've only used VNC because of x11vnc. I haven't found any other programs that do this on Unix, and I would even say it's one of my favorite Linux programs (another being Konqueror.)

---

### Post by Dr Small on 2007-11-06
> **Inxsible said:**
> I used vnc  but the problem is that it was quite slow even in the same network. So I am assuming it will be a sloth over the internet.

That's why I wanted to see if FreeNX provides something better. There is also Hamachi, as I recently discovered, but I have no clue as to how to use it.

I guess if someone could point out a link describing the pros and cons of all it would be great.

Just trying to get a feel for all of them.

Thanks
Check this page out:
[http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software)

---

### Post by Inxsible on 2007-11-06
> **Dr Small said:**
> Check this page out:
[http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software](http://en.wikipedia.org/wiki/Comparison_of_remote_desktop_software)
thanks Small,

I think from what I read there, NXServer/NXclient seem to handle all technologies like NX,VNC,RDP etc.

so the comparison should not be between FreeNX and VNC rather the protocols themselves like NX VNC RDP etc.

hmmm....a lot of researching needs to be done on my part :D

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

