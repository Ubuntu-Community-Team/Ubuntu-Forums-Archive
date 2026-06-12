---
title: "Headless server problem"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by senrew on 2007-08-25
Ok, this is my first time actually posting, also the first time I couldn't find an existing answer for my problems.

I installed ubuntu server. Went into the CD and manually installed openssh-server. Put the headless server in it's corner, connected ethernet and power and turned it on. My router config reports it pulling an IP address. I've waiting long enough for it to have booted. 

I tried this two ways...with PuTTY on my vista laptop and via ssh on my kubuntu desktop, but both times got a timed out error when trying to connect. I can't ping the server either. Supposedly, instaling the OS, making sure ssh is up and putting the thing in it's permanent home and all connected is all that's needed.

So...I don't get why I can't see the box remotely. I'm thinking that it's just some stupid step I glossed over, but then again, it could be something else entirely. Not sure. Any ideas why it may not be working?

BTW...I tried connecting my monitor and keyboard/mouse. Doing that, it just sits at the first login prompt. So I know it's booting alright at least.

---

### Post by sad_iq on 2007-08-25
Have you pinged the ip of the server or the name?? Try pinging the ip...see if it works...maybe it's a DNS error.
P.S. Sorry for myshort message but i just woke up...I need to drink my cofee first!

---

### Post by senrew on 2007-08-25
Yeah. 

I get a whole buttload of these that don't end until I ctrl+c the thing:

From 192.168.0.102 icmp_seq=xxx Destination Host Unreachable

Again, the router DHCP config shows that the server is pulling an IP lease. So, I dunno.

---

### Post by senrew on 2007-08-25
actually...

The ping results show as follows.

PING 192.168.0.102 (192.168.0.102) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=xxx Destination Host Unreachable

I didn't notice the fist time, but the first line is my servers IP. The results however show the IP of the box I'm working off of. Why is that?

---

### Post by mrgrapefruit on 2007-08-25
Make sure sshd is running on the ubuntu box, and make sure it is configd properly - which should be at something like ```
/etc/sshd_config
```

Also if thats not the problem, make sure the router is set to port forward for SSH.

---

### Post by senrew on 2007-08-25
I'll try that. Then again, why can't I even ping the thing? Should be able to do that from any connected machine on my network.

---

### Post by Dr Small on 2007-08-25
It sounds more like a network problem than an SHH problem, in my opinion, since you can not ping the computer. You should be able to ping any computer, with or without openssh-server on it. That is just an option.

Edit, I would screw this server's head back on, and try to see if I could connect outside of the computer, (to the network) from the server. But, just the same, I still think it is a network problem.

Dr Small

---

### Post by kevdog on 2007-08-25
You have to open up ports in the firewall to allow ping, ssh, etc. I believe by default all inbound ports on ubuntu are closed by default.  I believe you need to modify your iptables.  I can across an interesting way to do this yesterday without having to modify the IPtables manually,  take a look at this (Im only recommending this -- not sure if Firestarter works on server edition):
[http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111)

---

### Post by southernman on 2007-08-25
Network Problem +1

I am with Dr Small on this one. If I were you, I'd put the head back on and setup a static ip on the server. You shouldn't have to open a whole in your router, unless you aim to ssh in from outside your lan.

To connect from your lan just do:

> ssh username@x.x.x.x
replace username with the user setup on the server and use the static ip of the server... on first connetion you'll have to save the RSA key (just type "yes" and enter) then supply the password for the server username and you should be good to go.

edited - ssh config file is located at /etc/ssh/sshd_config. Out-of-the-box it should just work. Only edit the file to lock it down.

---

### Post by Dr Small on 2007-08-25
> **kevdog said:**
> You have to open up ports in the firewall to allow ping, ssh, etc. I believe by default all inbound ports on ubuntu are closed by default.  I believe you need to modify your iptables.  I can across an interesting way to do this yesterday without having to modify the IPtables manually,  take a look at this (Im only recommending this -- not sure if Firestarter works on server edition):
[http://ubuntuforums.org/showthread.php?t=57111](http://ubuntuforums.org/showthread.php?t=57111)
Yes of course. The firewall on the server must allow inbound connections, for hosts and then port 22 needs to be opened to allow ssh access. I forgot about this. I have no idea how to do this on a server addition, via the command line, as I have never did it that way. I have only ever did it via Firestarter, but I am sure there are some documentation on the wiki about iptables.

Dr Small

---

