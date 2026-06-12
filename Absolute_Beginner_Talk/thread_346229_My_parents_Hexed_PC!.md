---
title: "My parents Hexed PC!"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-01-25
Yesterday my parents had some weird Windows XP problems that made the PC require shutdown time of approx 1-2 minutes.  So I decided to finally make a Dual boot Linux for them since Ubuntu doesn't get weird when installing Acrobat Reader.
The installation went smooth within 30 minutes I hade everything setup Internet, programs, media and even the printer.  Something which would've taken 2-3 hours on XP.

But today the Internet just won't work on Ubuntu!:mad: I figured it's some hardware problems since the PC was built by me for my parents.  (and everything I touch seems to be Hexed :(  )
But to confirm the Hex statement I booted into Windows XP to see if their would be a connection....and what do you know Internet popped out right away.
[COLOR="Red"]OS problem not Hardware problem[/COLOR]

SO IT WAS A UBUNTU PROBLEM AFTER ALL, not the electronic HEXED curse over me!
( I don't know weather I should be sad or happy :confused:  )
[COLOR="Red"]What can I do to bring back Internet on Ubuntu which previously worked yesterday?????[/COLOR]

---

### Post by Zzl1xndd on 2007-01-25
May not be the issue but I know on one machine I was using Kubuntu and every time I restarted its disabled my NIC. Just wondering if you checked to see if was enabled or not?

---

### Post by scrooge_74 on 2007-01-25
Did you try sudo dhclient eth0

---

### Post by turbojugend_gr on 2007-01-25
Let us know, is it an ethernet router, a wireless? a usb ? how do you connect to the internet ? Static Ip or DHCP ? Then everything would be much easier to solve ;) !

Till later, cheers.

---

### Post by monstermudder78 on 2007-01-25
Sorry I can't be much help, I had a similar problem (I think) and it just fixed itself.  Here is my short and rather unenlightening thread:
[http://ubuntuforums.org/showthread.php?t=344779&highlight=internet+connection]("http://ubuntuforums.org/showthread.php?t=344779")

---

### Post by jingo811 on 2007-01-25
> May not be the issue but I know on one machine I was using Kubuntu and every time I restarted its disabled my NIC. Just wondering if you checked to see if was enabled or not? How do I check my NIC?

> Did you try sudo dhclient eth0
> taco@Einstein:~$ **sudo dhclient eth0**
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:16:17:73:69:94
Sending on   LPF/eth0/00:16:17:73:69:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 119460 seconds.
taco@Einstein:~$

Also see these screenshots for info!
[http://img232.imageshack.us/img232/8278/screenshot4ux.png](http://img232.imageshack.us/img232/8278/screenshot4ux.png)
[http://img259.imageshack.us/img259/8112/screenshot11ef.png](http://img259.imageshack.us/img259/8112/screenshot11ef.png)

[SIZE="3"][COLOR="Red"]Update!  Weird observation the Connection properties says I have adress 192.168.0.3 but the cable is plugged into the 192.168.0.2 hole.  I'm in bizarro world again![/COLOR][/SIZE]

> Let us know, is it an ethernet router, a wireless? a usb ? how do you connect to the internet ? Static Ip or DHCP ? Then everything would be much easier to solve  !
I'm using a TCP/IP cable connected to the router so I'm guessing I'm an ethernet?!
Using DHCP I guess?!

> Chances are it was a network problem. I stick with code in the Ubuntu repositories. I've seen people running automatix or easyubuntu have trouble before. Neither of these are in the standard repositories.
 Yeah I'm using Automatix too and had to do some erasing and pasting in my repository list when terminal echoed some connection error messages during update and so on......
I basically deleted the entire Automatix repository URL adresses using only this list 
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)
But then I've been using the same list on my other Ubuntu PC for some months now without problems :confused:

---

### Post by Zzl1xndd on 2007-01-25
To check to see if your nic is enabled go system > Admin > networking. It might also be worth checking some of the other settings here.

---

### Post by jingo811 on 2007-01-25
Eh I think you need to be more specific with me!  I don't really know what NIC means so I don't know what to look for exactly.  But when using that networking program I see that the difference between my working Internet machine and the one that went loco on me is that the weird PC has got two Ethernet connections.
eth0 and eth 1
when my good PC has only got one Ethernet connection
eth0

Do I just disable either one of them and trial-and-error?

---

### Post by Zzl1xndd on 2007-01-25
Eth0 is normally your network card I would try haing just that one enabled. oh and sorry a NIC is your Network Interface Card.

---

### Post by mangoti on 2007-01-25
It seems to me that your network card (NIC) is up and running. By the way there is no numbered hole, only logical adresses automatically or manually assigned to all nics plugged into the router. In your case it ranges from 1 to 254; you don't have that many holes, do you? :)

Try these commands to see what's up (use ctrl+c to interrupt)

```
ping 192.198.0.1 (I assume this is your router)
ping 192.168.0.3 (your computer)
ping 127.0.0.1 (loopback, kind of like local/internal network address)
ping google.com
```

Then try:

```
route
```

and post the output.

---

### Post by Duppy on 2007-01-25
Go on System > Administration > Networking:

Is the wired connection ticked and enabled? Click properties.. have a look around, make sure its good to go.

---

### Post by jingo811 on 2007-01-26
Weird today my parents Hexed PC got assigned a new IP adress 192.168.0.2 by the router and it worked again all by itself without me fixing anything :confused: 
However I disabled one of the Ethernet connections.  So instead of having both
**eth0 and eth 1**
I now only have
**eth0**
enabled, hoping that this RANDOM disconnect from the Internet won't happen again.

Tnx for the help ppl!

---

### Post by jingo811 on 2007-01-26
OK I was wrong the problem returned 1 hour after first shutdown.  When I booted the PC up after 1 hour Internet was gone again.  Then after 5 hours it still didn't find Internet and fix itself like it did this morning.

The problem remains :( 
> Go on System > Administration > Networking:

Is the wired connection ticked and enabled? Click properties.. have a look around, make sure its good to go.
Yes both were clicked and enabled in the first place, then I tried to disable eth1 having only eth0 but nothing, so now I re-enabled all the eth's.  Still nothing.
[http://img260.imageshack.us/img260/4820/screenshot2zm2.png](http://img260.imageshack.us/img260/4820/screenshot2zm2.png)
On my other good PC that I've been using the same Ubuntu 6.06 I only have eth0 how the heck did I get 2 eth's on the new PC?

What next??

---

### Post by Bartender on 2007-01-26
Unless I'm mistaken - which happens a lot - eth0 is the loopback function.  It's a way that Linux talks to itself, so to speak.  So if you disabled everything but eth0 there's no way you're going to connect.

---

### Post by jingo811 on 2007-01-26
But if you compare the Networking screenshots between my old PC with Ubuntu 6.06 that I have been using for approx 4 months
[http://img144.imageshack.us/img144/3181/screenshotpa6.png](http://img144.imageshack.us/img144/3181/screenshotpa6.png)
and the screenshot of my parents new PC
[http://img260.imageshack.us/img260/4820/screenshot2zm2.png](http://img260.imageshack.us/img260/4820/screenshot2zm2.png)

You can see that the double eths' on the new Ubuntu 6.06 PC is causing more trouble than my old working 6.06 PC.  I've basically used the same procedures when installing all the extra media stuff with Automatix and such.

---

### Post by jingo811 on 2007-01-26
bump1

---

### Post by scrooge_74 on 2007-01-27
> **Bartender said:**
> Unless I'm mistaken - which happens a lot - eth0 is the loopback function.  It's a way that Linux talks to itself, so to speak.  So if you disabled everything but eth0 there's no way you're going to connect.

You are mistaken eth0 is usually refer to your ethernet card (or at least the first one) your system recognizes.

Loopback is recognize as:   lo

JINGO811:  you should check the config files, post the info on 

/etc/network/interfaces
/etc/host.conf
/etc/resolv.conf

---

### Post by jingo811 on 2007-01-27
taco@Einstein:~$ **sudo gedit /etc/network/interfaces**
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp

auto eth1


taco@Einstein:~$ [B]sudo gedit /etc/host.conf
[/B]
> order hosts,bind
multi on

taco@Einstein:~$** sudo gedit /etc/resolv.conf**

> nameserver 195.58.103.130
nameserver 195.58.103.18
nameserver 213.150.135.210

---

### Post by scrooge_74 on 2007-01-27
I think is your interface file is the problem it says you have 6 network cards and everything is in auto. The system is confuse.

do a dmesg and find out which ones are your real cards and then comment out the rest, you should have only the lo, probably eth0 and if you have wireless is one of the others.

Then you should reboot and let the system use the correct one

---

### Post by jingo811 on 2007-01-28
**1.) dmesg**
Hmm I think I will need some hands on guidance with the DMESG command the list is like miles long but these are the lines I found about eth's I don't know exactly what to look for when searching for the Network card stuff?
> [17179588.836000] eth0: forcedeth.c: subsystem: 01462:7250 bound to 0000:00:08.0

[17179589.356000] eth1: forcedeth.c: subsystem: 01462:7250 bound to 0000:00:09.0

[17179596.708000] eth1: no link during initialization.

**2.) ##Commenting /etc/network/interfaces**
But still I experimented by commenting selected lines like so and when they didn't work I tried a different combinations but that's not very scientific like.  There's like hundreds of combinations I can try so I stopped and waited for further instructions from you guys.

Here's one combination I tried of many that didn't seem to work :confused: 
> taco@Einstein:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


#iface eth1 inet dhcp

#auto eth1

Again I need to point out there's 2 networking cards when using networking program
[http://img260.imageshack.us/img260/4820/screenshot2zm2.png](http://img260.imageshack.us/img260/4820/screenshot2zm2.png) - Screenshots from before, for this configuration eth1 was crossed over and disabled!
How can I delete the one that's not neccessary, I only have one network card and its built-in the MOBO.
[B]
3.)  How my good PC look like[/B]
There's only 1 network card.
[http://img144.imageshack.us/img144/3181/screenshotpa6.png](http://img144.imageshack.us/img144/3181/screenshotpa6.png)
OK this is how my good PC with the same 6.06 install CD have looked like these past 4 months without behaving weird with Internet so far.....
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
Couldn't I just use the exact same 
/etc/network/interfaces
configurations on my parents new Ubuntu PC?

**4.) What made this problem happen to begin with?**
OK I used the same Ubuntu 6.06 Live CD to install Ubuntu, for both my old and new PC.
Both were installed from scratch with default Ubuntu settings, except I dowloaded Automatix on both PCs at different time thus by different versions.
But still that can't possible be the reason for my Networking setting to differ so much??
WHy WHy WHy :confused:

---

### Post by scrooge_74 on 2007-01-28
It seems you have to network cards, eth0 and eth1, eth0 should be your ethernet card.  You can comment out the rest

Automatix could be the reason you had troubles in the first place.

You only need to have lo, eth0 and eth1. Take the rest out and reboot, you can even check that same file when booting from the Live CD

---

### Post by jingo811 on 2007-01-29
OK I tried to copy the Interfaces list when doing the Live Boot since Internet worked during Live.  But that didn't solve anything back in the real world.

**Before shot:**
[http://img260.imageshack.us/img260/3600/screenshot1wk8.png](http://img260.imageshack.us/img260/3600/screenshot1wk8.png)
Connection always said "lo" I couldn't change it through the drop down list and 
Default gateway list was always empty without choices.
**After shot:**
[http://img165.imageshack.us/img165/834/screenshot2at2.png](http://img165.imageshack.us/img165/834/screenshot2at2.png)
Now Connection seems to be ok it says eth0 everytime I boot but
Default gateway list always gets emptied after reboot :confused: 

So the above solution worked the first time but then the next time I rebooted it Internet dissappeared again.
Is there no end to this never ending madness :(

---

### Post by jackrobinson on 2007-01-29
> **scrooge_74 said:**
> Automatix could be the reason you had troubles in the first place
I don't think so.

---

### Post by mangoti on 2007-01-29
How many physical network cards do you actually have?

---

### Post by jingo811 on 2007-01-29
Well I bought this MOBO in order to build the simple surf machine for my parents
[http://www.webhallen.com/prod.php?id=58975](http://www.webhallen.com/prod.php?id=58975)
Could this description mean that I have 2 network ports?
• LAN Dual Gbit LAN (nVidia lMAC)

....*browsing my MOBO manual* hehe seem like I really do have 2 network cards in the MOBO.  Guess I'll have to disable one and see if I can reach Nirvana :guitar:

---

### Post by LookTJ on 2007-01-29
Maybe the dhcp file is to blame?

---

### Post by mangoti on 2007-01-29
> **jingo811 said:**
> Well I bought this MOBO in order to build the simple surf machine for my parents
[http://www.webhallen.com/prod.php?id=58975](http://www.webhallen.com/prod.php?id=58975)
Could this description mean that I have 2 network ports?
• LAN Dual Gbit LAN (nVidia lMAC)

....*browsing my MOBO manual* hehe seem like I really do have 2 network cards in the MOBO.  Guess I'll have to disable one and see if I can reach Nirvana :guitar:

It appears that you have 2 NICs. If you need them both, you will have to assign a default route to the one connected to the Internet: 
```
sudo route add default gw 192.168.0.1
```
assuming 192.168.0.1 is the IP address of your router.

If you only need one, your best bet is to disable one in the bios.

---

### Post by jingo811 on 2007-01-30
> sudo route add default gw 192.168.0.1
Solved this mystery :D WHOOOOOOHAAAAAAAA (that's my way of saying tnx to everyone)

---

### Post by jingo811 on 2007-02-06
OK I had to Un-resolve this thread for the 3rd time bump!!!
After 1 week of stable Internet connection by using the above default gateway command I finally got HEXED again.
Ubuntus networking got confused again after all these troubleshooting.  What else can I do to contain this problem further more?

---

### Post by jingo811 on 2007-02-08
bump 4.

OK I used every little trick that I've learnt from you guys and it seems the only way to get my NIC back online was doing the 
```
sudo route add default gw 192.168.0.1
```

But I've already done that 2 weeks ago do I need to re-type that in everytime Ubuntu gets confused by chance in the future also?
Isn't there a config file I can paste this into so that the network confusion gets fixed permanently not just temporarily?

---

### Post by jingo811 on 2007-02-10
[COLOR="Red"]Fresh start bump 5![/COLOR]

OK to make this problem less confusing I decided to summarize all that I've done through these 3 pages.  Maybe someone then can see the absolute problem confusing my Ubuntu.
The following are the commands that I've used to troubleshoot with:

**1.)**
```
sudo dhclient eth0
```
[COLOR="Sienna"]#Nothing much was obtained by this command.[/COLOR]

**2.)**
> ping 192.198.0.1 (I assume this is your router)
ping 192.168.0.3 (your computer)
ping 127.0.0.1 (loopback, kind of like local/internal network address)
ping google.com
route
[COLOR="Sienna"]#Nothing valuable to pinpoint my problems with these commands.[/COLOR]

**3.)**
/etc/network/interfaces
/etc/host.conf
/etc/resolv.conf
[COLOR="Sienna"]#Only network/interfaces was worth tampering with.[/COLOR]
[B]
4.)[/B]
```
sudo gedit /etc/network/interfaces
```

> #auto lo
#iface lo inet loopback
[B]
auto eth0
iface eth0 inet dhcp[/B]

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

[COLOR="Sienna"]I basically commented out everything in the list except for eth0 is that really healthy in case I need to do some extra networking stuff like SAMBA and such things in the future?[/COLOR]

**5.) Last and only workable solution so far...**
```
sudo route add default gw 192.168.0.1
```
But it only managed to make my Ubuntu networking stable for 1 week after that it got confused again and I had to type the whole command in and reboot.  In order for my PC to get on the Internet.

[COLOR="Red"]QUESTION[/COLOR]
Is there a permanent solution for me so that I won't have to re-enter such long commands in case Ubuntu gets its networking confused again?  By the way its my parents PC so they won't be as patient and understand how to manually type in long commands everytime Internet fails.

---

### Post by jingo811 on 2007-02-10
OK things got ugly when I commented out these lines from the interfaces list last night.
> #auto lo
#iface lo inet loopback
It made my Desktop vanish all together when logging in there was no navigating to be done.
But that's solved now!

However that little drama made me a little more enlightened it seems like these 2 commands in combination will make NIC come back online again temporarily```

sudo dhclient eth0
sudo route add default gw 192.168.0.1
```

So my question is this, is there a permanent solution to making these 2 commands run everytime I boot my PC?

---

### Post by jingo811 on 2007-02-11
Is this a unique problem that can only be solved permanently by using Bash programming?
I'm reading about it but haven't learnt it yet...

---

### Post by gwpritch on 2007-02-11
This has probably been getting confusing based on all the varying advice you have been getting, but I think your ultimate answer is buried in this thread.
I had a similar problem when I added a wireless router to my home network. The internet would work for a bit after reboot or restarting the network but then would stop for no apparent reason. In frustration I even built myself a network restart icon.
What I finally discovered was that it was having both the wired nic (eth0) and the wireless nic (ath0) activated that was causing confusion and blocking internet access.
So first....System>Administration>Networking....make sure that the wireless network connection ath0 is not active (ie the box not checked...if it is you are probably reactivating the nic every time you reboot) since you are only using a wired network.
Second...just check back in /etc/network/interfaces and make sure that only eth0 and lo are set to auto. 
```
sudo /etc/init.d/networking restart
```
You should now good to go ... no further action should be required to make it permanent.

---

### Post by jingo811 on 2007-02-12
How can I make this command run every time I boot my PC?
```
sudo /etc/init.d/networking restart
```

I'm happy that I can control my network hardware and doesn't mind using terminal everytime I want to access Internet by fixing my confused NIC.  But this particular coumputer is for my parents who doesn't even know how to use Windows XP properly.
So I would like to make this Networking fix run automatically without them having to type anything in terminal every time they turn on the PC.

---

### Post by gwpritch on 2007-02-12
If everything is set up as I indicated and ath0 is deactivated, then you shouldn't have to do anything. Hopefully your problem will be history. The command was just to restart the network without rebooting once you made the changes.

---

### Post by jingo811 on 2007-02-12
Well my interfaces list looks like this and everytime GUI networking shows an empty space in the **Default Gateway Device **dropdown list.
```
sudo gedit /etc/network/interfaces
```
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

So I think I need to find a way to insert your command in some Autostart file for Ubuntu.
How can I achieve that?

---

### Post by gwpritch on 2007-02-12
ok do this:

System>Administration>Networking>Wired Connection Properties

Change configuration to Static IP Address and specify the address and gateway manually.

That should make it permanent. There is really no necessity to use DHCP on a small home network anyway.

---

### Post by jingo811 on 2007-02-12
In what scenarios are DHCP the best choice?

---

### Post by gwpritch on 2007-02-12
I'm no network expert but I would guess on large networks where it is just not feasible to individually assign addresses to every box and where you want central control of access to the network and subnetworks.

---

### Post by jingo811 on 2007-02-14
tnx for the tips.  Static do sound like the optimal answer for me, but I want to learn the big stuff so I guess I'll have to learn Bash scripting to solve my annoying DHCP problem.
Which might take some weeks to learn so I probably should [Re-solve] this thread at this point.

---

### Post by scrooge_74 on 2007-02-15
jingo811, did you check this info? [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php) , it has instruction on how to avoid lossing the name servers

---

### Post by jingo811 on 2007-02-15
tnx I'll read that.
> it has instruction on how to avoid lossing the name servers
So are you saying I'm having problems with my name server or is it an indirect problem?

---

### Post by scrooge_74 on 2007-02-15
it seems dhcp will lose the IPs of the dns servers

---

### Post by gwpritch on 2007-02-15
Its not so much that the dns server is lost but it is renewed with every new lease. This can be overcome by editing /etc/dhcp3/dhclient.conf and looking for a line that says something like: 

#prepend domain-name-servers 127.0.0.1;

uncomment this line and change the IP address to an alternate DNS. Multiple DNS servers can be added by copying this line one after the other. This alternate will then be permanently added to the DNS list and will be checked before the DNS provided by your ISP.  I did this to get around a notoriously slow DNS from my provider.

---

### Post by scrooge_74 on 2007-02-15
You are correct, that is exactly the info on the link, to make changes to that line so it wont loose it.

It happen to me when using wireless at home or at my brother in law house, config are different and had troubles myself in the past

---

### Post by jingo811 on 2007-02-27
I followed the instructions on 
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)
by editing both these
/etc/resolv.conf
/etc/dhcp3/dhclient.conf

I still get a confused NIC/router cooperation.
Do I need to do the same procedure to my router in order for this to kick in?
[http://www.opendns.com/start/netgear.php](http://www.opendns.com/start/netgear.php)

---

