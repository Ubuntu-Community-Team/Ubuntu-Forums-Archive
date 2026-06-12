---
title: "Hi I need some help with firestarter and an SMB share."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Bright Hammer on 2007-12-04
Let me describe my network. 

1 Desktop with a samba share where everyone has write access (gusty) Static Ip
1 Laptop with a samba share “ “ (gusty) dhcp
1 Xbox running XBMC (able to access the shares to play media files)static ip

I was able to access both shares from my xbox to play media files. I installed firestarter on my laptop and now I am unable to access the share while the firewall is enabled. Here is what I have configured for inbound policy.

Inbound hosts - 192.168.0.1/24
Inbound service- SMB (everyone)


When I try to access the laptop from the XBMC I get connection was refused while the firewall is on. When it is off I don’t have any problems. I can turn it off and be happy but I would like to figure out why this is happening. If you need more info let me know. 

Thanks in advance for your help.

---

### Post by Paqman on 2007-12-04
Can you explain what you mean by having trouble "when the firewall is on"?

Firestarter isn't a firewall, it's just a configuration GUI for the built-in iptables firewall system. You shouldn't leave Firestarter running anyway, since it runs with super user privileges.

---

### Post by Bright Hammer on 2007-12-04
When I said that firestater is on I mean when it is active. I when I disable it I am able to access the share.

---

### Post by jms830 on 2007-12-21
I have the same problem. If I open firestarter, and click "stop firewall" then my xbox can connect to my desktop's samba share. However, if I "start firewall" back up again in firestarter, then my xbox cannot connect to the samba share. It is very annoying to have to stop my firewall every time I want to connect to my samba share.
My xbmc xbox ip is 192.168.0.110. I know that is it because I can connect using ftp to it. In firestarter I have tried allowing samba ports (137-139 445) for 192.168.0.110. It still will not connect.

---

### Post by ceejay on 2008-01-02
Hello

Well, ever optimistic, perhaps someone will see the post this time - but I have exactly the same problem as the previous two posters.  I've used firestarter to configure the firewall to allow access to the samba ports, but its not working.  If I stop the firewall altogether, samba works fine and the external devices can connect to my shares. But if I start the firewall they can't connect.  

I'm using Ubuntu 7.10.  I've tried to allow incoming access to 192.168.1.1/24 (meaning the whole of my local network???) and the samba ports specifically.

Since a major function of this box is to serve up shares, this is a bit of a problem - I'm having to leave the firewall turned off all the time, which is not ideal!

All clues much appreciated.

TIA

---

### Post by Banj on 2008-02-02
I'm having the exact same problem.

If I open firestarted I can internet connection share with XBMC but can't share files through SMB.

If I stop the firewall in firestarter I can access my shares but can't internet connection share anymore.

I think it's because XBMC will only see my shares by browsing the workgroup. If I point XBMC to an IP address it won't work. I think this is why even when I allow SMB ports for my subnet in firestarter it still blocks the share.

I could really use some help here because I'm totally inept at networking and I'm frankly amazed that I've managed to blunder my way as far as I have,

:)

---

### Post by jms830 on 2008-02-04
Hey, I finally solved this problem using this post

[http://ubuntuforums.org/showthread.php?t=190542](http://ubuntuforums.org/showthread.php?t=190542)

---

