---
title: "Internet Sharing..."
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by suixin on 2005-08-14
First of all i have to apologize, I'm sure i can get the answer somewhere frm the internet, ive search for 2 days for this question and i'm really exhauted for being disapointed, pls pls help me team, i'll be vry appreciate upon the support, thanks..

U guys know about internet sharing in Windows XP rite?
the setup just need to run a wizard to determine the realted PC....
now the situation is:

Ubuntu (main Pc which connect to the broadband)
Window XP (another PC which connect to the internet thru Ubuntu)

no router, just linkin between 2 network cards
network card is fine and can be activate (dhp0/dhp1)

I hope ive make the situation clear and easy to understand

So wht should i do to let the Win XP share the internet connection with Ubuntu?

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=suixin]First of all i have to apologize, I'm sure i can get the answer somewhere frm the internet, ive search for 2 days for this question and i'm really exhauted for being disapointed, pls pls help me team, i'll be vry appreciate upon the support, thanks..

U guys know about internet sharing in Windows XP rite?
the setup just need to run a wizard to determine the realted PC....
now the situation is:

Ubuntu (main Pc which connect to the broadband)
Window XP (another PC which connect to the internet thru Ubuntu)

no router, just linkin between 2 network cards
network card is fine and can be activate (dhp0/dhp1)

I hope ive make the situation clear and easy to understand

So wht should i do to let the Win XP share the internet connection with Ubuntu?[/QUOTE]

First step, you need to turn on IP forwarding:
```
$ sudo sh
# echo "1" > /proc/sys/net/ipv4/ip_forward
```

Next step, you need to set up your routing table so your LAN traffic goes to the LAN and the Internet traffic goes to the Internet.  I am going to make some assumptions here that you will have to correct if I am wrong:
Assuming:
dhp0 is your LAN network card.
dhp1 is your Internet network card.
You LAN network is 192.168.0.0 netmask 255.255.255.0.

If the above assumptions are valid, and starting with an empty routing table:
```
$ sudo route add -net 192.168.0.0 netmask 255.255.255.0 dev dhp0
$ sudo route add -net 0.0.0.0 netmask 255.255.255.255 dev dhp1

```

Finally, you have to set the default route (sometimes called the gatweway or default gateway) on the WinXP machine to your Ubuntu machine's IP address on dhp0.

I realize this is somewhat technical for the newbie section, so if you are confused on certain points, feel free to ask questions.

---

### Post by Nequeo on 2005-08-14
> 

First step, you need to turn on IP forwarding:

```

$ sudo sh 
# echo "1" > /proc/sys/net/ipv4/ip_forward

```


This works, but every time you restart your Ubuntu machine, you will need to do it all over again. Instead, I woud do it like this:

```

$ sudo gedit /etc/network/options

```
The very first line will say "ip_forward=no". Change 'no' to 'yes', save, and you're done!

You'll still need to follow the rest of the instructions in cwaldbieser's post, though. And make sure the Windows XP machine is on the same subnet, and it's gateway is set to the IP address of your LAN card in the Ubuntu machine. 

(I'm pretty sure I remember needing to do something with IP-tables, on the Ubuntu box, too. I'll look it up for you if you're still having problems after this.)

In any case, hang in there. It's not exactly simple, but once you get it working it's much more flexible that Window's internet sharing wizard. And you learn a lot in the process :)

---

### Post by cwaldbieser on 2005-08-14
[QUOTE=Nequeo]
(I'm pretty sure I remember needing to do something with IP-tables, on the Ubuntu box, too. I'll look it up for you if you're still having problems after this.)
[/QUOTE]
Yeah, my bad!  I forgot you have to do IP Masquerading on the Ubuntu box.  (I'm spoiled because I am just using a hardware router).

If you have a firewall like Firestarter running, then it will have instructions for how to do the IP Masquerading.  Otherwise...

If the device that represents your network card to the Internet is eth1, then the following commands should do the trick:

```
$ sudo iptables -t nat -P POSTROUTING DROP
$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

The first command sets the default policy of the chain to drop all packets.  This only goes into affect if none of the rules in the chain match the packet.
The rule we add to the chain specifies that any packets that are routed to the eth1 device need to be masqueraded.  

This means your Ubuntu box will doctor the packet so that a machine on the Internet thinks that the packet originated from the Ubuntu box.  Your Ubuntu PC will track the connection, so if a machine on the Internet responds, it will send the packets back to the machine on the LAN that originally sent them.

These commands need to be put in a startup script somewhere if you want them to be in effect each time you boot up-- I am a little fuzzy where that should be off the top of my head.  You also wouldn't use "sudo" with them because they'd already be running as the root user at startup time.

It is a lot to digest all at once-- Firewalls like Firestarter or Guarddog + Guidedog  usually make it a little easier on you from a conceptual viewpoint.

---

### Post by suixin on 2005-08-15
haha...sry...
i dun think i can get it
i follow exactly wht u gave (the coding)
turns out my Ubuntu cant online at the end :P

i'm still a newbie, need sum spoon feeding :P

becos within windows XP we do not need to set IP
so this is the part i'm confusing..
:(

---

### Post by Nequeo on 2005-08-15
No worries,

We're happy to spoonfeed... But we need to know a little bit more information before we can give you exact instructions.

I'm guessing your internet stopped working because you just entered the commands cwaldbieser gave you without stopping to see if the numbers were right. :) But even if you did, more information never hurts. 

First thing I'd like you to do is restart your Ubuntu machine (if you haven't already!), which hopefully should get the internet working on it again. Then type in the following commands, one by one, and copy the output you get from each of them into a message for us.
```

ifconfig
route
cat /etc/resolv.conf

```

Cheers,

---

### Post by suixin on 2005-08-15
[QUOTE=Nequeo]No worries,

We're happy to spoonfeed... But we need to know a little bit more information before we can give you exact instructions.

I'm guessing your internet stopped working because you just entered the commands cwaldbieser gave you without stopping to see if the numbers were right. :) But even if you did, more information never hurts. 

First thing I'd like you to do is restart your Ubuntu machine (if you haven't already!), which hopefully should get the internet working on it again. Then type in the following commands, one by one, and copy the output you get from each of them into a message for us.
```

ifconfig
route
cat /etc/resolv.conf

```

Cheers,[/QUOTE]


[COLOR=Blue]king@Darling:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:C0:D3:07
          inet6 addr: fe80::211:d8ff:fec0:d307/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3477 (3.3 KiB)  TX bytes:2088 (2.0 KiB)
          Interrupt:22 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:11:D8:C0:E6:43
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fec0:e643/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:235012 (229.5 KiB)  TX bytes:77401 (75.5 KiB)
          Interrupt:17 Memory:d1000000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43384 (42.3 KiB)  TX bytes:43384 (42.3 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:219.95.40.242  P-t-P:219.93.218.177  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:226550 (221.2 KiB)  TX bytes:66279 (64.7 KiB)

king@Darling:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
219.93.218.177  *               255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         219.93.218.177  0.0.0.0         UG    0      0        0 ppp0
king@Darling:~$ cat /etc/resolv.conf
nameserver 202.188.0.133
nameserver 202.188.1.5[/COLOR]


feel so touch, thanks guy, i'll provide watever u guys need, thanks :)

---

### Post by Nequeo on 2005-08-15
Okay... try this.

On your Ubuntu computer, type in these commands:

```

$ sudo iptables -t nat -P POSTROUTING DROP
$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

Then go to the Windows XP computer. Click Start--->Control Panel--->Network

Right click on the LAN network connection and select Properties. Then find the TCP/IP check box, select it, then click 'Properties' button next to it. 

If the 'obtain IP address automatically' button is clicked, change it over to manual. Do the same for the DNS settings below it. Then, enter these following settings:

IP: 192.168.1.3
Subnet Mask: 255.255.255.0
Gateway; 192.168.1.2

Primary DNS: 202.188.0.133
Secondary DNS: 202.188.1.5

Then click 'okay'. Then click 'close' on the network screen.

Then try and access the internet! It if doesn't work, restart the Windows computer, and try again. If it still doesn't work, we'll go from there. If it DOES work, let us know that too... because we still need to create a start-up script. Otherwise, you'll lose internet access on the XP machine any time the Ubuntu machine restarts. 
Cheers,

---

### Post by suixin on 2005-08-16
[QUOTE=Nequeo]Okay... try this.

On your Ubuntu computer, type in these commands:

```

$ sudo iptables -t nat -P POSTROUTING DROP
$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

Then go to the Windows XP computer. Click Start--->Control Panel--->Network

Right click on the LAN network connection and select Properties. Then find the TCP/IP check box, select it, then click 'Properties' button next to it. 

If the 'obtain IP address automatically' button is clicked, change it over to manual. Do the same for the DNS settings below it. Then, enter these following settings:

IP: 192.168.1.3
Subnet Mask: 255.255.255.0
Gateway; 192.168.1.2

Primary DNS: 202.188.0.133
Secondary DNS: 202.188.1.5

Then click 'okay'. Then click 'close' on the network screen.

Then try and access the internet! It if doesn't work, restart the Windows computer, and try again. If it still doesn't work, we'll go from there. If it DOES work, let us know that too... because we still need to create a start-up script. Otherwise, you'll lose internet access on the XP machine any time the Ubuntu machine restarts. 
Cheers,[/QUOTE]



thanks alot!!!
too bad i'm now in Bangkok(jst arrive), and will go back to my country on next monday
so pls pls pls dun blame me for late reply, i swear i wan to do the testing asap more than any ppl
pls keep giving me support when i get back
doing the testing will be the 1st thing in my list when i get back :)

---

### Post by Nequeo on 2005-08-16
No worries.

Enjoy the trip, and we'll see you when you get back.

Cheers,

---

### Post by jrev on 2005-08-16
I have done a practical step by step guide (in french ) for the beginners (me)
if necessary I will turn it into english 
it's 2 pages for setting the network 
2 pages to share the web connection 
and 2 pages to share files and printer 
but I need some help with the last 2 pages
 :|

---

### Post by jrev on 2005-08-17
Hi Nequeo or cwaldbieser ,

Could you tell me how I can understand the routing table on my gateway PC :

jean@aspire:~$ sudo route
Password:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
1-c-1.tnt01.par *               255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
default         1-c-1.tnt01.par 0.0.0.0         UG    0      0        0 ppp0

Thanks

---

### Post by sirro on 2005-08-17
ive been looking for this myself......noob that i am.....i want to set my machine up the same but there isnt any tutorials i could find......so can i/we/us/you make it into a step by step how-to ? or get the translation of jrev's please  :) 

only thing is i dont want a firewall......plus if we leave that out it makes it simpler....maybe

---

### Post by jrev on 2005-08-17
You can have it in openoffice format or here in HTML now :

thanks



2 Sharing your Internet connection



This chapter is a follow up of “1 Build up your local network on Ubuntu 5.04”

In order to use the ICS (internet connexion sharing) on one of your network machine, the transmission must be OK (ping OK)

We will call this machine the ICS server. We will be able to call the other PC by their name instead of their IP address

Perequisite : The internet connection comes through the eth1 card (ADSL) or through an external modem 56 Kbs via ppp0. The simplest local network is : 2 machines linked via a crossed cable to the Ethernet card.

By system –> administration –> Networking , select “Ethernet connection/ the interface eth0 is not active”, then select “Properties”





1. Connection sharing configuration (ICS)

Here is the commands to type on the ICS machine, to activate Internet sharing :

sudo bash
# echo 1 >/proc/sys/net/ipv4/ip_forward 

# iptables -t nat -A POSTROUTING -s 192.168.10.0/24 -o eth1 -j MASQUERADE 
Check now that the contents of the ip_forward file is “1” :
# cat /proc/sys/net/ipv4/ip_forward

This iptables command allows all the other network machines to reach Internet with the ICS machine identity. That's what we call NAT (Network Translation Address) or IP address masking (Masquerading). 
but this sharing validation will not last after the end of the session 
To get round this feature, we have to pass the following command : 
sudo gedit /etc/network/options 
and change the line “ip-forward=no” to “ip-forward=yes”


Now that we have allocated our local IP addresses and activated the ICS all our machines are able to go on the Net, but only on the basic way :

Try the command ping 212.27.33.233, and you will see that the web site which is not on your local network will answer your request

In order to be able to reach other addresses by their URL (Uniform Resource Locator)

e.g. [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/) we will make some change in the /etc/hosts file





2. Modify the /etc/hosts file

We will now give names to our local machines. Those machines must know for example that PC number 168.10.2 is named toshiba. You have to modify this /etc/hosts file in all your machines



Here is the modified /etc/hosts file on toshiba :

127.0.0.1       localhost.localdomain   localhost toshiba
192.168.10.1    aspire

We have indicated on line 2 the name of the ICS gateway 

# the following lines must not be altered

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

The gateway /etc/hosts file on ICS aspire will be different :

127.0.0.1       localhost.localdomain   localhost aspire
192.168.10.2    toshiba

...from now on, your machines can be called by their name : 
$ ping toshiba will provide an answer  

3. DNS configuration

Each PC connected to the Internet has registered the IP addresses of the nameserver of the ISP (Internet Service Provider)

So we have to make the change allowing the local network PC's to be able to type :

ping ubuntu-fr.org instead of ping 212.27.33.233



This change will allow all the local network machines browser to reach the right site from its URL

We will copy the contents of the /etc/resolv.conf file of the ICS machine when it's connected to the Internet



jean@aspire:~$ cat /etc/resolv.conf

nameserver 213.36.80.1

domain ubuntu
The content of the ICS /etc/resolv.conf file is the address of the nameserver belonging to the ISP.

Only copy this content into the /etc/resolv.conf files of all the other machines.



Now we can reboot the ICS machine, connect it to the Net then open the toshiba browser and mail client.

Enjoy ...

the picture didn't follow but anyway it was in french sorry about it ...

---

### Post by xmastree on 2005-08-17
I'm interested in this, I'm building a ubuntu powered router, and last time I tried to get it to work, it didn't.

It can get on the net itself, but another machine couldn't use it as a gateway. Couldn't even ping it. I had one NIC set to DHCP for the uplink, and one static, connected via a (tested) crossover cable to another box.

jrev, if you can provide a how-to, even not in perfect English, I'll test it for being idiot-proof, as I am the idiot you are looking for...  :grin:

---

### Post by az on 2005-08-17
I would suggest that you guys start another thread somewhere else.  The absolute beginnier forum should host advice like "use firestarter"  

Someone who does not know linux and who thinks an absolute beginner must run iptables commands from the command line will run away and never come back.
The whole point is to make absolute beginnners feel comfortable.  Let's please give one simple option, and point them elsewhere (to other threads) for more complex solutions.

I am not sayting that any of the advice is wrong, just scary for the type of user we are trying to attract, here.

(just my two cents)

---

### Post by jrev on 2005-08-17
Hi azz,

I understand your point...
I would appreciate a place where we can exchange documents in OOO format so we can correct our mistakes 

Had I found the right tuto in one page (that's all it needs)  I would not have attempted to make one myself with two ...

---

### Post by jrev on 2005-08-17
[QUOTE=xmastree]I'm interested in this, I'm building a ubuntu powered router, and last time I tried to get it to work, it didn't.

It can get on the net itself, but another machine couldn't use it as a gateway. Couldn't even ping it. I had one NIC set to DHCP for the uplink, and one static, connected via a (tested) crossover cable to another box.

jrev, if you can provide a how-to, even not in perfect English, I'll test it for being idiot-proof, as I am the idiot you are looking for...  :grin:[/QUOTE]

Hi xmastree,
Thanks a lot,

I was in Manilla where my son was born 34 years ago, busy building the telecom center of the airport ...
Things have changed since ...

---

### Post by Brunellus on 2005-08-17
[QUOTE=azz]I would suggest that you guys start another thread somewhere else.  The absolute beginnier forum should host advice like "use firestarter"  

Someone who does not know linux and who thinks an absolute beginner must run iptables commands from the command line will run away and never come back.
The whole point is to make absolute beginnners feel comfortable.  Let's please give one simple option, and point them elsewhere (to other threads) for more complex solutions.

I am not sayting that any of the advice is wrong, just scary for the type of user we are trying to attract, here.

(just my two cents)[/QUOTE]
 People are interpreting "absolute beginners" to mean "absolute beginners TO UBUNTU" rather than "total noob"...

---

### Post by az on 2005-08-17
[QUOTE=jrev]Hi azz,

I understand your point...
I would appreciate a place where we can exchange documents in OOO format so we can correct our mistakes 

Had I found the right tuto in one page (that's all it needs)  I would not have attempted to make one myself with two ...[/QUOTE]

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

wiki.ubuntu.com/forum

It is not in OOO format, but it is viewable and editable by everyone online.



"People are interpreting "absolute beginners" to mean "absolute beginners TO UBUNTU" rather than "total noob"..."

Which is fine, too.  We tried to be more strict when this sectionwas first opened, but it is very very hard to keep on top of everything.  It is a very popular section and that is a good thing.

I am not scolding anybody, I just want to keep things into perspective.  I think this issue can influence the way non-experts feel about linux - more so than in the other sections.  So I think it is more important to not give people the wrong impression here.

Also, if someone feels they are too inexperienced to ask a question in the server talk section, you are probably wrong.  There are questions from all levels of expertise, there.  Nobody was born an expert.

---

### Post by sirro on 2005-08-18
[QUOTE=azz]I would suggest that you guys start another thread somewhere else.  The absolute beginnier forum should host advice like "use firestarter"  

Someone who does not know linux and who thinks an absolute beginner must run iptables commands from the command line will run away and never come back.
The whole point is to make absolute beginnners feel comfortable.  Let's please give one simple option, and point them elsewhere (to other threads) for more complex solutions.

I am not sayting that any of the advice is wrong, just scary for the type of user we are trying to attract, here.

(just my two cents)[/QUOTE]

i do agree in some ways....but from my experience the people who go to linux are more the people who are ....more technicly minded....if i can put it that way.....
the only thing i see as a rule for this section is go STEP BY STEP......dont assume i know where things are cause i dont as a rule.....and also ipv4 isnt a directory on my pc..so i looked in synaptic for it and cant find it...s o ....thats the end of me ](*,) 

azz you said use firestarter. will that do all this for me? if so i will do that...and find out where i can put trusted ip's :grin: 

thanx to all of you ......

---

### Post by sirro on 2005-08-22
bump.... ='(

---

### Post by suixin on 2005-08-23
[QUOTE=Nequeo]No worries.

Enjoy the trip, and we'll see you when you get back.

Cheers,[/QUOTE]

[COLOR=Red]$ sudo iptables -t nat -P POSTROUTING DROP[/COLOR]
[COLOR=Red]$ sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE[/COLOR]

BAck!!
erm.. after i've key in the command...the prob turns out my Ubuntu cant online too :P

[IMG]http://img376.imageshack.us/my.php?image=ubuntu4is.gif[/IMG] 
[IMG]http://img376.imageshack.us/my.php?image=xp3wo.gif[/IMG]

---

### Post by sirro on 2005-08-23
will firestarter do this for me?............oh did i mention i hate xp ....but im going back if this wont work.

---

### Post by sirro on 2005-08-28
thanx boys im back on the xp bandwagon :mad:  ](*,)

---

### Post by kagashe on 2005-08-30
[QUOTE=sirro]will firestarter do this for me?............oh did i mention i hate xp ....but im going back if this wont work.[/QUOTE]I have one Laptop connected to internet on which Ubuntu 5.04 is installed. I am using Firestarter as router on this machine. I have another desktop which is connected to the Laptop through LAN card and Win XP home is the OS on the desktop. I have set up the desktop to have static ip address of 192.168.0.2 and gateway as 192.168.0.1. I have set up the Laptop eth0 to have the static ip address of 192.168.0.1.

I am connecting the Laptop to internet through ppp0. The Firestarter has been set to connect to internet through ppp0 and local network through eth0. The Firestarter is working as router and I am able to surf the net on the desktop as well as the Laptop simultaneously.

If I had two network cards on the Laptop, I could have also configured the Laptop to connect to internet through eth0 and local network through eth1 through Firestarter.

Firestarter has very nice online documentation about this type of internet connection sharing here:
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Firestarter is available available through apt-get from the "universe" repository.

I totally agree with azz on this issue.

kagashe

---

