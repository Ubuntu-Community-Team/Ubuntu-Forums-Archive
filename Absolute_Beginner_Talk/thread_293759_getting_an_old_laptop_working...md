---
title: "getting an old laptop working.."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by jas. on 2006-11-05
OK I may not be an absolute beginnger in Ubuntu, but I am when it comes to configuring laptops and PCMCIA network cards, so I'm hoping this is the right forum.

I have an old thinkpad 570 here, which I'm trying to get up and running, but I can't seem to get the network card recognized.  Have you ever done something where you've read so much and tried so many things that you can't even remember where to start?  That's kind of the situation I'm in now, so I'm hoping someone can help me out.

Starting from the beginning: 300 mhz, 4 GB drive, 192 MB RAM, so I'm trying to run as light a system as I can here.  My goal was to install a pretty minimal system, and once I get it working, to use fluxbox as the window manager. 

I found the thread here on the forums where the guy got his thinkpad 570E up and running dapper by installing 5.10 and then upgrading.  For some reason, 5.10 just wouldn't install on this computer. It would get to a certain point and just die.  I ran md5sums and my image was good; I re-burned the CD at lower speeds--nothing worked.  After several tries, I said what the heck, I'll give Edgy a try.  I dl'd the alternate install CD, and installed a command-line-only version, and everything went smoothly.

So first of all, this error shows up on boot and in dmesg:

[INDENT][56.087339] piix4_smbus 0000:00:06.3: IBM Laptop detected; this module may corrupt your serial eeprom!  Refusing to load module!
[/INDENT]
I've googled and found a few mentions, but nothign about how to possibly fix it.  but I'm wondering if it could be the source of my problem, which is that I can't get the network card up and running.  

here is ifconfig:

[INDENT]# ifconfig

Eth0	Lin encap:Ethernet  HWaddr 00:D0:B7:01:52:83
	UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 b) TX bytes:1710 (1.6 KiB)
	Interrupt:3 Base address:0x300

lo	Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	UP LOOPBACK RUNNING  MTS:16436  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
[/INDENT]

so no inet addr for eth0, although it does recognize that it's there.  /etc/network/interfaces it looks like this:

[INDENT]# more /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[/INDENT]
which seems pretty normal from what little I know about these things.  But trying to ping my router gave me a Network is unreachable command.

So I tried assigning it an IP address by going 

[INDENT]#ifconfig eth0 192.168.0.106 up[/INDENT]

Then when I pinged the router it actually tried to ping, which is a step in the right direction, but I got a bunch of "Desination host unreachable" errors.

running dhclient gives me this:

[INDENT]#dhclient
There is already a pid file /var/run/dhclient.pid with pid 3384
kille old client process, remove PID file
Listening on LPF/eth0/00:d0:b7:01:52:83
Sending on   LPF/eth0/00:d0:b7:01:52:83
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database – sleeping.
[/INDENT]

Now, on my router the subnet mask is 255.255.255.0, so I re-ran dhclient with an -s 255.255.255.0 flag, and got the same messages.

So, it seems that the card is there and recognized, but for some reason it just can't see my router.  (I should note that it has little red and green lights on the dongle, and the red light is lit meaning it has power, but the green light meaning connectivity isn't).

So finally I tried to give the computer a static address in /etc/network/interfaces:

[indent]auto eth0
iface eth0 inet static[indent]address 192.168.0.106
netmask 255.255.255.0
gateway 192.168.0.1[/indent][/indent]

and restarted networking.  Still got the 'destination host unreachable' errors.

I know there's something obvious I'm missing.  Can anyone help?

I should mention that I know it's POSSIBLE to have linux running on this machine--I did an installation of Zenwalk a couple of weeks ago and things worked OK, although it was slow.  But I am used to using ubuntu and like the way it works, and don't know much of anything about slackware, so I'd prefer to get this one up and running rather than resorting to that.

I know there's something obvious I'm missing, but I can't seem to figure out what it is.  Can anyone help?

---

### Post by mips on 2006-11-05
Just a shot in the dark but try booting with acpi=off or noacpi or something like that.

---

### Post by jas. on 2006-11-05
> **mips said:**
> Just a shot in the dark but try booting with acpi=off or noacpi or something like that.



Thanks for the reply mips.  I tried, but it didn't make much difference.  

I thought the noacpi or acpi=off thing was about detecting the cards in the first place, isn't it?

actually hold up, there's another message.  When I boot normally, I get this:

[INDENT]cs46xx: failure waiting for FIFO command to complete[/indent]

when I boot with noacpi, I don't get that error.  Googling turns up that it may be sound card related.

Either way, the network card such as it is doesn't act any differently.

would an lspci help?

[indent]#lspci
00:00.0 Host bridge: Intel Corp 440BX/ZX/DX &#8211; 82443BX/ZX/DC Host bridge (rev 03)
00:01.0 PCI bridge: Inte Corp 440BX/ZX/DX &#8211; 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:05.0 Multimedia audio controlor: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:06.0 Bridge: Intel Corp 82341AB/EB/MB PIIX4 ISA (rev 02)
00:06.1 IDE interface: Intel Corp 82341AB/EB/MB PIIX4 IDE (rev 01)
00:06.2 USB Controller: Intel Corp 82341AB/EB/MB PIIX4 USB (rev 01)
00:06.3 Bridge: Intel Corporate 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:07.0 Communication controller: Agere Systems WinModem 56K (rev 01)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
[/indent]

I don't see the card in there.  Did I mention it's a PCMCIA Intel Pro/100 card?

---

### Post by gn2 on 2006-11-05
Have you tried changing the MTU?

---

### Post by jas. on 2006-11-05
> **gn2 said:**
> Have you tried changing the MTU?


I hadn't before, but I have now, and no difference.  Thanks.

---

### Post by Neobuntu on 2006-11-05
OK now, listen up. Some of my "project" laptops are ThinkPad 560. Not X, E or anything else. That is significantly less (older) hardware than yours. The biggest problem with mine is the weird 256K screen and it not working without old and specific X for it. I have been round and round and the bottom line is what you are hoping for will be too slow.

In my neck of the woods, people are giving away notebooks BETTER than these. So I must point out to newbie at large that this is a REALLY geeky, never say die thing to be doing on these old and therefore less standard hardware notebooks.

Anything can be made to work but your still on a notebook that was made for (about) Windows 95 (Which is far more unsupported and dangerous). So "I feel the need, the need for S P E E D !"

Try Puppy Linux. I know you sound like the type to pick whatever YOU want but in the end I really think one of the many Live CD versions of Puppy will get the most life (WITH SPEED) out of your notebook.

If you do not have a CDROM on that notebook, remove the hard drive to another notebook that does and install these live CD files to there. Puppy (and D.S.L.) have HD installers. Don't do regular HD installs, do the one that installs the live CD file to work similarly on the HD instead of slow CD. This way, it loads from Hard Drive fast and into RAM. Then everything runs REALLY fast. It easier to upgrade the one big file upon next release (but test it first) and don't worry about your files and settings, these mature live CD's can handle that for you. Just always do your back ups (Get a Flash Drive). you do have a little less control of things like windows border looks but you can even remaster your own live CD version fairly easily.

Puppy (and optionally DSL) loads it's self into RAM and runs (Really fast) from RAM. Given about 128MB RAM or better; so you are good to go. 

Ubuntu, as great as it is (I like Kubuntu) is NOT optimized for these old,  relatively slow computers. You might have better flexibility with similar Debian but it will be a major roll your own custom (time) deal. Slackware is known for working on a little older box but these options are uber-geek (plenty of time needed) experiments. Puppy is right now. Even the down load goes fast.

Download the live CD first and try it out where you can. It's a slightly different feel than Ubuntu so give it a chance. It works.

You know, open software is simply amazing IF you know which one. If you want speed and you want it without all the to do. Walk with the Puppy.

If you have over 256MB RAM and a faster hard drive, use Kubuntu (also easy with Dapper); that is, if you'd like to make XP and Vista look bad (I mean REALLY bad).

Still, why not do them all (and dual boot)?

---

### Post by jas. on 2006-11-05
> **Neobuntu said:**
> OK now, listen up. 

<snip>

You know, open software is simply amazing IF you know which one. If you want speed and you want it without all the to do. Walk with the Puppy.

If you have over 256MB RAM and a faster hard drive, use Kubuntu (also easy with Dapper); that is, if you'd like to make XP and Vista look bad (I mean REALLY bad).

Still, why not do them all (and dual boot)?


thanks neobuntu--i'll take another look at puppy; it didn't work on this machine last time I tried (I've been fiddling with various distributions, in case I wasn't clear about that; I just would prefer ubuntu if I can do it). 

truth be told this old computer had been running xp for a couple of years without a problem, and i know it's uber-geeky to try and get a linux running on here.  I just thought it would be kind of a fun experiment.  if i can't do it, i'll give up and do something else--but i figured it was worth asking.

---

### Post by freshofftheufo on 2006-11-05
Not helping much but regarding the error you saw:
> [56.087339] piix4_smbus 0000:00:06.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
I've installed Edgy on my Thinkpad, a slightly sadder specimen than yours (128 RAM and 2xxMHz), and though I had to go through the alternate installation three times to get it to work, that warning was present each time and I don't believe there were any ill effects. I can't pretend to understand what it's referring to though.

---

### Post by jas. on 2006-11-06
thanks for the tip on that error, freshofftheufo.  

actually i ran puppy today and it worked like a charm this time, so i may just give up on getting ubuntu on this computer after all.  i mean, there's only so much time i can dedicate to it, and i've been messing around with it for several days now.

i mean, no offense or nothin.  i'm still running it on this server upstairs...

---

### Post by Buzzkill on 2007-04-26
I get the same "corruption" message on my 570E and have been trying to figure out where it comes from as well.  It seems however that your network card driver is the real problem and is not necessarily related to the error message.  I used fwcutter first to configure the driver for my broadcom 43xx based wifi card, but have been using ndiswrapper lately.  Google either one and you might find what you need to get your connection working.  Ubuntu may have it's dark corners of compexity but it kicks *** overall, and is worth another try.

---

### Post by jimrz on 2007-04-27
that "corruption" error seems to come up on all older ThinkPads,but does not seem to adversely effect operations. 
on my old 600x I also get an msg that the BIOS date = pre 2000 is unacceptable and acpi force will be required if you want acpi. a little research found that acpi force by itself can render your pcmia slots useless and suggested adding:
```
acpi=force pci=noacpi
```
to your menu.lst will solve the problem, and it did for me running feisty.
also, i agree with the previous post that your wifi problem sounds more like a driver issue than acpi. check out which chipset your card uses and see what solutions are out there. if yours is not easily fixable, I am using a netgear wg511t  w/ atheros 5212 chipset (can be had pretty cheap) and it works perfectly "out of the box"under fiesty w/ network-manager connecting using WPA-PSK or roaming to various open ap's.

---

