---
title: "PPPOE internet connection not working"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by GaryReggae on 2007-12-08
Hi there, I've decided to have another attempt at weaning myself off Windoze and giving Micro$oft the boot by giving Ubuntu another try - I installed Dapper Drake about a year or so ago and liked what I saw but in the end went back to Windoze because I have a lot of MS dependent software.  However, I recently heard about a thing called WINE that lets you run Windoze software from Linux and as my Windoze installation is living up to its name and going very slow again, I thought I'd have another bash at Ubuntu.

I found an old 20Gb HDD and installed it in my PC as an extra (slave drive) and installed the latest version of Ubuntu onto it (Gusty Gibbon) but I cannot connect to the internet with it.  If I remember rightly, it connected straight away last time with no need to change any settings as I just have an ADSL router but nothing happens now, if I type in (for example) [http://www.bbc.co.uk](http://www.bbc.co.uk), it just sits there and waits.  It's not the router itself as it works fine in Windoze, I am using it right now.

I read the HELP file in Ubuntu and it said to run sudo pppoeconf which I did and it asked a lot of questions, most of which I accepted the defaults for as reccomended except the username and password which I entered correctly.  It then said something about running plog if there were problems, so I did and this is what came up:

> me@mycompname:~$ plog
Dec  8 10:42:03 mycompname pppd[6170]: Plugin rp-pppoe.so loaded.
Dec  8 10:42:03 mycompname pppd[6170]: In file /etc/ppp/peers/dsl-provider: unrecognized option 'eth1'
Dec  8 10:44:17 mycompname pppd[6502]: Plugin rp-pppoe.so loaded.
Dec  8 10:44:17 mycompname pppd[6504]: pppd 2.4.4 started by root, uid 0
Dec  8 10:44:52 mycompname pppd[6504]: Timeout waiting for PADO packets
Dec  8 10:44:52 mycompname pppd[6504]: Unable to complete PPPoE Discovery
me@mycompname:~$ 


Yikes!  It refers to 'eth1' but I thought the convention is UNIX was to start device numbers from 0 so surely it should be 'eth0' as I only have one ethernet card?  

If anyone can help me, it would be much appreciated as a system with no internet is no use at all to me!  It's also a pain as if I want to visit this forum, I have to log off, start up Windoze and then go back into Ubuntu again (which seems to take ages to start up).  <Grumble> why is nothing ever simple?!

---

### Post by schmildo on 2007-12-09
HA, you sound like me.
ok,
I'm a bit of a linux noob, but I should know enough to get ou going if someone else doesnt help you first.

It looks like your router might be running a DHCP server. That would explain why you didn't have to configure anything last time. (DHCP servers give out IP addresses and other important stuff to computers on a network dynamically)

1) What the hell do they call it.. um.. what GUI are you using? I'm using Xubuntu Gutsy 7.10, there is also Ubuntu, and lots of others. (I know you said you were using ubuntu but i just wanted to be sure) I'm afriad I dont know how to configure it using the graphical interface, that would be the best solution for you.

2) I'm not sure how to configure DHCP in any flavour of ubuntu, but If nobody else gets arond to answering you in time I might be able to help you troubleshoot, (and maybe setup a static IP address)

You only need to stress about 4 settings with a static setup. (these are the four settings that DHCP 'automatically' discovers for you)
An IP address and IP mask for your PC, and
a gateway (your router's IP address) and a DNS server (usually provided by your internet service provider)

Jump into windows, go to the command prompt and type: [COLOR="DarkSlateBlue"]ipconfig /all[/COLOR]

it'll show you the ip address, subnet mask, default gateway and DNS settings. Get a piece of paper and write these four things down

if you go back to your unix machine, (irritating having to reboot when you don't know if its going to work huh?)

Take a look at mine; i've setup my Xubuntu machine with the static IP address of 192.168.0.199, my router's IP address is 192.168.0.194, I use a strange mask of 255.255.255.224, your's will probably be  something like 255.255.255.0. eth0 is my network card, and lo is the loopback, dont worry about the loopback.

**tim@lister:~$** [COLOR="DarkSlateBlue"]ifconfig[/COLOR]
[COLOR="Sienna"]eth0      Link encap:Ethernet  HWaddr 00:0D:61:7C:B3:83  
          inet addr:192.168.0.199  Bcast:192.168.0.223  Mask:255.255.255.224
          inet6 addr: fe80::20d:61ff:fe7c:b383/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60727541 (57.9 MB)  TX bytes:5286266 (5.0 MB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/COLOR]
You might find that your inet addr:is 169.254.x.x which indicates that your computer is set to use a DHCP server, but it couldnt find one.


There is a file called 'resolv.conf' located in /etc that stores the DNS server addresses (mine are from westnet) I'm using a program here called 'cat' it simply prints the file to the screen so you can see the contents of the file.

**tim@lister:~$** [COLOR="DarkSlateBlue"]cat /etc/resolv.conf[/COLOR]
[COLOR="Sienna"]nameserver 203.21.20.20
nameserver 203.10.1.9[/COLOR]

The other file that may need altering is below:

**tim@lister:~$** [COLOR="DarkSlateBlue"]cat /etc/network/interfaces[/COLOR] 
[COLOR="Sienna"]auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.199
netmask 255.255.255.224
gateway 192.168.0.194







auto eth0[/COLOR]

If you change these files you'll need to restart your networking services (kinda like the windows "repair this connection" option)


[COLOR="DarkSlateBlue"]/etc/init.d/networking restart[/COLOR]

So:
 1)Run the two 'cat' commands and give me an idea of what you see, (i dunno if you'll be able to save it to a usb or not, I think the usb needs to be formatted in FAT16 for both windows and unix to read them.

2) Lemme know what the windows machine says to ipconfig /all. (ie wha'ts the windows machines ip,mask,gateway & dns settings.

Good luck!

---

### Post by GaryReggae on 2007-12-09
Thanks for your reply.  Here is what ipconfig within Windows displays:

> 
Ethernet adapter Local Area Connection:

Connection-specfic DNS Suffix:
IP Address: 192.168.1.4
Subnet Mask:255.255.255.0
Default Gateway: 192.168.1.1


The default gateway's IP address is the actual IP address of my DSL router.

In Ubuntu (just the 'standard' GNOME desktop version of Gusty Gibbon), here are the results.  I have changed the IP addresses using the Network admin function in the GUI.  Luckily, Ubuntu lets me access my Windows drive so I can save files directly to that.  I always use FAT32 as I don't like NTFS.

> gaz@GAZ-Ubuntu2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:90:2C:75  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe90:2c75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1525 (1.4 KB)  TX bytes:6931 (6.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

gaz@GAZ-Ubuntu2:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
gaz@GAZ-Ubuntu2:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!



nameserver 192.168.1.1

It wouldn't let me edit those two files in /etc.  I opened them in the standard text editor but it said I don't have the permissions to save them.

Any further advice would be appreciated!

---

### Post by HereInOz on 2007-12-09
If you are using an ethernet modem/router, then you should not have to worry about PPPoE config on the linux machine - the modem/router will do that for you.

I would suspect a DNS issue.  If the modem/router is a D-Link, or a Netcomm, I know that some models of these do not pass DNS correctly, and although you will get an ip address assigned, and all that, the DNS resolution fails.  Different versions of Ubuntu behave differently in this regard.

One thing to try is to manually configure your network interface by setting a fixed IP address (192.168.1.101 would do) with a gateway address of 192.168.1.1, and the DNS addresses provided by your ISP.  You get to the network configuration via System > Administration > Network.

Try this and if it fails to work, then I most humbly apologise.

You will have to disable roaming mode in Network Manager to be able to manually configure the network interface.

---

### Post by rkd on 2007-12-09
As HereInOz said, if you are using a router, it could be that it is handling the username/password stuff for the PPPoE connection, and if so, it is a mistake to specify PPPoE in your Ubuntu network setup.  I don't have enough experience with DSL connections to tell you how to check in Windows to see whether it is handling the PPPoE username/password.  If you remember that it is, then you probably do have to set up Ubuntu to do that too.  If you remember that Windows is NOT doing the PPPoE username/password, then redo your Ubuntu setup and don't have it do the PPPoE stuff -- just have it find the network automatically or tell it to use DHCP to get the network stuff.  I'm new to Ubuntu and don't know all the ins and outs of configuration yet so I can't tell you exactly how to get it to work.  If you follow instructions for setting up Ubuntu using a router (assuming there are such directions), that could very well be all that you need to do.  I was under the impression that it would discover the router and set up to use DHCP automatically, but maybe it isn't quite so simple.

Manually configuring the addresses in Ubuntu might be okay for a test to see whether you can get it working, but if the modem is using DHCP to assign an address to your computer, it is possible it could pick a different address occasionally, and if your computer thinks it has a fixed address, the mismatch could cause a problem at that time.  So be careful with any fixed address configuration.  If you can get the DHCP stuff working, that is a better way to go.

On another point, you mentioned your intention to use WINE to let you run some Windows programs that you still need.  I just want to warn you that WINE works for some programs, but not for others, so if you have trouble getting one or more of your programs working, it might not be anything you are doing wrong.  The Windows environment is big, complex, and incompletely documented, so the WINE interface is incomplete.  Some things work; others don't.  There is a commercial product built on WINE named Crossover Office that I understand provides a somewhat more complete Windows environment (though still not complete) that you could try if you find WINE doesn't work for all of the programs you need.  There is another one, too, but I don't remember its name at the moment.  My point is just that the programs you want to use might not work with WINE, and that there are those two others that you could try if you run into that problem.

---

### Post by schmildo on 2007-12-09
I was hoping i'd be able to read a bit and come back with a magic answer, but it's not happening, I just don't know enough about PPPoE connections in linux.

but...

I agree with the other comments, its odd that you'd be requiring PPPoE to be configured by the hosts inside your network. Most people use either PPPoE or PPPoA, but it's normally configured inside your router because these protocols are suited to wide area networks, not LANs. (i'm using PPPoA for example between my router and my provider, but standard ethernet protocols inside my house)

If someone's accidentally lead you down the PPPoE path, then your troubles should be over, you can switch linux back to a standard setup.

clutching at straws here:
I was reading: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) which looks like what you may have read already, but the section on 'booting' refers to the order you have the lines in your 'interfaces' file. Its possible that the program is complaining about eth1 because it's not configured it yet, (what the heck is eth1 anyway? some kind of virtual interface?.... eth0 looks like a run-of-the-mill LAN card, which I can see that you've configured staticly)

If it's only a DNS issue then you should still be able to ping your router. Lets find out:
Go to the command line and type:
[COLOR="DarkSlateBlue"]ping 192.168.1.1[/COLOR]
It'll repeatedly give you responses, to shut it up hold down control+c.

Come to think of it; i must be blind, It seems you've told linux to use your router as a DNS server (you can do that) but I didn't see the printout of what DNS server your windows machine is using. Make sure you specified the '/all' at the end of the 'ipconfig /all' command, the DNS address should be directly below the ipaddress,mask and gateway settings i think. Otherwise I'll show you how to check it using windows.

If you are in unix and if you:
[COLOR="DarkSlateBlue"]ping 72.14.253.104[/COLOR]
and
[COLOR="DarkSlateBlue"]ping 209.131.36.158[/COLOR]

and if you get a response like:

**tim@lister:/etc/ppp/peers$**[COLOR="DarkSlateBlue"] ping 72.14.253.104[/COLOR]
[COLOR="Sienna"]PING 72.14.253.104 (72.14.253.104) 56(84) bytes of data.
64 bytes from 72.14.253.104: icmp_seq=1 ttl=243 time=190 ms
64 bytes from 72.14.253.104: icmp_seq=2 ttl=243 time=191 ms[/COLOR]

...then go and grab a beer and relax, it's just DNS stuffing you around. You'll have an answer very soon. Oh, yeah, if that works then you can actually stick that IP address into your browser window instead of the "http://www.blah.com" and load up internet websites, infact one of these ip addresses i've supplied is google, so you'll be able to browse the net and get back to this forum.


Lemme know if you have a standard ethernet port at the back of the computer, and if its plugged into the router... or if you have some other cabling setup, like USB or something.

Oh and I forgot to mention, you had problems editing those files because the computer didn't trust you, you gotta let it know who's boss by giving it the finger and saying "nah bro; i'm a SUPER USER!"

from the console if you want to edit a file as the super-duper-doody-doo-user just type 'sudo'
before the command.
eg.
[COLOR="DarkSlateBlue"]gedit somefile.txt[/COLOR] [COLOR="Magenta"]will open the file thinking you are just a boring run-of-the-mill user.[/COLOR]

but 

[COLOR="DarkSlateBlue"]sudo gedit somefile.txt[/COLOR] [COLOR="Magenta"]will open the file with 'root' access.[/COLOR]

Alot of the system files can only be modified by the root user or the system itself, this keeps you safe from hackers and yourself when you've had too much beer.

Speaking of beer, i'm going to grab one.

---

### Post by GaryReggae on 2007-12-10
Thanks for all yuor replies, I'm at work at the moment so not able to actually try anything on my home machine but I just want to clarify a few of the questions you have raised:

1.  The router itself deals with the username and password for my internet account which is why I was confused when I had to enter it into the PPPOE config utility.  I just type the router's IP address into the browser then I can log into the router's config system and amend all that but I don't think that is the problem.

2.  The router is connected to the PC by a standard Ethernet cable which is plugged into the motherboard's built in ethernet port, I think the network chipset (or whatever it's called) is Intel based.

3.  The router is a cheapo 'Guru' brand one.  With Windows and my previous installation of Dapper Drake, it just worked straight away without any need to configure the DHCP asettings.

When I get back home, I will try having a look at the ipconfig settings for DNS in Windows - I forgot it only displayed that if you add the /all switch to it!

It seems that the PPPOE stuff has clouded the matter somewhat although it didn't work before I meddled with that so it's not entirely to blame.

---

### Post by meborc on 2007-12-10
i am not sure if it will work, but you can set your router to "bridge" mode... meaning that it will not try to insert the login and password for ADSL itself.. but it would wait for the computer to do that... then the pppoeconf should set things up from ubuntu...

not sure, but you can try it

---

### Post by rkd on 2007-12-10
I'm pretty sure he shouldn't put the router in bridge mode.  Then he'd have to fiddle around to get the connection to work from Windows.

I don't know why the Ubuntu install didn't automatically find and set up the networking properly, but using pppoeconf was definitely the wrong thing to try.  I don't know enough to say how to do it, but the first thing that he needs to do is make sure the pppoeconf stuff is completely undone.  Is there a way to tell Ubuntu to completely forget everything it thinks it knows about the networking and start fresh? I think that is what he needs to do.  Perhaps it was just some random glitch that prevented it from discovering the router on the first installation and getting it to do the network discovery stuff again will result in it properly finding the DHCP interface in the router and things will start working properly.

---

### Post by meborc on 2007-12-10
> **rkd said:**
> I'm pretty sure he shouldn't put the router in bridge mode.  Then he'd have to fiddle around to get the connection to work from Windows.

I don't know why the Ubuntu install didn't automatically find and set up the networking properly, but using pppoeconf was definitely the wrong thing to try.  I don't know enough to say how to do it, but the first thing that he needs to do is make sure the pppoeconf stuff is completely undone.  Is there a way to tell Ubuntu to completely forget everything it thinks it knows about the networking and start fresh? I think that is what he needs to do.  Perhaps it was just some random glitch that prevented it from discovering the router on the first installation and getting it to do the network discovery stuff again will result in it properly finding the DHCP interface in the router and things will start working properly.

well... in this case i would use "sudo dhclient" command, to try to get the computer connecting with the router

and i kind of didn't think about xp when suggesting the "bridge" mode :) ups

---

### Post by schmildo on 2007-12-10
Here's a thread discussing the IPv6 issue (it's a quick fix).
[http://ubuntuforums.org/showthread.php?t=635216&highlight=ipv6+issue](http://ubuntuforums.org/showthread.php?t=635216&highlight=ipv6+issue)
(actually this wasn't what I originally found, I forgot to post it and lost it, but this discusses it anyway)

I'd try that once you somehow ditched the pppoe stuff....

I'm only guessing, but if I was going to try to remove pppoe, i'd first try the pppoe configuration program again to see if there's a 'i changed my mind go away' option, if that fails, i'd edit /etc/network/interfaces (with root priveleges) and mimic what my 'interfaces' file looks like.

youd basicly be deleting

[COLOR="Sienna"]auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
iface eth1 inet manual[/COLOR]

from your own file.

Now i do mean i'm guessing here, i really don't know much about it.

If the 's' hits the 'h' you could reinstall linux?

Hehe i meant 'ess' hits the 'aitch'

---

### Post by GaryReggae on 2007-12-10
Thanks for your further advice guys.  I have edited the /etc/networks/interfaces file and here is what it currently shows:

**/etc/network/interfaces**
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

Here is what happens if I do dhclient:

===========================================

sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 6737
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:90:2c:75
Sending on   LPF/eth0/00:18:f3:90:2c:75
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 1717 seconds.

==========================================

and finally ifconfig:

==========================================
gaz@GAZ-Ubuntu2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:90:2C:75  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe90:2c75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7275 (7.1 KB)  TX bytes:45185 (44.1 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

======================================

I have changed all the settings back to DHCP as they were originally but still no internet.  If I try and ping anything (other than the router), it just hangs and never comes up with anything (like when I try and use the internet).

Here is the results of ipconfig/all from windows:

> Windows IP Configuration

        Host Name . . . . . . . . . . . . : gaz1
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Marvell Yukon 88E8001/8003/8010 PCI
Gigabit Ethernet Controller
        Physical Address. . . . . . . . . : 00-18-F3-90-2C-75
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.4
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : 10 December 2007 20:36:17
        Lease Expires . . . . . . . . . . : 10 December 2007 21:36:17 

Any more ideas?  I would be happy to reinstall Linux but I'm not confident it will make any difference as  it didn't work in the first place before I started playing with PPPOE (the reason I did that is because I consulted the Ubuntu help file regarding not being able to connect to the internet and it had two categories under DSL - USB modems and PPPOE so I assumed I must need to look at PPPOE as my router is definitely not USB (actually I tell a lie, you CAN use it via USB and indeed I do sometimes with my Windoze laptop) but the PC concerned here is only ever connected to it via Ethernet.

PS: Schmildo, you seem to have omitted the link to the IPv6 issue article you mentioned...

---

### Post by rkd on 2007-12-10
I'm only starting to learn about Linux, so I might be a little off on some of this, but here are a couple of experiments to try.  From what dhclient shows, I think it successfully contacted the DHCP server in your router.  Your PC was given the address 192.168.1.4 and has a DHCP lease lasting another 1717 seconds.  ifconfig seems to show packets flowing (though a lot more transmitted than received, which seems odd to me).  So I think some things are working at a low level.

Let's see what we can learn with some pings.

Open a terminal window.

enter ping 192.168.1.1

Do you get results similar to what the example from schmildo yesterday shows?  In particular, do you get responses, not timeouts?

If you got good responses, enter 

ping 208.67.219.99

and see whether you get responses or timeouts.  If you get responses, enter

ping [www.opendns.org](www.opendns.org)

Do you get responses or timeouts?

I'd expect the pings with numeric addresses will work.  If not, then I don't know enough yet to tell you what to do to fix it, but maybe someone else will know.

If the pings with numeric addresses work but the ping with the opendns address does not work, then I think your Ubuntu is not doing the DNS stuff correctly.  Again, I don't know how to fix it, but maybe someone else will know.

If the ping with the opendns address works, then the problem might be with the web browser you tried to use to see whether your network connection was working.  Try using another web browser.  Again, due to my ignorance of Ubuntu, I don't even know what web browsers are there in a default install, but perhaps you do and can try another one.

If you try another browser and it also fails, then I don't know what to try next, and we'll have to wait for someone with more knowledge than I to come along to offer some help.

---

### Post by schmildo on 2007-12-12
Sorry man yeah I did forget to post it, and I can't find the orignal thread I was looking for, but this page: [http://ubuntuforums.org/showthread.php?t=635216&highlight=ipv6+issue](http://ubuntuforums.org/showthread.php?t=635216&highlight=ipv6+issue) does mention the issue and a couple of ways to stop it.  (I didn't have the problem myself,so i dont' know why other people would)

---

### Post by nezam05 on 2008-07-20
Well, i found one solution in roaringpenguine.com. but i dont know how to work with this.
can anyone tell?

---

