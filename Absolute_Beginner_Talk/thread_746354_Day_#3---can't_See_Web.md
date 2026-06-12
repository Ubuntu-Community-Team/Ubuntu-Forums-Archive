---
title: "Day #3---can't See Web"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by seanarcher on 2008-04-05
100% NEWBIE

been trying for 3 days to somehow get UBUNTU to reach the web.
I have a cable modem.
then router, with 4 switch ports.

I have "sucessfully" installed the 8/07 version of ubuntu now 7 times
twice on a dell inspiron laptop
twice on a dell dimension
twice on a dell optiplex
and now once on an IBM vista workstation

each and EVERY time, it goes flawlessly
except, I can NEVER reach the web


i CAN however reach my local LAN
i can see and copy files from another 2 windows machines
i can ping the other 3 computers,
and the router

i have sucessfully gotten this far with DHCP,
and by setting a static (192.168.1.*)
where the star is a # higher than 10

(11,12,17,19,20,100...all work)

but i aways get THIS far,
and never ever ever ever actually get through to the web.

if in stall a WIN98 or XP on the machines (by overwriting the ubuntu)
they instantly hook up to the web.

after 3 days or forum reading, web searching and 7 re-installs....
i am now begging for outside help!

obviously, i am typing this on a windows box.....

but what am i missing!!?!?!?

i have used the GUI all the way...
and did try the terminal commands....

i am a 100% novice....but is it that hard to get this OS to "just work" for me?!?!?!

ack.
please, help.

please!

thanks

[email]seanarcher@hotmail.com[/email]

---

### Post by upthelum on 2008-04-05
It's odd that you can talk to other machines on a Lan but not to the Internet, which would suggest it's not a problem with your install but with a networking device on the Lan. Try connecting the pc as close to the gateway as possible and check networking firewalls/router settings for a start.

---

### Post by prshah on 2008-04-05
> **seanarcher said:**
> 
and by setting a static (192.168.1.*)
where the star is a # higher than 10


After setting a static IP address, edit your /etc/resolv.conf and point it to your router, eg ```
sudo gedit /etc/resolv.conf
``` then add the following line
> nameserver 192.168.1.1 (Usually)

The restart networking ```
sudo /etc/init.d/networking restart
```
 BANG! You're connected.

---

### Post by ghost_ryder35 on 2008-04-05
you also might want to include some more name servers in the [B]/etc/resolv.conf[B] file like the public DNS servers

Service provider:OpenDNS
Public Name server IP address:
a) 208.67.222.222
b) 208.67.220.220

Service provider: vnsc-pri.sys.gtei.net
Public Name server IP address:
a) 4.2.2.1
b) 4.2.2.2
c) 4.2.2.3
d) 4.2.2.4
e) 4.2.2.5
f) 4.2.2.6

would look like this

```

nameserver 192.168.1.1
nameserver 4.2.2.1
nameserver 4.2.2.5

```

---

