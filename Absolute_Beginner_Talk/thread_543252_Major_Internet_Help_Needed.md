---
title: "Major Internet Help Needed"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-09-04
Hi guys.  Last year at college, I used Ubuntu fine on the network here at school (even from the LiveCD), with no configuration.  This year, when I installed Ubuntu (same school, same connection, same computer, same version of Ubuntu) the connection will not work.  Please bear in mind that the Internet does work on my Mac and Windows installs.

If I ping [www.google.com](www.google.com), it says it could not find the host.  If I ping the IP address, it works once, but every ping that comes after that fails.  I can ping my own computer's IP address.

Finally, the IT guys here claim that nothing has changed on their end.  Please help, I'm so frustrated!!!

---

### Post by Darklighter137 on 2007-09-04
Bump.  I'm sorry, but I was really hoping to get my Internet hooked up tonight so I could configure it for my computer science class.

---

### Post by LowSky on 2007-09-04
are you talking about wireless or wired connection?

---

### Post by Darklighter137 on 2007-09-04
It is a wired connect (I know, it is all very odd).

---

### Post by coffecup1978 on 2007-09-04
perhaps you could post us the "ifconfig"?

in console:
#>sudo su
#>ifconfig

---

### Post by Darklighter137 on 2007-09-04
Done:

eth0      Link encap:Ethernet  HWaddr 00:16:EC:C8:3E:FC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by n3tfury on 2007-09-04
maybe your NIC is toast.  got any lights flashing on it?

---

### Post by dwhitney67 on 2007-09-04
> **Darklighter137 said:**
> Done:

eth0      Link encap:Ethernet  HWaddr 00:16:EC:C8:3E:FC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Your eth0 interface is obviously not connected.  Have you tested the hard-wire socket (in the wall) to verify that it is active?  Sometimes a simple problem like that can cause problems.

I presume you are back at school from a summer break.  Did you change your eth0 configuration to use a fixed IP vs. a DHCP-given IP?

---

### Post by Darklighter137 on 2007-09-04
To both of the above posters, my connection works fine in Windows Vista, so I know its not the socket or anything.

---

### Post by Darklighter137 on 2007-09-04
Sorry, I know this is one weird problem.  Before anyone suggests it, I've burned multiple CD's and all of them had the same problem (yes they were burned at x4, yes the md5 was checked, and yes the CD was checked before installing).

---

### Post by Darklighter137 on 2007-09-04
It may also help if I add this:  there is no router.  I just plug an ethernet cable from my computer into the wall (yes, this does work in Windows Vista, and used to work in Ubuntu).

---

### Post by dwhitney67 on 2007-09-05
Help us out... what are the settings on the eth0 device?  Select **System -> Administration -> Network** if you prefer a UI-driven tool.  Then select **Wired Connection** and the **Properties.**  Is it setup for DHCP?  If so, then close (cancel) that dialog box.

Has your school provided you with any connection info, like DNS Server IPs or a Domain IP?  Those can be added by going to the DNS tab.

Lastly, see what is written to dmesg concerning eth0 (and post it).  Run this command:

[FONT="Courier New"]$ dmesg | grep eth0[/FONT]

---

### Post by alienexplorers on 2007-09-05
Do you have your host name and domain name setup correctly? Do you have ETH0 setup for DHCP? Do you have ETH0 enabled?

---

### Post by Darklighter137 on 2007-09-05
To the first question, there are a bunch of "not availble's" and 0's in the fields.

There are no special requirements for my school's internet connection.  Once the connection has been registered (and it has), it works without anything special.

dmesg | grep eth0 yields:  

[    7.027102] eth0: RealTek RTL8139 at 0xf88e6c00, 00:16:ec:c8:3e:fc, IRQ 20
[    7.027116] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   24.130562] eth0: link down
[  286.109968] ADDRCONF(NETDEV_UP): eth0: link is not ready

Thanks for all the interest guys!

---

### Post by dwhitney67 on 2007-09-05
Two pages of posts and now the world finally knows that you have a Realtek 8139D.  :)


Try running this command:

[FONT="Courier New"]$ sudo modprobe 8139too[/FONT]

Then run:

[FONT="Courier New"]$ sudo /etc/init.d/networking restart[/FONT]

Then post what dmesg states by running this command:

[FONT="Courier New"]$ dmesg | grep eth0[/FONT]

---

### Post by Darklighter137 on 2007-09-05
Sorry, I was doing my best to be helpful to potential answers.

If I run *sudo modprobe 8139too*, nothing happens.
If I run *sudo modprobe 8139*, I get a **FATAL:  Module 8139 not found.**

The final command you suggested returns a "command not found" error.

Thanks!

---

### Post by dwhitney67 on 2007-09-05
Actually it appears the first modprobe you ran worked; it loaded the module.  Verify (if you wish) by running this command:

$ sudo lsmod | grep 8139

The other command should have worked.  Please try again:

$ sudo /etc/init.d/networking restart

Also verify your eth0 connection:

$ dmesg |grep eth0

$ /sbin/ifconfig eth0

---

### Post by Darklighter137 on 2007-09-05
Thank you for your prompt reply!

The sudo /ect/init.d/networking restart failed.  The other two commands produced output exactly like they did before, with no changes.

---

### Post by dwhitney67 on 2007-09-05
Ok, here's my last gasp... run this command:

[FONT="Courier New"]$ sudo modprobe 8139cp[/FONT]

You shouldn't see any response (that means it loaded the module).  You can verify by running:
[FONT="Courier New"]
$ sudo lsmod | grep 8139[/FONT]

Afterwards, try this:
[FONT="Courier New"]
$ sudo /sbin/ifconfig eth0 up[/FONT]

Btw, what was the error given when you ran the 'restart' on the networking script?  You are running Ubuntu 7.04 right?  If not, then maybe the script has a different name.  Look in /etc/init.d.

And also... if any of the command fail, please post the output.  Simply telling me that it "failed" gives me nothing.

---

### Post by Darklighter137 on 2007-09-05
The first command ran without a hitch.

The second command produced the following output:
8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp

The third command ran without a hitch, but there was no actual change in Internet connectivity.

The error with the restart networking script was that /ect/init.d/networking could not be found (I am using 7.04).

---

### Post by Darklighter137 on 2007-09-05
Thank you all again for your tremendous effort.  ^_^

---

### Post by dwhitney67 on 2007-09-05
Try replacing the "ect" with "etc" for that script you said you couldn't find.  Once again, the command is:

[FONT="Courier New"]$ sudo /etc/init.d/networking restart[/FONT]

Copy/paste if you have to.

If this script is still not found, then you are missing this (and who knows what else) from your distro.

---

### Post by Darklighter137 on 2007-09-05
Thank you, I'll give it another go as soon as I'm able.  

Thank you very much for all of your trouble!

---

### Post by Darklighter137 on 2007-09-05
Okay, here's the scoop.  The command worked just fine, but the Internet is still down.  :(

---

### Post by jerutley on 2007-09-05
Don't know why noone else has caught this.  This is from one of your earlier pastes:

[ 7.027116] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 24.130562] eth0: link down
[ 286.109968] ADDRCONF(NETDEV_UP): eth0: link is not ready


Basically, what this is saying is that the network chip is not seeing any signal coming in - unless you also get something later in dmesg saying the link is up.  What puzzles me is you say it's working in Windows - is this on the same machine?  Or is windows a different machine than your ubuntu installation - because seeing that definately makes me think either the network card in your machine is bad, or there is no signal coming from your network jack.

---

### Post by antisocialist on 2007-09-05
now, im no master of ubuntu or anything, as i just got it yesterday, but i had a problem with internet as well.
my moto is if it doesnt work restart it. i restarted and it didnt work. that was kinda a bummer for me. then i tried my less machine friendly version and booted ubuntu set the connections etc to what they needed to be saved it and held the power button till my laptop shut down. then i turned it back on and it was working perfectly.
now, im not saying this will work for you, but im not saying it wont either.
what im saying is that you should give it a try to see if it works.
even if it doesnt at least you tried so u might as well try rebooting (i got used to doing it twice a day with windows and eventually got bored looked for an alternative and found ubuntu)

---

### Post by Darklighter137 on 2007-09-05
Thanks, but I've installed, reinstalled, rebooted, etc. and it just doesn't work.  If this machine hadn't been working with Ubuntu before that'd be fine, but it was perfect last semester!

---

### Post by alienexplorers on 2007-09-05
Is windows on the same machine as Ubuntu.  If not are you using the same network cable.  If not try switching cables.  Cables are known to die from bending and such.  If it is the same cable I would try inverting the cable so the end in the computer is now plugged into the wall outlet.  If that does not work I would then have the feeling that the Ethernet card has died.  Is yours an on board model or is it a plugin adapter.  If a plugin adapter I would try to borrow one from someone at the college and try your computer with there card.  If it works then all you need to do is get a new card.

---

### Post by bigken on 2007-09-05
if the window is on another pc pull the card from that machine and try it on the linux machine

---

### Post by antisocialist on 2007-09-05
> **bigken said:**
> if the window is on another pc pull the card from that machine and try it on the linux machine

now THAT is a good idea =p

---

### Post by Darklighter137 on 2007-09-05
Thanks guys, but the Windows and Ubuntu are on the same machine.

---

### Post by bigken on 2007-09-05
you could try pulling the card boot ubuntu without the card then shutdown put the card back reboot and see if there are any changes

---

### Post by alienexplorers on 2007-09-05
i Just noticed something in your ifconfig listing.  I am listing yours and mine to show the differences.
Yours:
> eth0 Link encap:Ethernet HWaddr 00:16:EC:C8:3E:FC
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:20 Base address:0x6c00 

Mine:
> eth0      Link encap:Ethernet  HWaddr 00:0F:B5:8A:BF:12
          inet addr:192.168.1.43  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2610026 (2.4 MiB)  TX bytes:261734 (255.5 KiB)
          Interrupt:5


You are missing the inet, bcast, and mask.  Yours also does not say running after up broadcast.  

This sounds like your Ubuntu is not interperating the address and mask sent to it.  It sounds ike your DHCP is not working correctly.  Try going into synaptic and removing completely dhcp3-client and dhcp3-common.  Reboot your computer.  When it finishing loading go back into synaptic and reloading these two drivers.  Reboot again and see if this helps.  Try listing ifconfig again and post results.

---

