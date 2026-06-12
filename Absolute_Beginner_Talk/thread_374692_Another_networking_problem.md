---
title: "Another networking problem"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Newbie1Kenobi on 2007-03-02
Hi all, I'm new to Ubuntu, just installed it today and I cannot connect to either my home network or the internet.  I'm trying to connect through my router, but I am not getting anywhere.  If anyone or several someones can walk me though the entire process (identifying Ethernet card, finding drivers, etc) I'd be eternally grateful.  I've looked through the forums and tried a couple of things, but nothing is working.  Any help is greatly appreciated.

---

### Post by scxtt on 2007-03-02
what does "sudo /sbin/ifconfig" return?
do you use DHCP or a static ip?

we're not talking about wireless are we?

---

### Post by Newbie1Kenobi on 2007-03-02
Thanks for the quick reply.

I use DHCP, and I'm not talking wireless..

I get 
eth0
Link encap: ethernet HWaddr 00:E0:4C:E6:7C:8C
UP BROADCAST MULTICAST  MTU: 1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
Interrupt:193 Base address:0xe400

lo
Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU:16436  Metric:1
RX packets:512 errors:0 dropped:0 overruns:0 frame:0
TX packets:512 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:36553 (35.6 KiB) TX bytes: 36553 (35.6 Kib)

---

### Post by scxtt on 2007-03-02
as far as i know, you need some sort of DHCP client (server?) running, i don't use DHCP myself - so i'm not sure what you'd need to do (it might be really simple, not sure) ...

cause it looks like eth0 is up, it just doesn't have an IP associated w/ it ...

i could probably guide you through setting up a static IP if you want, but as far as DHCP goes all i can really say is see if installing some things "sudo {apt-get / aptitude} search dhcp" returns helps ...

---

### Post by Newbie1Kenobi on 2007-03-02
If at all possible, I'd like DHCP.  My router is set up for that, I know it wouldn't affect me if I got a static IP address, I'm stubborn.  I'll try the commands you suggested...do I type that in as one command, exactly, or is it several that I can try?  Thanks again.

If the ethernet is enabled, shouldn't the light be liut up on the tower?  It isn't, so maybe I need a new ethernet cable?  Could it really be that simple?

---

### Post by scxtt on 2007-03-02
looks to me like the only problem is the lack of an IP assoc. w/ eth0 ... you could go static, then back to DHCP if static works, to rule that out ...

you can use either:

sudo apt-get search dhcp
sudo aptitude search dhcp

i just don't know if you use 1 or the other :)

---

### Post by PilotJLR on 2007-03-02
There is no need to add a dhcp server if one already exists on the router.

What happens if you do this:
```

sudo dhclient eth0

```

---

### Post by Newbie1Kenobi on 2007-03-02
sudo aptitude search dhcp got me this

i   dhcp3-client                          -DHCP client
i   dhcp3-common                     -Common files used by all the dhcp3* package

IS this good or bad?  If it is relatively easy to set up a static IP, I'm willing to try that, too.  Thanks for your help.

---

### Post by Ripfox on 2007-03-02
This may sound simple, but did you try system/administration/networking

and set the wired connection for DHCP?

---

### Post by Newbie1Kenobi on 2007-03-02
Pilot, when I ran the command you suggested I got this:

Listening on LPF/eth0/00:E0:4C:E6:7C:8C
Sending on LPF/eth0/00:E0:4C:E6:7C:8C
 Sending on Socket/Fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

It repeated that a few times, changing only the interval then I got:
 No DHCPOFFERS received
No working leases in persistent database - sleeping

---

### Post by Newbie1Kenobi on 2007-03-02
[quote="ripfox"]This may sound simple, but did you try system/administration/networking

and set the wired connection for DHCP?[/quote]

Yup.  If you guys are thinking "I wonder if it's x, but then think it is too stupid, go ahead and ask.  This is probably a very simple error on my part.  I'm brand new to Ubuntu, so maybe I haven't names something properly.  Thanks for all your help.

---

### Post by PilotJLR on 2007-03-02
You don't need to install anything else... the lack of a DHCP offer being received is more important.

Have you ever used this computer (cabled as it is) on a network before? If you dual boot, then does it work on the internet with the other OS?
Also, is the network cable connected directly from your machine to the switch port on the router?

And - does the router's DHCP server work right now on any other computers or devices that you may have?

---

### Post by Newbie1Kenobi on 2007-03-02
No, this is the first time I've had this computer hooked up to the network and it is strictly Ubuntu. It's new, only in the sense that I just got enough parts together to power it up.  I have two other computers connected to the router and all computers are hardwired into the router.  

So if understand this all so far, the Ethernet port on my computer is working, but for some reason there is no answer at the router...could it be a bad cable?

---

### Post by scxtt on 2007-03-02
before you start replacing hardware (even just a cable), i'd go static 1st just to make sure you can get a working connection - that's just me tho :)

---

### Post by Newbie1Kenobi on 2007-03-02
Oaky...how do I do that?

---

### Post by scxtt on 2007-03-02
sudo vi /etc/networking/interfaces

add (or edit it to) the following (your IPs might be different):

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1

then do a "sudo ifdown eth0" followed by "sudo ifup eth0"

you could probably use a GUI tool too {KDE and Gnome both have one} ... run "sudo /sbin/ifconfig" again and see if eth0 has an IP :)

---

### Post by Newbie1Kenobi on 2007-03-02
Yup eth0 has the IP address I assigned it.  Haven't tried to go online with ityet..will do that and post back.

---

### Post by scxtt on 2007-03-02
if it doesn't work, quite possibly a nameserver issue ... i get those from my router, then enter them in /etc/resolv.conf ...

nameserver <IP of nameserver>
nameserver <IP of nameserver>

---

### Post by Newbie1Kenobi on 2007-03-02
And I can't get online.  Also, I noticed after the sudo ifdown eth0 I got the message SIOCADDRT: Netwrok is unreachable.

---

### Post by Newbie1Kenobi on 2007-03-02
Where would I get that from my router?  The nameserver, that is.

---

### Post by scxtt on 2007-03-02
every router is different, but i can see mine in a "status" tab ... at worst, your ISP would have to give it to you ...

do you know the IP of the router?  you should be able to connect to it via a browser even if the nameservers aren't set ...

---

### Post by Newbie1Kenobi on 2007-03-02
I think this is what you meant.
LAN IP Address: 192.168.0.1 
Network Mask: 255.255.255.0 
DHCP Server: ON 
 

That was in the Status tab of my router.

---

### Post by scxtt on 2007-03-02
like i said, all routers are different - i see this:

IP Address: <my outside IP>
   Subnet Mask: 255.255.248.0 
   Default Gateway: <my default outside IP gateway>
   DNS: <DNS #1>
<DNS #2>
<DNS #3 (empty)>
   DHCP Remaining Time: 3 days 15:45:28

your router should be able to get the nameservers (DNS) from your modem and AFAIK you should be able to see them (somewhere) via your router's web interface ... i've had access to 2 diff. linksys routers and this is the case for them both ...

---

### Post by Newbie1Kenobi on 2007-03-02
I'm not quite following you.  I've got my router address 192.168.0.1, my outside internet address, and my subnet mask 255.255.255.0.  Are there other terms to look for that may be used in my router.  Also, I tried to ping my linux computer from the one I'm on now.  It couldn't reach it.  To me, that suggests bad cable.  The Linux computer can't reach my Windows one and vice versa.  My Windows computer works fine through the router.  Maybe I've just got a tunnel vision.  Still, I only need about 25' of Ethernet cable, which is about 10.00.  I think I'll pick some up tomorrow.  Is there anything else you want me to try tonight?  I'll look around in my router some more, bu tI'm stil not entirely clear on what you're looking for.  Thanks for all your help and patience so far.

---

### Post by scxtt on 2007-03-03
any box that has a working internet connection should be able to "tell" you your DNS servers ... 

take a look on your windows box at that working connection and you should be able to get the DNS servers from clicking on "details" in "connection status" ...

also, what's your **/etc/networking/interfaces** look like?

i'd swap out a "working cable" before laying down cash on another one when you're not sure it's the problem ...

---

### Post by Newbie1Kenobi on 2007-03-03
One last stab at this DNS thing.  In my router, under DNS, I've got "Automatically obtain"  checked. upElsewhere under backup DNS, there are two potential back DNS addresses, they are blank.

I actually replaced the cable running from my modem to my router and lost all internet connections.  I left it alone for five minutes to give the connection a chance to re-establish itself.  It didn't.  When I went to unplug it, it did light up again.  I may try that switch a few more times.  The cable I'm using to connect my Linux computer to the router is a homeade one I got from a friend.  It's been in my closet for a few months and seems thinner than regular network cable.  Anyways, I think I'll call it a night for this stuff, I'm sure we're both getting frusterated.  Thanks for your help...hopefully tomorrow will bring the Internet to my Ubuntu.  :)

---

### Post by PilotJLR on 2007-03-03
We really need to put this DNS stuff aside; that is pointless without dhcp offers.

Could you use a known working Cat5 cable (such as router - modem) to connect the router's LAN PORT to the ubuntu box? Has to be a LAN port on the router, not the "Wan" or "Internet" port. Once you do that, go to the ubuntu box and do this once more:
```

sudo ifconfig eth0 up
sudo dhclient eth0

```
And then let's see what happens. Presuming the router and dhcp server work (as they have been), this should be successful if the cable is good.

---

### Post by Newbie1Kenobi on 2007-03-03
Well, it turned out to be the cable after all.  I pluged in the new one, and was online in a few minutes.  Is there another thread or can someone point me to a page that has some useful downloads, ie firewalls, etc?  Thanks for all the help and patience!

---

### Post by Ripfox on 2007-03-23
firestarter...sudo aptitude install firestarter

---

