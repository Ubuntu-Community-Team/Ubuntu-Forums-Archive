---
title: "Connecting a Server to the Internet on a Campus Network"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by i.wanna.corndog on 2007-09-10
Hey everybody,

I have sort of a unique situation.  I built a server and installed Ubuntu Feisty Server on it to use as NAS on my college campus network.  I was going to install some additional packages on this server, and I have found that I am unable to connect to the sources. My school network does have a filtering device (called iPrism) that has a graphical web interface so students can log on to the internet.

I am assuming the iPrism is blocking the internet to my server. Is there any way around this? I have Tor installed on my laptop, so would there be a way to route traffic through Tor if I could somehow install Tor on the server? Could someone direct me to more information on this or to a how-to if possible?

Thanks for the help!

Dan

---

### Post by BrendanM on 2007-09-10
Can't you just log into this iPrism thing? Are you blocked from reaching the web or is the campus firewall blocking connections from the web INTO your server?

---

### Post by dca on 2007-09-10
I'm assuming the campus has DHCP enabled where that is issuing an IP address to all clients that access the network?  That makes things a little difficult if you're looking into building a server.

---

### Post by jordanmthomas on 2007-09-10
To log on to my school's network without a graphical web browser, I am able to do one of several things:
1.  Install lynx / links and visit their sign-in page.  
2.  Personally, I use curl.  Here's how it works for my school's page...you'd need to change this to work for you.
```
#!/bin/bash
# logs onto resnet:  must be pysically connected to resnet of course
# in this script, replace MYUSERNAME and MYPASS with the correct values
# Is this really secure?  If someone has access to the file...no, so chmod is your friend.
# Oh well.  Deal with it
# 
MYUSERNAME=jmthomas21
MYPASS=*****
curl -k -d "Bear_ID=$MYUSERNAME&&Password=$MYPASS" https://resnet.tntech.edu/netauth.php
unset MYUSERNAME
unset MYPASS
```

**edit** and like dca said, DHCP is not your friend if you're hosting a web server, unless you're just hosting it for your LAN.  Then it's no big deal really (at least Windows computers can easily connect with just the hostname).

---

