---
title: "Laptop with Ubuntu (Asus Z70V)"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Ichijin on 2007-04-14
Well I have an Asus Z70V, the specs are:

Dothan 735 @ 1.7Ghz
Kingston 1024mb 533 mhz
TSSTcorp TS-L462A CDRW/DVD
Cisco LMC350 Wireless Card
Hitachi 7K60 60gb 7200rpm
Realtek ALC880
1680x1050 LCD
ATI X600 pci-e

running Windows XP

I haven't started putting Ubuntu on yet, but i just want to ask a few questions before i start.  

1.  Is there a way for me to get more battery life than i would for windows? (i do scaling, undervolting, lcd brightness adjusting all on windows already)

2.  Will I have any problems that you can see right off the bat when i install Ubuntu?  What won't work at all?  (i have run the feisty fawn beta live cd and couldnt' get my wi-fi card to work)

3.  I am what some people might call audiophiles (ie. expensive gear for listening through headphones) and with windows i sometimes get a lot of cracking in the music, but a restart usually fixes that.  With Ubuntu, would I have that kind of a problem?

I found this link for Gentoo Linux [http://gentoo-wiki.com/HARDWARE_Asus_M6VA,Z70VA](http://gentoo-wiki.com/HARDWARE_Asus_M6VA,Z70VA) don't know if it would help

My main gripes are just with better battery life, running 1680, and low noise.  If i have those, I'm basically set to convert to ubuntu.

I'm a person who enjoys a little hard work to have something special, so even if it take a little "tweaking" to get things working, I'm totally up for it

Thanks in advance

---

### Post by chalex on 2007-04-14
1) you should be able to set the cpu frequency and the lcd brightness, I'm not sure about undervolting.  Try it out with the LiveCD.
2) the real install will be just like the livecd.
3) it sounds like a hardware problem.

---

### Post by cvmostert on 2007-04-14
A wifi card can be tricky... but try and start with the live cd again using a cable.. then go on irc and let the people walk you through and see if you can make it work... it might not be that difficult... and at worst, you might have to use ndiswrapper... and use your windows drivers... but first get it working with the live cd... just to make sure...

---

### Post by Ichijin on 2007-04-14
but are there any ubuntu specific options i can tweak to improve batt life?

---

### Post by Ichijin on 2007-04-14
> **cvmostert said:**
> A wifi card can be tricky... but try and start with the live cd again using a cable.. then go on irc and let the people walk you through and see if you can make it work... it might not be that difficult... and at worst, you might have to use ndiswrapper... and use your windows drivers... but first get it working with the live cd... just to make sure...

the wifi card uses a mini-pci slot, so im not sure what you mean by "use a cable"

---

### Post by annda on 2007-04-14
as to power saving, there are many modes available for cpu scaling etc. search for governors (i can't remember the details).

as to the audio problem, i thought audiophiles detest low-end devices such as computer sound cards ;-) but if you just like sound, check the audio output with the live cd. it will tell you whether it's a hardware of software problem.

for the right resolution you will need an ATI video driver fglrx.

---

### Post by Ichijin on 2007-04-14
> **annda said:**
> as to power saving, there are many modes available for cpu scaling etc. search for governors (i can't remember the details).

as to the audio problem, i thought audiophiles detest low-end devices such as computer sound cards ;-) but if you just like sound, check the audio output with the live cd. it will tell you whether it's a hardware of software problem.

for the right resolution you will need an ATI video driver fglrx.

if i were to do scaling, undervolting, etc like windows, would i get the same/more/less battery life using Ubuntu? (ive seen the poll already, but it doesn't tell me if it were they same settings)

as for the onboard sound card, im kinda forced to use it since all my gear is at home :D

---

### Post by cvmostert on 2007-04-14
> **Ichijin said:**
> the wifi card uses a mini-pci slot, so im not sure what you mean by "use a cable"

I mean.. do not use the wifi card for the internet at first.. use your wired internet. otherwise you will not be able to get onto the net! :-)

---

### Post by Ichijin on 2007-04-14
> **cvmostert said:**
> I mean.. do not use the wifi card for the internet at first.. use your wired internet. otherwise you will not be able to get onto the net! :-)

DOH lol ok ill try that, but it would be 100000x more convient to get my wireless working

---

### Post by cvmostert on 2007-04-14
> **Ichijin said:**
> DOH lol ok ill try that, but it would be 100000x more convient to get my wireless working

i know.. but to sort the problem out... using the irc chat channel... you will need internet in the beginning.. UNLESS you have more than one pc ! of course :-) that is all i meant... 

hope you figure it out.

---

### Post by annda on 2007-04-14
ad power saving: ubuntu (or any other up-to-date windows-competiting linux distributions) is not renowned for long battery life. you will probably get about the same performance as windows. 

this is because newer linuxes run all the possible kernel modules, deamons, services etc. per default to make sure nobody complains "my scanner is not recognized just after being plugged in", even if they use it once a year.

there are guides telling how to switch off unnecessary modules and services. you might find them useful.

---

### Post by Ichijin on 2007-04-15
ok well i just finished installing and updating my feisty.  Wifi card can roam but can't connect (running the latest firmware).  I can't get to 1680 (it gives me artifacts for some reason, unless im supposed to restart after i change it).  My touchpad is really sensitive, any way to adjust it?  Oh also the scrolling on my touchpad doesn't work

EDIT: 
forgot to add some impression.  Well first of all, its great, i haven't found 1 thing i don't like about it (if i fix the hardware compatibility probs)  but i think i can get used to this.  Start up for feisty is kinda slow, don't know if that is because of beta/needs to config stuff/etc.  its a little annoying that it keeps asking for my password to install stuff or go someplace.  haven't tested it in detail yet to see what else is wrong, but hopefully nothing else :D

---

### Post by Ichijin on 2007-04-15
ok well i got some linux drivers from cisco...and it comes with an install script, but says i need to "run it as root type".  I have no idea what that means lol

edit: quick search on google gave me "sudo -s" before the filename.  is this right?  because i hate having to switch back and forth to windows just to access the forum

---

### Post by Ichijin on 2007-04-16
well right now im confused as to how to install libsigc++ and gtkmm which i need for my cisco drivers?  any help?

---

### Post by RudolfMDLT on 2007-04-16
It seems you where thrown into the deep end pretty quickly... :) I think that the drivers need you to compile from source.... No problem, it gets done pretty easily.

Open up the terminal and type the following command: 

> sudo apt-get install build-essential

This will download the applications needed to do this.

then after that try running the script again!

EDIT: It might be that you require more than just the build-essential package  , when an application tells you to download a packadge, open up the terminal, type in 
sudo apt-get install PACKADGENAME

or open up Synaptic and search through the database for the file. In order to do this you might need to enable all your repo's [:confused: ]("https://help.ubuntu.com/community/Repositories/Ubuntu")!

Goodluck!

---

### Post by Ichijin on 2007-04-16
ok well i installed both libraries but i can't seem to install the cisco drivers. but when i run the install file it tells me "run the install script in the dir"  lol so i dont' know what its asking.

---

### Post by Ichijin on 2007-04-16
well i installed fglrx, now it restricts me with 3 resolution option under 1680

---

### Post by hardyn on 2007-04-16
is the V the same as a Va? I used to own a Va...

first... for the cost of an intel 2200 wireless (about 40$ cdn) go out and buy one, save the headache... any half assed tech can install one, and not that difficult if you are good with a screw driver and have some patients.  the 2200 or 2915 work out of the box.

i never had any trouble with the ati driver, other than it being the ati driver, i didn't not have your resolution trouble.  following the install guide at: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
worked flawlessly.

there are a few things you can do about battery life... kind of a linux gripe of mine right now.
1) turn of wireless when your not using it. worth about 1h.
2) in the bottom of /etc/default is acpi-config  turn on laptop mode, then go to /etc/laptop-mode
and adjust the hard disk spin down time, default is 5seconds... which sounds like hard disk abuse to me... i upped mine to 2.5 min.

there is a feature on the fglrx driver to throttle down the x700 when you unplug it.. enable that it will help tons... it works from the command line as well if you want the GPU fan to slow down alitte... it was very noisy for me.

good luck.

---

### Post by aktiwers on 2007-04-16
I recommend you to install Feisty on that laptop! 
There has been alot of improvements, better video card support, better wireless support and stuff like that, and Feisty final release comes out in 4 days, so the beta is pretty save to use (I use it, without any bugs so fare).

---

### Post by Ichijin on 2007-04-16
> **aktiwers said:**
> I recommend you to install Feisty on that laptop! 
There has been alot of improvements, better video card support, better wireless support and stuff like that, and Feisty final release comes out in 4 days, so the beta is pretty save to use (I use it, without any bugs so fare).

ummmm i am using it lol

---

### Post by Ichijin on 2007-04-16
in response to hardyn's post z70v is z70va just with an x600.  i really love my cisco card and wouldn't trade it for anything (in windows anyways :D )

---

### Post by Ichijin on 2007-04-16
feisty is running a little slower than windows and also the step transtions aren't as smooth.  is there a way to check if its using my max frequency and to decrease transition time.  on windows i have RMclock set to 100ms

---

### Post by Ichijin on 2007-04-16
k well fglrx is installed, i checked with fglrxinfo...now to get 1680x1050

---

### Post by Ichijin on 2007-04-16
nm got 1680 to work....JUST NEED WIRELESS :(

---

### Post by annda on 2007-04-16
hi!

can you point us to the guide you are using to install the driver? it could help to try to walk through this with you.

---

### Post by Ichijin on 2007-04-16
im just using the forum because i don' thtink there is a guide for this card.  

well first i ran the install using sudo -s 

then i said yes to EULA

then it gives me "Please run the install from the directory containing the 
contents of the driver and utility archive."

in the drivers folder there are .c and .h files and in the utility folder there are the utilities that i run in windows (but not for windows) there is no install file in those folders

i think im supposed to compile the .c and .h file? i dunno

---

### Post by annda on 2007-04-16
hmm, where did you get the driver file and what is your card, then?

i can see kpciinstall and cwinstall instructions on the cisco site. are you trying to run any of those?

---

### Post by Ichijin on 2007-04-16
im running an mpi350 and i got the drivers from there.  i have tried ndiswrapper gui tool and when i point to the inf nothing happens

---

### Post by Ichijin on 2007-04-16
> **annda said:**
> hmm, where did you get the driver file and what is your card, then?

i can see kpciinstall and cwinstall instructions on the cisco site. are you trying to run any of those?

lol that just made me even more confused

---

### Post by annda on 2007-04-16
i have found out that a driver for your card is included in the latest linux kernels.

try this to see if the appropriate module is loaded:

```
lsmod | grep airo
```

---

### Post by Ichijin on 2007-04-16
i get:

 airo                   72352  0

---

### Post by annda on 2007-04-16
cool.

can you post the output of

```
ifconfig
```

and
```

iwconfig
```

---

### Post by Ichijin on 2007-04-16
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:13:D4:4A:B4:EC  
          inet addr:192.168.0.116  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe4a:b4ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:235780 (230.2 KiB)  TX bytes:24669 (24.0 KiB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:0D:65:72:C3:F8  
          inet6 addr: fe80::20d:65ff:fe72:c3f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:227 errors:7971 dropped:0 overruns:0 frame:7971
          TX packets:98 errors:13 dropped:0 overruns:0 carrier:0
          collisions:168 txqueuelen:1000 
          RX bytes:61644 (60.1 KiB)  TX bytes:10771 (10.5 KiB)
          Interrupt:17 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2377 (2.3 KiB)  TX bytes:2377 (2.3 KiB)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"winston"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:A4:31:AA   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=-88 dBm  Noise level=-95 dBm
          Rx invalid nwid:372  Rx invalid crypt:17  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:38943   Missed beacon:1

wifi0     IEEE 802.11-DS  ESSID:"winston"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:A4:31:AA   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=-88 dBm  Noise level=-95 dBm
          Rx invalid nwid:372  Rx invalid crypt:17  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:38943   Missed beacon:1


...winston is just a open access point with no security, but my actual one i want to use is ecrypted with WEP 128bit

---

### Post by nautilus on 2007-04-16
just to chime in about battery life..

i have a compaq v3000, and i've managed to extend my battery life drastically for about $100.

so, here's what i did:

i bought ram.

yep, that's it.  almost.  i just bumped it up to 1.2GB and, well a lot of people may scream in agony here but... well, i roasted my swap partition.  removed, gone...

anyway, then i set my HDs to spindown after 5 seconds or so, and although i haven't scientifically timed anything, it feels like i'm getting an extra hour out of it.

yes, lowering TXPwr on the wifi card probably helped, dimming the LCD sure, not using the dvd-rw and when absolutely necessary only running it at 1x probably helped a bit too, but i think that was the kicker.

ideally, i'd want it all solid state with no moving parts.  for my next trick i'm going to try booting into a maaaassive USB jumpdrive, because i'm crazy.

-edit-

for WPA you may need wpasupplicant, as found in Adept.

---

### Post by Ichijin on 2007-04-16
my access point at home is running WEP, but maybe in the future ill think about WPA thanks for the advice

---

### Post by annda on 2007-04-16
so you do have some wireless networking going on.

how did you configure it? using an applet in the panel? i'm asking because the easiest way is to modify your /etc/network/interfaces file, but if you use the network-manager applet, it doesn't work very well with conf files and needs GUI changes.

---

### Post by Ichijin on 2007-04-16
i am using the network manager in system -> admin

---

### Post by annda on 2007-04-16
so what does your /etc/network/interfaces file look like?

---

### Post by Ichijin on 2007-04-16
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by Ichijin on 2007-04-16
there seems to be wifi0 and eth1 missing so maybe that is y

---

### Post by Ichijin on 2007-04-17
well found this site [http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b](http://www.thinkwiki.org/wiki/Cisco_Aironet_Wireless_802.11b)

says that only firm versions 5.60.17, 5.20.17, and older are compatible with kernel Linux 2.6.11 and airo driver 0.6.  Im currently running 5.60.21, so ill try and lower my firmware and try again

now if only cisco site would work :X

---

### Post by Ichijin on 2007-04-17
well i changed my firmware version to 2.60.17 and nothing happened, still the same situation

---

### Post by annda on 2007-04-17
i was so fixated at the idea of your card not working, that i forgot to suggest the easiest solution: install the gnome network manager and applet. according to the official [hardware list]("http://live.gnome.org/NetworkManagerHardware") you card is supported (but not WPA encryption)

```
sudo apt-get install network-manager-gnome network-manager
```

after that, right-click on the panel > add to panel > network monitor.

> The easiest way to get NM to start controlling your network interfaces (plural because it will also control your wired connection) is to open up (in gnome, not sure on kde) System > Admin > Networking (the default networking tool) open the properties for all the devices there, whether wired or wireless and in the properties dialog box clear the box that says 'enable this connection'
---found in [featherking's HOWTO]("http://ubuntuforums.org/showthread.php?t=341357")

this should let you configure your card's connectivity. if not, post back. there is a very good troubleshooting guide, which you need only parts of:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

good luck this time!

---

### Post by Ichijin on 2007-04-17
ok well i got the network monitor up...its getting a signall of 100%, but no packets are being received only ones which are being sent...so i guess the card isn't actually connecting to it just looking at it

EDIT: ok nm im starting to receive packets now...but still it doesn't work

EDIT: tried it with no security didn't work, when i go to support tab for both it doesn't give me a router ip, so dhcp isn't working right?

---

### Post by Ichijin on 2007-04-20
how would i compile .c and .h files for the wifi card?

---

