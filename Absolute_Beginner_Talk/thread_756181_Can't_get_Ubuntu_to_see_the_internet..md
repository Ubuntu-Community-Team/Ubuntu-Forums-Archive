---
title: "Can't get Ubuntu to see the internet."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by linuxsmithB on 2008-04-15
1. I'm running Ubuntu 7.10

2. Dynex card - brand new

3. D-Link router

Ok, here goes....
A friend gave me an old Gateway computer she wasn't using anymore, so I decided to take it to use as a linux 'hobby' box.
I installed LinuxMint, and now the new version (7.10) of Ubuntu. Install runs fine, but the network card will not 'see' the D-Link router. It was working before, using the exact same router, earlier version of Mint.
The network card built into the motherboard went out, so I went and bought the Dynex card.
Looking at the router settings, I can see that the router is seeing the Dynex card, as it is giving me the MAC address of the card.
I have tried the DHCP settings, I have tried to assign it a static IP address.
The only thing I can think of is if it is a 'driver' problem.
Help?

---

### Post by neurostu on 2008-04-15
Try the following then post the results below:
open a terminal and run:
```

ifconfig

```

---

### Post by linuxsmithB on 2008-04-15
eth0        LInk encap:Ethernet   HWaddr   (mac address here)
               inet6 addr:   fe80::21d:fff:fec3:5d39/64  Scope:Link
               UP BROADCAST RUNNING MULTICAST    MTU:1500  Metric:1
               RX packets:0   errors:0   dropped:0   overruns:0  frame:0
               TX packets:30  errors:0   dropped:0   overruns:0   carrier:0
               collisions:0   txqueuelen:1000

eth0:avah    Link  encap:Ethernet   HWaddr   (mac address here)
         inet addr:169.254.5.22  Bcast:169.254.255.255 Mask:255.255.0.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         Interrupt:18  Base address:0x2c00

lo   Link encap:Local  Loopback
     inet addr:127.0.0.1  Mask:255.0 0 0
     inet6  addr:   ::1/128  Scope:Host
    UP LOOPBACK RUNNING   MTU:16436  Metric:1
    RX  packets:16  Errors:0  dropped:0  overruns:0  frame:0
    TX packets:16  errors:0  dropped:0  overruns:0  carrier:0
    collisions:0  txqueuelen:0
    RX  bytes:1184  (1.1 KB)  TX bytes:1184  (1.1  KB)

---

### Post by linuxsmithB on 2008-04-15
incidentally, when it says (mac address here) it's just the listing of my card's mac address....
just wanted to be clear

Thanks for your help!!!!!!!!!!!!!!!!!!

---

### Post by spiderbatdad on 2008-04-15
try ```
sudo ifup eth0
```

---

### Post by linuxsmithB on 2008-04-15
sudo ifup eth0

give me

interface eth0 already configured

---

### Post by spiderbatdad on 2008-04-15
ok try:
```
ping -c 6 google.com
```

---

### Post by linuxsmithB on 2008-04-15
ping -c 6 google.com

gets me

unknown host google.com

---

### Post by spiderbatdad on 2008-04-15
wondering why eth0 seems to be configured twice. Maybe open network manager and set one connection to roaming...disable the other.
Sorry...temporarily stumped.

---

### Post by unutbu on 2008-04-15
Sorry if this is obvious, but, is eth0 a wired or wireless interface?

Also, please post

```
route
```

Finally, can you ping the router using its numerical ip address?
Something like
```

ping 192.168.1.1
```

---

### Post by linuxsmithB on 2008-04-15
ok...

ping 192.168.1.1

gets me

Network is unreachable


and I've already tried setting eth0 to roaming mode, with no appreciable effect

---

### Post by linuxsmithB on 2008-04-15
sorry...

is a wired connection

---

### Post by spiderbatdad on 2008-04-15
have you tried running ifconfig again? Sorry you are having this problem.

---

### Post by linuxsmithB on 2008-04-15
route

gets me

Kernel IP routing table
Destination   Gateway          Genmask    Flags   Metric   Ref   Use   Iface
link-local        *                  255.255.0.0   U         0           0       0       eth0
default          *                  0.0.0.0           U         1000     0       0       eth0

---

### Post by spiderbatdad on 2008-04-15
> **linuxsmithB said:**
> route

gets me

Kernel IP routing table
Destination   Gateway          Genmask    Flags   Metric   Ref   Use   Iface
link-local        *                  255.255.0.0   U         0           0       0       eth0
default          *                  0.0.0.0           U         1000     0       0       eth0

Hmmm. not seeing the router...

---

### Post by linuxsmithB on 2008-04-15
shouldn't the link be showing some of the same tcp/ip layer?

as in 255.255.255.0 instead of 255.255.0.0

????

---

### Post by spiderbatdad on 2008-04-15
Is this a usb router?
And could you post the model?
Default should be the ip of the router.

---

### Post by linuxsmithB on 2008-04-15
that's what's making me crazy here

I've used this exact same router, the exact same cable, and got this exact same pc to connect to the inernet before

but suddenly it's just gone blind for whatever reason

---

### Post by linuxsmithB on 2008-04-15
D-Link DI-604 router with the original firmware, never updated

it's worked with the LinuxMint before with no problems

why would Ubuntu throw it for a curve???

the only new variable in the equasion is the network card, and if the router is reflecting the mac address, what's the problem????

---

### Post by spiderbatdad on 2008-04-15
Have you done a kernel upgrade through the update manager...maybe a change in the module has affected the driver. Maybe installing the linux-backports-modules-generic. Or look for a previous kernel in grub and try it.

---

### Post by linuxsmithB on 2008-04-15
oh....   yea......

you remember what forum u in?!?!

ABSOLUTE BEGINNER TALK

you wanna try that in a bit simpler terms now?

---

### Post by spiderbatdad on 2008-04-15
Sorry. You seemed  savvier than I.
```
sudo apt-get install linux-backports-modules-generic
```

If that doesn't work, after a reboot, enter the grub menu by pressing esc as the system prepares to boot....look for an earlier kernel...like 2.6.22-14...or 2.6.20-XX

If neither works try googling your router model with the word "launchpad" included, and they may have a fix ready.

---

### Post by linuxsmithB on 2008-04-15
sorry

I know WIN computers, yes

I'm learning (quite slowly, granted) linux now

I get the basic idea of what's going on, but the language of the OS is different

it's just makin me crazy that the router is seeing it just fine, but the network card wants to be blind

---

### Post by spiderbatdad on 2008-04-15
keep us posted...

---

### Post by linuxsmithB on 2008-04-15
sudo apt-get install linux-backports-modules-generic

gets me

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

---

### Post by spiderbatdad on 2008-04-15
running ```
dmesg
```
and following the boot process can be helpful.
near the end is where networking is configured. There may be a message to upgrade a driver, and a link even. Or you may see other suggestions earlier in dmesg regarding hardware issue that need resolving.

---

### Post by spiderbatdad on 2008-04-15
> **linuxsmithB said:**
> sudo apt-get install linux-backports-modules-generic

gets me

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

opps...you have no internet connection, so you dont have the repos available.

---

### Post by linuxsmithB on 2008-04-15
ok,

dmesg

gets me

well, a ton of stuff...
but the last one is:

eth0: no IPv6 routers present

---

### Post by spiderbatdad on 2008-04-15
run ```
uname -r
``` then look in synaptic for the backports modules related to your kernel...
make sure CD is enabled as a source in System>>Administration>>Software Sources.

You can also do it like this...with back-ticks, not apostrophes:sudo apt-get install linux-backports-modules-`uname -r`
You router is most likely not an ipv6 router, but an ipv4.

---

### Post by unutbu on 2008-04-15
Would you please post /etc/network/interfaces?
```

cat /etc/network/interfaces
```

---

### Post by linuxsmithB on 2008-04-17
ok

cat /etc/network/interfaces

gets me

auto lo
iface lo inet loopback

---

### Post by spiderbatdad on 2008-04-17
That is correct, if your router is set up for DHCP assigning.

---

### Post by linuxsmithB on 2008-04-17
it is

when I go to the Devices - Network tools window, by Network Device, I have 3 options

loopback interface (lo)
Ethernet Interface (eth0)
Ethernet Interface (eth0:avahi)

when I try to configure eth0:avahi, it says "the interface does not exist"

when I try to configure eth0, it just asks me for either roaming mode, static ip address, automatic config(dhcp) or local zeroconf netowrk (IPv4 LL)

---

### Post by spiderbatdad on 2008-04-17
Trying to look back through posts...eyes are tired. Could you post the output of the command:
```
sudo lshw -C net
```

---

### Post by linuxsmithB on 2008-04-17
sudo lshw -C net

gets me

*-network
description:  Ethernet interface
product:  RTL - 8139/8139c/8139c+
vendor: Realtek Semiconductor co., LTD
physical id : b
bus info: pci@0000:01:0b.0
logical name: eth0
version 10
serial: mac address here
size:100mb/s
capacity: 100MB/s
width: 32bitts
clock:  33MHz
capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd qutonegotiation
configuration: autonegotation=on  broadcast=yes driver=8139too  driverversion= 0.9.28  duplex=full latency=32 link=yes maxlatency=64 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by spiderbatdad on 2008-04-17
Quit fooling around...you know you're connected. LOL.
I'm stumped. Is your cable good? Are you using USB (unsuitable for broadband?)
Can you use an ethernet cable?

---

### Post by spiderbatdad on 2008-04-17
Found this:[http://ubuntuforums.org/showthread.php?t=607953](http://ubuntuforums.org/showthread.php?t=607953)
goes back to checking dmesg.

Also googled: "ubuntu RTL - 8139/8139c/8139c+" and got numerous pages.

Boot flags: noisapnp pnpacpi=off pnpbios=off

---

### Post by gali98 on 2008-04-17
Something else to try:
```
cat /etc/network/interfaces
```
Kory

---

### Post by unutbu on 2008-04-17
I think it would be good if we assess where we are:

```
% ifconfig
eth0 LInk encap:Ethernet HWaddr (mac address here)
inet6 addr: fe80::21d:fff:fec3:5d39/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000

eth0:avah Link encap:Ethernet HWaddr (mac address here)              
inet addr:169.254.5.22 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:18 Base address:0x2c00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0 0 0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 Errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1184 (1.1 KB) TX bytes:1184 (1.1 KB)
```

The "avahi" stanza indicates that DCHP failed to obtain an IP address for the eth0 interface. Avahi steps in to assign an address.
(At least that's what I just learned from [http://ubuntuforums.org/showthread.php?t=513198](http://ubuntuforums.org/showthread.php?t=513198))

```
% route
kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
link-local * 255.255.0.0 U 0 0 0 eth0
default * 0.0.0.0 U 1000 0 0 eth0
```

The default route is no good. It should look more like this:

```
% route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         routerip        0.0.0.0         UG    100    0        0 eth0
```

Notice the "UG" flag. G stands for gateway. Also, the default gateway should point to a specific ip address (routerip).
```

% ping 192.168.1.1
Network is unreachable
```

Not surprising, since the routing table is borked.
```

% cat /etc/network/interfaces
auto lo
iface lo inet loopback

```
Okay if DHCP is working, but it isn't....

---

### Post by spiderbatdad on 2008-04-17
This card has bugs filed against it.

```
Try to open your /etc/rc.local

sudo gedit /etc/rc.local

and add your desired row into that file:

mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R

Please be sure, don't touch, at the end of file, the "exit 0" instruction

Hope this Help
```  From launchpad: [https://answers.launchpad.net/ubuntu/+question/18140](https://answers.launchpad.net/ubuntu/+question/18140)

or adding boot flags...from this post: [http://ubuntuforums.org/showthread.php?t=607953](http://ubuntuforums.org/showthread.php?t=607953)

---

### Post by unutbu on 2008-04-17
linuxsmithB, would you be willing to have another go at a static ip connection?
Personally, I think it is easier than fussing with DHCP.

Here is what you could try:

You're going to need some numbers:
1) The router's ip. Mine is 192.168.1.1 and I think this is typical. For the sake of concreteness, I'm going to assume yours is 192.168.1.1 too, but correct me if I'm wrong. 192.168.1.1 will be the gateway address.

2) You get to choose your static ip. It should be on the same subnet as the router, so 192.168.1 is fixed. As long as it has not already been taken, how about 192.168.1.2.

3) Now edit /etc/network/interfaces: Run ```
gksudo gedit /etc/network/interfaces 
```and add this stanza:

```
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
auto eth0
```

4) Now hopefully you have a computer that can connect to the router?
Open a browser window on that computer and point the url to 192.168.1.1.
Turn off DHCP. I don't think this step is critical.

5) On the computer you are trying to network now type
```

sudo /etc/init.d/networking restart
ping 192.168.1.1

```

Does that work?

---

### Post by linuxsmithB on 2008-04-18
did just what you said

set the static ip address on the router and did just what u said

nothing but "destination Host Unreaachable"

---

### Post by unutbu on 2008-04-18
Hm, running out of ideas. Post the output to 
```

route
```

---

### Post by linuxsmithB on 2008-04-18
k

route

gets me

Kernel IP routing table
Destination    Gateway    Genmask        Flags      Metric   Ref   Use  Iface
link-local         *                255.255.0.0   U            0           0       0     eth0
default           *                0.0.0.0           U            1000     0       0     eth0

---

### Post by spiderbatdad on 2008-04-18
From launchpad: [https://answers.launchpad.net/ubuntu/+question/18140](https://answers.launchpad.net/ubuntu/+question/18140)

---

### Post by linuxsmithB on 2008-04-18
oh well

thanks for your help

just have to shoot it

---

### Post by linuxsmithB on 2008-04-18
ok....

how's about this

I can ping the router (192.168.0.1) and get a reply

BUT STILL CAN'T GET INTERNET CONNECTION!!!!!!!

---

### Post by tropdoug on 2008-04-18
I had this problem too, this is what worked for me, gleaned from other posts.

1st disable ipv6 in firefox by opening browser, typing [COLOR=Blue]about:config i[COLOR=Black]n the address box when it loads, type in the [COLOR=Blue]'filter[/COLOR]' box, [COLOR=Blue]IPv6[/COLOR], press enter, you should see one line that reads[/COLOR] network.dns.disableIPv6  [COLOR=Black]and double click to re set the value to [COLOR=Blue]True [COLOR=Black]and close the browser.

2nd open a terminal and type [COLOR=Blue]sudo gedit /etc/modprobe.d/aliases
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Blue][COLOR=Black][COLOR=Blue][COLOR=Black][COLOR=Blue]a[/COLOR]nd look for [COLOR=Blue]alias net-pf-10 ipv6  [COLOR=Black]and add [/COLOR]off [COLOR=Black]to the end of the line Save it and close.

3rd type[COLOR=Blue] Sudo gedit /etc/apt/sources.list[/COLOR]
and uncomment all the [COLOR=Blue]deb[/COLOR] lines. which were commented out on the install because the program could not find your internet connection. [COLOR=Blue]Save the file. [/COLOR]

4th open System > administration > Synaptic and click the settings tab. make sure the boxes are all checked for the canonical repositories, and uncheck the CD one. Click on Third party software and check the two boxes. (you may add others later)  Next use the [COLOR=Blue]find the best server[/COLOR] button to locate a good mirror/ server and accept the choice. 
 To check the network connection open System >network tools, and go to ping and try pinging google.com 

If all is well, use System > Update Manager 1st to install all current updates and then get to work installing the packages you want through synaptic. 

Hope this works for you. (I was a newbie three weeks ago, there is a learning curve but the OS is tops) :guitar:

[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by linuxsmithB on 2008-04-21
Ok, I've got the internet to connect, and I've got the orange square in the right corner, telling me there are updates....

but...

when I click on the squre to start the updates...

I get "Could not initialize the package information...

An unresolvable problem occurred wihte initializint the pakcage information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Tyep 'cdrom:[Ubuntu 7.10_Gutsy Gibbon_ -Release i386 (20071016)]/' is not known on line 1 in source list /etc/apt/sources.list. E:The list of sources could not be read.'



WTF?

---

### Post by unutbu on 2008-04-21
Glad to hear you got an internet connection! What did you do to make it work?

The error message you're getting is simply a complaint that it can not find your Ubuntu Live CD's repository of .debs.

This is easy to fix:

gksudo gedit /etc/apt/sources.list

Change the line that begins with
```
deb cdrom:
```

to
```
#deb cdrom:
```

Then run
```

sudo apt-get update
```

---

### Post by linuxsmithB on 2008-04-21
ok...

the command "sudo apt-get update"

gives me

'see' is not now on line 2 in surce list /etc/apt.sources.list

now whut?

I did what I was told to up to now

I can see the internet, but I can't connect to the update sources...

close, but no "touchdown"

---

### Post by linuxsmithB on 2008-04-21
ok

I went through the /etc/apt/sources.list and removed all the "deb" but not the #

was that right?

for the cdrom:

I removed the line so that it reads

# cdrom:[Ubuntu 7.20 _Gutsy Gibbon_ - Release i386 (20071016]/ gutsy main restricted

correct?

---

### Post by linuxsmithB on 2008-04-21
make that 

# cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016]/ gutsy main restricted

---

### Post by linuxsmithB on 2008-04-22
IT'S ALIVE!!!!

Went through, removed all the 'deb' from the sources.list, then removed everything in the first line after cdrom:.

Restarted the system, gave it a minute to think, and it's working!

Got all the updates and can surf.

Thanks to every one for all your help!:KS

---

### Post by unutbu on 2008-04-22
I am very happy that your system is working now, linuxsmithB. I'm a little amazed by how you did it, though. Appalled might be the right word.

A pound sign (#) in /etc/apt/sources.list tells apt to ignore the line, regard it as just a comment for humans to read.

All other lines in sources.list should either be blank or start with 'deb' or 'deb-src'. You should never remove all the words 'deb'. I would have guessed that would cause apt-get to go into conniptions.

If everything is working just as you want it, then... great! But if you find that apt-get is not working, then I suggest you change your /etc/apt/sources.list to look more like this:
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted security universe

deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse restricted main
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse main

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

---

### Post by Magnum010 on 2008-07-10
> **linuxsmithB said:**
> sudo apt-get install linux-backports-modules-generic

gets me

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic

I am a newbie also, had same problem, look at synaptic PManager, hardy adds hardy, so you probably do see the net(ie READING package list, but what you typed works at another distros website---been having same probably until I S&Ggled it.

---

