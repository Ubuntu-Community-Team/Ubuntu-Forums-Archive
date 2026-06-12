---
title: "ubuntu to XP gateway"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-02-11
I'm sure this is obvious, but I can't seem to figure it out, despite searching.  Two machines, one ubuntu(just!) one XP with broadband connection set up with ICS.  Both machines static IP address, and the ubuntu sees all the files shared on the XP, both machines ping each other.  How do I get the ubuntu firefox to connect through the gateway XP machine?
Thanks

---

### Post by souteneur3190 on 2006-02-11
give or draw a diagram of EXATCLY these two comps are connected.

---

### Post by damianubuntu on 2006-02-11
ubuntu: network card to hub.
XP: network card to hub & usb modem for broadband.
Is that sufficient?
(thanks for replying:)

---

### Post by bonzodog on 2006-02-11
most people would have that the other way around, with the ubuntu machine facing the net - you can control what comes into the Xp machine that way. Apart from that, I don't know exactly how to solve your problem.

---

### Post by d1337 on 2006-02-11
On your Ubuntu machine, is your /etc/network/interfaces pointing to the ip address of the XP box like
```
gateway         IP ADDRESS OF XP MACHINE
```

d1337

---

### Post by damianubuntu on 2006-02-11
HI D1337,
yes it is.

---

### Post by d1337 on 2006-02-11
Bonzodog is correct in saying that most folks have Ubuntu facing the net...but I'm sure that this can be done.  Is your hub just a switch or is it a router with a web interface?  If it has a web interface, you'll likely need to set it up as more or less a gateway pointing to the XP machine.  If it's just a switch, I'll do some research and see what I can find.

d1337

---

### Post by damianubuntu on 2006-02-11
its just a switch.  Hoping to transfer both machines over to linux, I just thought it would be easier to do one, leave the other with its internet connection for support, get one set up properly, and then start on the next one.  But perhaps I shouls just try and get the modem installed on the linux next.
Thanks for your help

---

### Post by d1337 on 2006-02-11
That may be your best bet.  If you want to pursue XP as a gateway though, I'd like to see you relevant portion of your /etc/network/interfaces as this may be a dns issue.

d1337

---

### Post by bionicyeti on 2006-02-11
Are you sure it might just not be a dns issue??? Did you try to ping a public IP address?

---

### Post by damianubuntu on 2006-02-11
well, whilst I try and get the modem set up, here is the interfaces stuff:
iface etho0 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

thanks

---

### Post by bionicyeti on 2006-02-11
Just for fun, from the XP box ping [www.yahoo.com](www.yahoo.com). It will resolve to 68.X.X.X or whatever. Go to the Ubuntu box and try to ping the number. See if get a reply.

---

### Post by d1337 on 2006-02-11
Did you copy and paste from /etc/network/interfaces?  etho0 looks funny to me.  Also, you may look at /etc/resolv.conf and insure that you have some dns info in there.  This varies to your particular setup and isp.  What bionicyeti is saying will help you see how it is resolving through dns which you can likely add to your /etc/resolv.conf or at the bottom of you /etc/network/interfaces.  Snips from mine follow:
```
# The primary network interface
auto eth0
iface eth0 inet static
        address         192.168.0.137
        netmask         255.255.255.0
        network         192.168.0.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 151.164.1.8 151.164.64.201
```
and resolv.conf
```
:~$ cat /etc/resolv.conf
nameserver 151.164.64.201
nameserver 151.164.1.8
nameserver 68.94.156.1
```
Having dns info in two places is not needed, just happens to be how mine is set up.

d1337

---

### Post by damianubuntu on 2006-02-11
great idea
ping works from ubuntu box to external address, so what do I need to do to get the DNS working?

---

### Post by Lord Illidan on 2006-02-11
Check the DNS servers from the XP box, and copy them to your machine. On Ubuntu the settings will be under System - Administration - Networking - DNS.

EDIT : Under XP the settings are in the Control Panel, networking, and somewhere in TCP/IP, I think.. Haven't used it for ages, though.

---

### Post by d1337 on 2006-02-11
Who is your isp and where are you located?  A google search can show you what your dns needs to be.

d1337

edit: or get info from xp as Lord Illidan suggested

---

### Post by damianubuntu on 2006-02-11
etho0 was a typo, haven't yet figured out how to copy and paste between machines;-)
and
my resolve.conf is completely empty.
Do I need to get appropriate DNS addresses from ISP or will yours do?

---

### Post by d1337 on 2006-02-11
Make sure you are looking at /etc/resolv.conf (not resolve).  You will likely need specific dns info...unless you are in the Little Rock, AR area.

d1337

---

### Post by Lord Illidan on 2006-02-11
Use the DNS info which is working on the XP machine of course.. just write it down on a paper, hehe...

---

### Post by damianubuntu on 2006-02-11
on XP my DNS addresses are automatically got from the ISP, which is BT UK, found the addresses on google but my resove.conf and interfaces are read-only.  Do I have to edit them in a terminal using sudo and if so how?

---

### Post by d1337 on 2006-02-11
I'm a vi kind of guy...so I would
```
sudo vi /etc/resolv.conf
```
enter your password, use shift+i to insert, shift-esc when done, shift z (twice) to save and exit.  Then restart networking (sometimes not needed) by
```
sudo /etc/init.d/networking restart
```
and try again.

d1337

---

### Post by damianubuntu on 2006-02-11
OK so done that but still no joy.
resolv.conf now reads:
nameserver 194.75.65.69
nameserver 217.35.209.189
nameserver 62.6.40.162

interestingly I put them first in interfaces, but then got a fail on restarting the networking?  Do they have to be in resolv.conf in order for interfaces to see them?  I now have them only in resolv

---

### Post by damianubuntu on 2006-02-11
also in trying to set up my modem, I get the message package pppoe not installed.
Any advice on how to do this, and is this also causing the problems with the browser?

---

### Post by d1337 on 2006-02-11
A bit stumped...but lets back up for a minute.  Sorry if this seems too remedial.  Are you certain that your connections are good and clean?  Are you certain that the ip address of the xp machine is static and is 192.168.0.1?  Are you certain that internet connection sharing is enabled?  Not sure how the xp firewall works, but is it set to allow connection from 192.168.0.2?  It may be difficult (read: plenty of research involved) to get your modem up and going without internet access on the Ubuntu machine as you'll likely need some packages (like pppoe for instance).  I don't think that this is a related issue, but as my avatar and name hints to...caution, I am the opposite of 1337.

d1337

---

### Post by damianubuntu on 2006-02-11
I'm pretty sure that all this is OK.  The two machines were working as two XP boxes, so I reckon the ICS and firewall are OK.  I use Kerio firewall which throws up any requests that it doesn't recognise anyway, and that's all been quiet.  I can ping 192.168.0.1/2 both ways and ping out on the ubuntu machine to ip addresses.

Hold on, just double checked the pinging and now I get network is unreachable.
??

Thnaks again for your time, I'm glad you're not doing anything else today;-)

---

### Post by damianubuntu on 2006-02-11
Rebooted the box, and lo and behold ping works, ping name works and browser resolves names!  Yippee

Thanks very much for everyone's help

---

### Post by d1337 on 2006-02-11
Woot!  Glad it works...and now we both know how it's done :)

d1337

---

