---
title: "I'm completely lost and confused"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Lderan on 2007-01-06
Okay I am sorry if there are hundreds of threads on this but I can't find anything that helps.

I can not connect to the internet, the wireless connection thingy in the network setting shows up. But no matter what I put into it, it just doesn't connect.

I have a belkin wireless router, the wireless card I can't remember the make. But it didn't need the install CD when I was using windows xp.

I'm using ubuntu 6.10 and I really don't want to return to windows xp

Can anyone help me out? I have no idea :)

---

### Post by chronusdark on 2007-01-06
did you install network manager?

```
sudo apt-get install network-manager-gnome
```

---

### Post by teaker1s on 2007-01-06
terminal type and post result 
[COLOR="Red"]lspci[/COLOR]

---

### Post by HereInOz on 2007-01-06
There are going to be other blokes who know far more about wireless networking with Ubuntu than I do, but let me throw in my $0.02 worth.

You may find that you are able to connect using WEP, but not able to connect using WPA or WPA-PSK.  This is apparently a common issue.

Although I personally know little about it, there is also a program available known as ndiswrapper, which I believe allows you to run Windows drivers on your wireless card.  Could be wrong and if I am, at least we will both learn when the corrections are posted.

The easiest way to get hold of ndiswrapper is to install Automatix2 - [http://www.getautomatix.com](http://www.getautomatix.com) - and then use that to install ndiswrapper, and a whole heap of other goodies.  Of course, you may need to set up a temporary Cat5 cable to achieve this, if you haven't already.

Sorry I can't be more specific, as wireless is not my strong point, but hopefully it helps a little.

---

### Post by Lderan on 2007-01-06
Thankyou all for the quick replies, will try and do what you lot have surgested :D

Okay nothing happened when I typed "ispci" all it says is command not found,
Also when I type in
"sudo apt-get install network-manager-gnome" it comes up with 

Reading  package list... done
Building dependency tree
Reading state information.. done
E: Couldn't find package network-manager-gnome

I am more confused now o.O

---

### Post by maniacmusician on 2007-01-06
> **HereInOz said:**
> There are going to be other blokes who know far more about wireless networking with Ubuntu than I do, but let me throw in my $0.02 worth.

You may find that you are able to connect using WEP, but not able to connect using WPA or WPA-PSK.  This is apparently a common issue.

Although I personally know little about it, there is also a program available known as ndiswrapper, which I believe allows you to run Windows drivers on your wireless card.  Could be wrong and if I am, at least we will both learn when the corrections are posted.

The easiest way to get hold of ndiswrapper is to install Automatix2 - [http://www.getautomatix.com](http://www.getautomatix.com) - and then use that to install ndiswrapper, and a whole heap of other goodies.  Of course, you may need to set up a temporary Cat5 cable to achieve this, if you haven't already.

Sorry I can't be more specific, as wireless is not my strong point, but hopefully it helps a little.
the **easiest** way to install ndiswrapper is actually

> sudo aptitude install ndiswrapper-utils
and if you want a graphical config utility for ndiswrapper:
> sudo aptitude install ndiswrapper-utils ndisgtk

---

### Post by Biggus on 2007-01-06
> Okay nothing happened when I typed "ispci" all it says is command not found,

I think its lspci (ell-ess-pee-see-eye), not ispci (eye-ess-pee-see-eye)

---

### Post by teaker1s on 2007-01-06
it's a small "L" not i at the start
lspci

---

### Post by Lderan on 2007-01-06
> **Biggus said:**
> I think its lspci (ell-ess-pee-see-eye), not ispci (eye-ess-pee-see-eye)

Oh my mistake :( sorry

---

### Post by teaker1s on 2007-01-06
no problem, I'm dyslexic;)

---

### Post by HereInOz on 2007-01-06
Thanks for the assist on ndiswrapper, maniacmusician.  I figured that if I contributed my limited information in the area, then someone would come back with the real deal.  :-)

Cheers.

---

### Post by teaker1s on 2007-01-06
need to find out what chipset the wireless has first as for ndiswrapper this is the most suitable one I've used and contributed to here even if you need to substitute driver file
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")

---

### Post by Lderan on 2007-01-06
okay this is what im getting

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
02:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by teaker1s on 2007-01-06
okay can't see your wireless device, any switch on it? or is it usb? if so terminal type
[COLOR="Red"]lsusb[/COLOR] 
post results

---

### Post by Lderan on 2007-01-06
okay its coming up with now
Bus 003 Device 004: ID 07b8:6001 D-Link Corp.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 079b:005d Sagem ( This is my phone I think)
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

---

### Post by teaker1s on 2007-01-06
[COLOR="Red"]Bus 003 Device 004: ID 07b8:6001 D-Link Corp.[/COLOR]

usb wireless adapter,I haven't left you I will be back shortly after i find what chipset your wireless has

---

### Post by Lderan on 2007-01-06
Thanks a lot :D

---

### Post by SVWander on 2007-01-06
Hi, you might try to research iwconfig. You will need to know the network card you are using before you can connect. For my network card I found it best to use i**wconfig Ra0** followed by command that would configure your network **essid "name of connection"** there is a post somewhere on this site that show the details. The final step is using dhcl. I am in the process of connecting to a new router so I don't have that machine up yet or I would copy the command I use. Good luck.
Tim

---

### Post by Lderan on 2007-01-06
I tried inputting iwconfig and what had what looked like my card was eth1. Is that right.
oh bags, im totally useless.

---

### Post by teaker1s on 2007-01-06
unless anyone watching this thread knows more it would appear that you have 
ZyDAS ZD1211 802.11b/g USB WLAN chipset.
According to what I can find ubuntu has a driver installed by default and providing firmware has loaded then installing 
[COLOR="Red"]network-manager-gnome[/COLOR] should control it
this thread discusses it 

[http://ubuntuforums.org/showthread.php?t=187947&highlight=ZyDAS+ZD1211+802.11b%2Fg+USB+WLAN+chipset]("http://ubuntuforums.org/showthread.php?t=187947&highlight=ZyDAS+ZD1211+802.11b%2Fg+USB+WLAN+chipset")

---

### Post by teaker1s on 2007-01-06
okay I have an Idea what is wrong terminal
[COLOR="Red"]gksudo gedit /etc/iftab[/COLOR]

paste what is displayed in gedit

---

### Post by Lderan on 2007-01-06
I just get lost looking at that thread, you have to treat me like an idiot :P

okay the gedit is coming up with

eth0 mac 00:30:1b:ba:2e:95 arp 1
eth1 mac 00:12:0e:0b:5e:b3 arp 1

---

### Post by SVWander on 2007-01-06
> **Lderan said:**
> I tried inputting iwconfig and what had what looked like my card was eth1. Is that right.
oh bags, im totally useless.
look at HOWTO: Wireless with Rt2500 cards . . . you are dealing with a different card but the commands are about the same. It is worth a try. I know the feeling . . . of being useless. I have been trying for days to fix my sound system! 
tim

---

### Post by teaker1s on 2007-01-06
okay we have decided you have a ZyDAS ZD1211 802.11b/g USB WLAN chipset. in your wireless and it should in theory work out the box with no agro providing firmware loaded.

 I think you can't see wlan because there is a config file that needs changing. to do this we are going to edit the file by using gedit text editor to edit the file and alter it. 

In terminal issue the command
[COLOR="Red"]gksudo gedit /etc/iftab[/COLOR]

copy and paste the file contents

---

### Post by Lderan on 2007-01-06
> **teaker1s said:**
> okay we have decided you have a ZyDAS ZD1211 802.11b/g USB WLAN chipset. in your wireless and it should in theory work out the box with no agro providing firmware loaded.

 I think you can't see wlan because there is a config file that needs changing. to do this we are going to edit the file by using gedit text editor to edit the file and alter it. 

In terminal issue the command
[COLOR="Red"]gksudo gedit /etc/iftab[/COLOR]

copy and paste the file contents


okay the gedit is coming up with

# This file assigns persistent names to network interfaces.
# see iftab(5) for syntax
eth0 mac 00:30:1b:ba:2e:95 arp 1
eth1 mac 00:12:0e:0b:5e:b3 arp 1

---

### Post by teaker1s on 2007-01-06
good we can see that you have two ethernet ports and from the commands you previously entered I know that you have one wired ethernet port and i can see that you have one wireless port that appears up and running.
Now what I would like you to do is to alter your file so it looks like below. the hash comments out  the eth1 and forces it to be wlan
[COLOR="Red"]
eth0 mac 00:30:1b:ba:2e:95 arp 1
#eth1 mac 00:12:0e:0b:5e:b3 arp 1[/COLOR]

save the file

next in terminal
[COLOR="Red"]gksudo synaptic[/COLOR]

search and install
[COLOR="Red"]network-manager-gnome[/COLOR]

**reboot**

---

### Post by Lderan on 2007-01-06
okay, i can't find network-manager-gnome :O

---

### Post by teaker1s on 2007-01-06
now in
[COLOR="Red"]system-administration-networking [/COLOR]

make sure the configuration tick boxes look like the screenshot below

you should also now have a network applet on desktop panel that has now taken over control of all network interfaces

---

### Post by Lderan on 2007-01-06
okay, i rebooted and its still no connecting. I couldn't install the network-manager-gnome thing as I couldnt find it :(

---

### Post by teaker1s on 2007-01-06
have you wired ethernet access on the ubuntu system?

---

### Post by Lderan on 2007-01-06
Nope there is no wire from the pc to the router, it's a tiny bit impratical

---

### Post by teaker1s on 2007-01-06
okay well to install the package with synaptic you need to have internet access:-k 
back in a moment-does your internet connected pc have a  cd burner?

---

### Post by Lderan on 2007-01-06
yes it does :)

---

### Post by teaker1s on 2007-01-06
okay which version of ubuntu edgy did you install? if your not sure tell me your processor in ubuntu box and in terminal
[COLOR="Red"]uname -r[/COLOR]

tell me the output

---

### Post by Lderan on 2007-01-06
it came out with
2.6.17-10-generic
its also ubuntu 6.10

---

### Post by teaker1s on 2007-01-06
okay what processor? pentium or amd  and is it duel core(64bit)

---

### Post by Lderan on 2007-01-06
its amd 3300 as far as i remember not a duel core.

---

### Post by teaker1s on 2007-01-06
okay well I'm not sure if you can use this attached package, it's 386i which is 32bit so should work on  amd as you have generic kernel

burn package to cd

---

### Post by teaker1s on 2007-01-06
put cd in ubuntu drive and

[COLOR="Red"]sudo apt-cdrom add[/COLOR]

[COLOR="Red"]sudo apt-get update [/COLOR]

[COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]

---

### Post by Lderan on 2007-01-06
Its saying
E: unable to locate any package files, perhaps this is not a Debian Disc

---

### Post by teaker1s on 2007-01-06
okay I know the problem, the package is fine, the issue is it's bitching about no internet access, ignoring that can you now 
[COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]
or does it refuse? if so we need to stop it trying to connect to internet repositories

---

### Post by Lderan on 2007-01-06
now its saying it can't find it. sorry for the late reply, didnt notice it went onto a new page.

---

### Post by teaker1s on 2007-01-06
did it work with cdrom add? and look at the cd?

if yes

okay try this in terminal

[COLOR="Red"]gksudo synaptic[/COLOR]
hit the reload tab

ignore the couldn't download all repository index's
on search select
look in: description and name.
[COLOR="Red"]network-manager-gnome[/COLOR]

---

### Post by Lderan on 2007-01-06
no i don't think the cd-rom add worked.
I tried that, but no luck.

---

### Post by teaker1s on 2007-01-06
try this copy the deb package to desktop and double click
package installer should appear and have install package button

---

### Post by Lderan on 2007-01-06
Status: Error : Depenendency is not satisfiable: libnm-util0
that what comes up when i double click it.

---

### Post by teaker1s on 2007-01-06
dependency issues:-k 
okay well the way to resolve this is download and burn full alternate 386i iso by selecting on download page

Other installation options 

select a mirror near you 

ubuntu-6.10-alternate-i386.iso

then run synaptic again and use Add cd-rom

hit reload tab

now search

network-manager-gnome

if this still won't work you will need repository sources commented out-I know the packages you require are on alternate iso as I extracted the package from the iso:mrgreen:

---

### Post by teaker1s on 2007-01-06
really must sleep it's 03:50am local time, I'm subscribed to this tread and i will be back to help you

---

### Post by Lderan on 2007-01-06
so do i install it from the alternate ubuntu or do i use it as a live cd thing? or am i just babberling?

---

### Post by teaker1s on 2007-01-07
you will need to let your ubuntu box boot normally without the cd in drive then
then run synaptic again and use Add cd-rom

place alternate iso in drive

hit reload tab

now search

network-manager-gnome

this is because you haven't got it connected to the internet we tell synaptic to add the contents of the alternate iso to it's sources.this means that we can now use synaptic to install any program contained on the cd source we added

---

### Post by Lderan on 2007-01-07
oh i see, you seriously rock dudey :) 
If it works then you are...a newbie saint.

Okay thens, what is happening is this.

Add cd-rom.

Insert a cd-rom > OK

Scanning CD-ROM

Software packages voume detected > Start package manager

An error occured.
E:Sub-process gpgv returned an error code (2)
W.Signature verification failed for :/cdrom/dists/edgy/Release.gpg
<close>

Do you want to add another CD-ROM? > no

Search > network-manager-gnome

Results none.

is that right? :confused:

---

### Post by teaker1s on 2007-01-08
W.Signature verification failed for :/cdrom/dists/edgy/Release.gpg

I'm not sure what this means it could be that the cd is corrupted or other issue-did you burn as an  iso image rather than just burn to disc?
also check md5 checksum?

---

### Post by Lderan on 2007-01-09
okay I have got it to connect to the internet now, 
The main problem now, with using network-manager-gnome, that it fails 5/6 times before it connects, how do i fix this?

okay, now it doesn't connect to the internet, the w-lan isn't showing up in the network-manager-gnome thing at the top. 
It wont connect even if i type the w-lan's name into "connect to oher w-lans" thing.
I haven't done anything to it and im very confused. lol

---

### Post by teaker1s on 2007-01-09
make sure on gnome panel that you click
system
administration
networking

and make sure that you have devices unconfigured-otherwise network-manager-gnome can't control them. see attached screenshot

---

### Post by Lderan on 2007-01-09
thats exactly what it looks like on my comp, gah the confusion

---

### Post by teaker1s on 2007-01-09
okay i only have experience with broadcom and ndiswrapper, try putting the config file back we altered by removing [COLOR="Red"]#[/COLOR]
[COLOR="Red"]gksudo gedit /etc/iftab[/COLOR]


save file

with broadcom commenting out eth1 forces the wireless to become wlan0, now network manager gnome can still connect the broadcom when it's seen as eth1. maybe your chipset didn't like us commenting out eth1.

reboot

other than this i would recommend looking at this thread and leaving a post and possibly messaging them

[http://ubuntuforums.org/showthread.php?t=187947&highlight=ZyDAS+ZD1211+802.11b%2Fg+USB+WLAN+chipset]("http://ubuntuforums.org/showthread.php?t=187947&highlight=ZyDAS+ZD1211+802.11b%2Fg+USB+WLAN+chipset")

---

### Post by Lderan on 2007-01-09
Will do this when i get back home, thanks again :D

---

