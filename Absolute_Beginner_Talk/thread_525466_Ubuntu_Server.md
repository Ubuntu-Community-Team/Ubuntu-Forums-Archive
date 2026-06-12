---
title: "Ubuntu Server"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by serfczar on 2007-08-14
I'm almost certain the reason why I cannot download any updates with my ubuntu server is that My network card drivers are not installed.

I found the file for the linux driver at a website. (here it is on my server, [http://www.techflash.frih.net/ubuntu/FastEthernet.zip](http://www.techflash.frih.net/ubuntu/FastEthernet.zip))

how do I install these drivers for my network card?

I ran lspci and it recognized my card.
I ran ip addr

eth0: <NO-CARRIER, BROADCAST, MULTICAST, UP> mtu 150 qdisc pfifio-fast qlen 100
inet 192.168.1.5/24 brd 192.168.1.255 scope global eth0
valid lft forever preffered-lft forever

I don't know where it is getting 192.168.1.255 from because that isn't anything on my network

My network is like this... DSL Modem/Router >>>Switch >>>> ubuntu server
All direct wired.

The DSL Modem/Router is 192.168.1.1 the switch is 192.168.1.5

---

### Post by yellowband on 2007-08-14
hello

how did you come to this determination?  ubuntu is pretty good at detecting a lot of NIC right out of the box.

what version of ubuntu are you using?  server or desktop?  commandline or gui?

more importantly what does ifconfig print out for you?

can you ping any addresses on your network or the internet?  

maybe post your ifconfig output and we can help from there.

---

### Post by serfczar on 2007-08-14
This is a server as stated above CLI V7.04, I cannot ping google.com, I cannot ping 192.168.1.1(Destination host unreachable)  ifconfig prints out...


eth0 link encap:ethernet
hw addr 00:12:17:58:1D:0B
inet addr: 192.168.1.5 Bcast 192.168.1.255 mask 255.255.255.0
Inet6 addr: fe 80:212:17ft:fe58:1d0b/64 scope Link

UP Broadcast Multicast MTY:1500 metric:1
RX Packets: 0 errors: 0 dropped: 0 overruns:0 frame: 0
TX Packets: 0 errors: 6 dropped: 0 overruns:0 carrier: 12

RX bytes: 0(0.0b) TX bytes:0 (0.0b)
Interrupt: 11 Base address: 0xec00


Thanks for your help.

---

### Post by az on 2007-08-14
Are you connecting to your switch using DHCP?

Also, post the result of

dmesg|grep eth

---

### Post by yellowband on 2007-08-14
hmm you might be right about the missing drivers, maybe somebody else can comment.

looks like your eth0 has the i address of your router though....

try givng your network card its own ip address:

ifconfig eth0 192.168.1.100 (or whatever address you intended).

---

### Post by Alterax on 2007-08-14
You're coming up with a class 'C' address, so that tells us two things right off the bat:
--Your Ubuntu installation DOES recognize your network card (otherwise it would not assign it)
--Your Ubuntu server is getting its address via DHCP, more than likely from the router.  If you can't get out, the information passed from the DHCP server on the router is wrong.

This means either the IP range is not getting routed out, or that DNS is not resolving the names properly.  This can be resolved either through setting a DNS server manually, or changing to a static IP address.  Since the latter involves the former, we will start with setting the DNS address manually.

Find out what the DNS servers are for your network from one of your other machines.  Then you will need to edit /etc/resolv.conf

sudo nano /etc/resolv.conf

and change it to this line:

nameserver (IP address of the DNS server, without parenthesis)

Then save it with (CTRL-X) then Y [ENTER].
Next, restart the network stack with:

sudo /etc/init.d/networking restart 

(This will take a minute or two)
=============================================================================
TEST TO SEE IF IT WORKS, SUCH AS BY USING:
ping [www.google.com](www.google.com)  (or some other site)
If it works, you're done.  No need to proceed.
=============================================================================


If this doesn't work, we can safely assume that the IP address should be changed to a static one:

Grab the IP information from one of your other installations, and set this manually in /etc/network/interfaces using an open IP address that IS in your network.  I am assuming that your card is eth0; change as necessary for your own situation:

sudo nano  /etc/network/interfaces
change the lines from:
iface eth0 inet dhcp
to read as follows:

iface eth0 inet static
address  (whatever the new IP address should be, without parenthesis)
netmask (Whatever the subnet mask should be, without parenthesis)
gateway  (The IP address of the router or gateway, without parenthesis)

Then save it with (CTRL-X) then Y [ENTER].

Restart the networking stack again with:
sudo /etc/init.d/networking restart

---

### Post by serfczar on 2007-08-14
No, I have dhcp turned off, I put some settings in when I installed the server. I believe it asked for the gateway, i put in 192.168.1.3, and it asked for the subnet mask and i put in 255.255.255.0, and it asked for it's ip and i put in 192.168.1.5

dmesg|grep eth -----------


eth0: ADMtek comet rev17 at Port 0xec00, 00:12:7:58:1D:0B, IRQ 11

eth0: no IPv6 routers present.


Come to think of it, It asked me for a nameserver and I didn't know what to put, so i just put it the same as gateway.

---

### Post by nvrpunk on 2007-08-14
Well, try ifconfig -a or ifconfig --all.  

It is possible your firewire is being pulled as eth0.  Happens to me.... and..... it even gives it a class C address :P

Anyhow my nic is eth1 because of this, this may also be your problem :)

---

### Post by serfczar on 2007-08-14
I do not have a firewire port. I have two usb, and two serial, this is a rather old machine we are working with here. intel celeron 1.4GHZ socket 3something

---

### Post by Alterax on 2007-08-14
"Come to think of it, It asked me for a nameserver and I didn't know what to put, so i just put it the same as gateway"

Bingo!  I think we have found the problem; try pinging this address:  216.239.51.99
If this succeeds, you just need to set up the DNS address for name resolution.  Check your other systems for the DNS address they look to, and put this into /etc/resolv.conf as I mentioned above.
(No need to go on to static IP setting, as you've already done it.)

--Alterax

---

### Post by az on 2007-08-14
Try

sudo ifdown eth0
 
and then

sudo dhclient eth0

See if that can connect.  If that works, then you have a configuration problem.  (I am assuming your router/switch provides a dhcp server..)

---

### Post by serfczar on 2007-08-14
still says unreachable...
maybe i put all the settings in wrong...

my switch says it is 192.168.1.3
subnet mask is 255.255.255.0

.... crap i just realized i do have dhcp enabled. but i think i put in a wrong setting to mix with the dhcp

with those ip's what should i set it my config to?

i also just recognized that none of those blinky lights on the back are working... dhclient eth0 didn't work

on my windows machines when the blinky lights on the network card aren't working that usually tells me that the driver is not installed.

---

### Post by Alterax on 2007-08-14
If 1.3 is the switch's address, don't point the gateway to it.  The switch's IP address is just for administering the switch; you need to set the gateway address to the router, so it can push your requests out to the 'Net.

Try setting it as a static (see above).  Find out what IP addresses your machines are and put one that is in their range as the new machine's IP address (If your netmask is 255.255.255.0 any number between 1 and 254 that isn't used is fine in the last set of numbers).  Set the gateway and netmask, and nameserver/DNS server the same as your other machines.

--Alterax

---

### Post by Alterax on 2007-08-14
If the lights aren't blinking, you don't have a physical connection.  (If they are solid or blinking, you do, although solid tends to mean that there's a lot of traffic trying to go through).   Also make sure you aren't using a crossover cable.

sudo ifconfig eth0 up

Failing that, swap the cable with a known working one and see if it lights up.

---

### Post by serfczar on 2007-08-14
> **Alterax said:**
> If the lights aren't blinking, you don't have a physical connection.  (If they are solid or blinking, you do, although solid tends to mean that there's a lot of traffic trying to go through).   Also make sure you aren't using a crossover cable.

sudo ifconfig eth0 up

Failing that, swap the cable with a known working one and see if it lights up.


I know this cable works. 1 light is supposed to light up even if a cable isn't connected right?

---

### Post by serfczar on 2007-08-14
> **serfczar said:**
> I know this cable works. 1 light is supposed to light up even if a cable isn't connected right?

dangit i checked all the connections and it was loose... omG!! i'll see how things go now and post back.

---

### Post by serfczar on 2007-08-14
ok cable connected now, and the problem offically exists :D i can't ping my switch.. i'll try some of you guys suggestions and get back to you.

---

### Post by serfczar on 2007-08-14
thanks guys for all your help i got it working now!

---

### Post by Alterax on 2007-08-14
Glad to hear it.  Enjoy!

--A

---

