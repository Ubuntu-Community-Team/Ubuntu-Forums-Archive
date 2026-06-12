---
title: "[SOLVED] Wireless issue"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Gipsy25 on 2007-12-29
I installed the last ver of ubuntu 7.10 a couple days ago and im having issues with the wireless card. (I am new i really dont know what im doing but so far i like ubuntu a lot ... thank you)

I have dsl, when pc is connected to the wire no problem i connect just fine.
The wireless card is installed correctly i checked the hardware list i can see it there (like in windows .. i know i know don't hate me for that last comment) i went to the network configuration and i can see the wireless option i do properties and i choose the wireless option then, wep (wep-key ASCII  enter password and of course the ssid name,and DHCP )  everything is fine ...  but i cant connect ... i read something about the wpasupplicant so i checked if it was installed if im correct i do: 
[B]sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manage[/B]r

 it says is installed. so i am out of ides on this particular case 
any ideas on what im doing wrong ???? please help 

The wireless card is TRENDnet 
108Mbps 802.11g pci adapter 
supports 64/128 bit wep, wpa and wpa2

Thank you in advance

---

### Post by reverseninja on 2007-12-29
Out of curiosity, have you disabled wireless security temporarily and then tried to connect?

---

### Post by Gipsy25 on 2007-12-29
Ahaaa how do i do that ?? sorry i got that sudo stuff from another posting (similar to my issue) by the way thanks for taking the time and reply to me 

regards 
Gipsy

---

### Post by bwtranch on 2007-12-29
Do you have your own router?

---

### Post by Gipsy25 on 2007-12-29
ya i do ... its dsl .. (not the best but ...) i can connect using the wire ... under Ubuntu ... but it doesn't let me use the wireless card ... like i said before i can see the network but thats about it .. (dsl gives you a modem/router so you can connect wireless i connect just fine using windows with the same card)
Thank you

---

### Post by Gone fishing on 2007-12-29
what does your /etc/network which is the main config file look like?

mine looks like:
> 
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.224
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:ispasswordxxx
wireless-essid fish

auto wlan0

iface eth0 inet dhcp

auto eth0

the s: means it's ascii rather than hex does your look right?

---

### Post by Gone fishing on 2007-12-29
Oh and make sure in network settings you've disabled roaming first

---

### Post by Gipsy25 on 2007-12-29
Well i got some info before so i tried it but still didn't work ... this person told me to do this 
**********************************************
"Procedure to enable WPA Wireless in Ubuntu
To update the source list run the following command
sudo apt-get
sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome network-manager
sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command
sudo /etc/init.d/dbus restart

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.
After enterring all the details my wireless network was connected and working fine you can see in the follwoing screen
****************************************************
mine looks like this now because i did the changes before but still not working
This is the current file now ...  
before it looked the same but without the " ##" 
should i take that back  ???? 
im so confused 
Thanks 
*********************auto lo
iface lo inet loopback
## iface eth1 inet dhcp

## auto eth1

## iface eth0 inet dhcp

## auto eth0

iface ath0 inet dhcp
wireless-key s: Password
wireless-essid gipsy

auto ath0


iface eth0 inet dhcp

****************
Thanks

---

### Post by Gone fishing on 2007-12-29
If you use WEP why did you need to do all that stuff about enabling WAP. 

I wonder if thats the problem? I cant help feeling that the Network Manager gui would do all that if you selected WAP

---

### Post by bwtranch on 2007-12-29
OK, that's good. Doing an ad hoc thing on someone else's is tricky, but that can be done. Sounds like your network card is having trouble seeing the router. In my config, I have a ethernet running to the modem, it's actually a modem/router, then ethernet to the host computer, then ethernet to the wireless router and wireless to computer #2. The way you check settings for the router is to open up a browser and type 192.168.2.1
That pretty common or 192.168.1.1
There is another one and I can't remember it. You should be able to get the manual online though. Because if you get network manager to say it's working, it probably is. Another thing to check is static or dynamic IP addressing. Mine is dynamic, so that's all I have to set. If you have static you have to enter in the IP address and some other items. There's a great little tutorial out there and I'll see if I can find it and get back. :)

Edit: Have you posted the output of lspci ? or lsusb, depending on which one you are using?

---

### Post by Gipsy25 on 2007-12-29
im not sure .. i will put as it was before i made those changes and i will try again ....
i just did what he told me but im not sure what i did ... 
i'll see if it works ... 
wish me luck ...
thank you

---

### Post by Gipsy25 on 2007-12-29
ya i did that .. i went to the router page and i can see the name of the computer it says connected (using wire) i went to the wireless options and it shows wep and it shows the password ...  192.168 ... that i managed to do but still no luck .. now my question is .. should i reverse the changes that i did to my file or leave it as it is ... ?

---

### Post by Gipsy25 on 2007-12-29
ya i did that .. i went to the router page and i can see the name of the computer it says connected (using wire) i went to the wireless options and it shows wep and it shows the password ... 192.168 ... that i managed to do but still no luck .. now my question is .. should i reverse the changes that i did to my file or leave it as it is ... ?

---

### Post by ugm6hr on 2007-12-29
> **Gipsy25 said:**
>  i went to the network configuration and i can see the wireless option i do properties and i choose the wireless option then, wep (wep-key ASCII  enter password and of course the ssid name,and DHCP )  everything is fine 

The wireless card is TRENDnet 
108Mbps 802.11g pci adapter 
supports 64/128 bit wep, wpa and wpa2

First thing - you do not need to use Network Settings at all.  To return this back to normal:
**System->Administration->Network**
In **Connections** tab, select **Wireless connection** and click **Properties**
Tick the **Enable roaming mode** box and click OK, then close Network Settings.

To connect with wifi - click on the Network Manager icon (looks like a monitor screen or 4 vertical grey bars near the top right - in the panel (see screen shot here: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/))
Select your SSID, and enter the security details in the new window.  It should then connect each time.

If this doesn't work, then your wifi card probably needs a different driver.  Repost here for further advice.[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

---

### Post by bwtranch on 2007-12-29
In Properties try entering WPA personal.

---

### Post by Gone fishing on 2007-12-29
sounds like you're very close can you ping the router

---

### Post by bwtranch on 2007-12-29
Re: #14 Entering roaming mode never worked for me, even when I did have the right driver installed. But, 'cha never know. :confused:

---

### Post by ugm6hr on 2007-12-29
> **bwtranch said:**
> Re: #14 Entering roaming mode never worked for me, even when I did have the right driver installed. But, 'cha never know. :confused:

Do you use Network Manager or Monitor (aka Settings)?  Network Manager doesn't work if you don't have roaming enabled in Monitor, does it?  And Monitor does not have GUI  WPA support (hence it only offers WEP or open).

EDIT:
I have just realised that Network Monitor / Settings does offer WPA now (Gutsy). My mistake.

---

### Post by Gipsy25 on 2007-12-29
Well when i go to the settings it only says 
"ENABLE THIS CONNECTION"  but i remember seeing " Enable roaming mode" but i dont see it anymore. When i had that option and tried it would look for the network and it would asked me again for the password without connecting ... 

thank you

---

### Post by djfick on 2007-12-29
if you can ping the router and connect to the gui for it, there might be a DNS problem

---

### Post by ugm6hr on 2007-12-29
> **Gipsy25 said:**
>  it would look for the network and it would asked me again for the password without connecting ... 

Is that in Network Manager (like the screenshot)?

If so, and you are using WPA encryption, I think that this is because your password has to be in HEX  (not ASCII) for Network Manager.  If this doesn't mean anything to you - it is HEX if it is 63-64 digits, ASCII can be any length.  The easiest way to fix this is to set a HEX code in your router's settings page.

---

### Post by bwtranch on 2007-12-29
Re: #18 Ah, must be settings. I believe that is what our friend is using. System -> Administration -> Network. I got on this thread to really try and learn some more and contribute what I can. I think just about everyone has issues on the wireless thing in Linux. If you don't you're lucky I think.

---

### Post by ugm6hr on 2007-12-29
@Gipsy25:
I don't want to confuse you, but perhaps it would be best if you clarified some facts before we all carry on advising in different directions:
1. What encryption are you using - WEP or WPA?
2. Is your password HEX or ASCII?
3. The output from
```
lspci
```

@bwtranch:
I am lucky (in Gutsy), but needed a bit of work with Feisty.  Network Manager is considered buggy by some (as it was for me in Feisty), but I've had no problems at all since Gutsy with it, so have kept it as default (I was a Wicd fan in Feisty).  The only thing it flounders with is hidden SSID networks (not a problem for me).

---

### Post by bwtranch on 2007-12-29
Re: #23 I totally agree. We need to all get on the same page. Going in too many directions and it is becoming confusing. Maybe after we solve this, we could work on my new graphics card problem. :)

---

### Post by bwtranch on 2007-12-29
You might find my little thread useful [http://ubuntuforums.org/showthread.php?p=4034873#post4034873](http://ubuntuforums.org/showthread.php?p=4034873#post4034873) This is how I got mine to work. :popcorn:

---

### Post by Gipsy25 on 2007-12-29
ROUTER:
im using 	Authentication: wep-open
		Encription: wep  (custom phrase) 
		channel 1
		dhcp is enable on the router
the router give me other options :
wep-shared
wep-psk
wpa-psk and wpa2-psk
wpa2-psk

on the computer I can see the the network
Wired network (realtek conductor)
Wireless network : gipsy 
Connect to other wireless network
Create new connection
Manual configuration

my network settings shows the Wireless connection:
under property 
“I have enable roaming mode”
ESSID = empty
pass: wpa personal

Now if I change the settings and disable “enable roaming mode”
it allows me to choose ESSID also can change the “password type” (either ASCII or hexadecimal).
Now I know that ASCII is 5 or 13 characters and hexad is 10 or 26 characters. To make it simple I'm using ASCII (5 characters).
Connections settings : automatic configuration (dhcp)  / then click ok. 
When I do this, and I go to the 2 little pc's next to the clock the wireless network is there no more (sorry I'm also learning English).  I can only see “wired configuration and manual configuration” 
 
The output from “lspci “ is the following 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 02)

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)


just as a recap I modified a file /etc/network/interfaces 

*********************************************
"Procedure to enable WPA Wireless in Ubuntu
To update the source list run the following command
sudo apt-get
sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome network-manager
sudo gedit /etc/network/interfaces
Comment out everything other than “lo” entries in that file and save the file
Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
sudo touch /etc/default/wpasupplicant
Reboot your system or use the following command
sudo /etc/init.d/dbus restart
Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.
After enterring all the details my wireless network was connected and working fine you can see in the following screen
So my file now looks like this 
auto lo

iface lo inet loopback


## iface eth1 inet dhcp


## auto eth1


## iface eth0 inet dhcp


## auto eth0


iface ath0 inet dhcp

wireless-key s: PASSWORD

wireless-essid gipsy


auto ath0

---

### Post by ugm6hr on 2007-12-29
OK. You have an ASCII passowrd on WEP encryption.

The poroblem may be the ASCII password - I have always used HEX with Netwrok Manager.  Perhaps change encryption on the router to OPEN (i.e. no encryption), and see if you can connect.  If yes - then try a HEX password with WEP.  I would actually recommend WPA in the long term (for increased secutriy).

I am not certain about your wifi chipset, which I think is:
> 
00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

I have never seen this one before.  This command will make it clear which is the wifi controller, and which are ethernet:
```
lshw -C network
```

Might need to do a bit of searching about this chipset...

EDIT:
```
lshw -C network
```
should return:
>   *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:27:12:5f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

Looks like this uses the madwifi drivers (successfully).  So there should not be a problem with the driver.  Try a HEX key (instead of ASCII).  The other thing to try is Wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)).

---

### Post by Gipsy25 on 2007-12-29
lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

gipsy@gipsy-ubu:~$ lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

---

### Post by ugm6hr on 2007-12-29
Re-read my post above (I have edited).

It is **lshw -C network**

Capital **C** is important.

---

### Post by Gipsy25 on 2007-12-29
Sorry im learning here is the info requested 

**********************
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0a:e6:07:6c:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wifi0
       version: 01
       serial: 00:18:e7:28:3f:bc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:2
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 00
       serial: 00:80:ad:c8:1f:87
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.65 latency=0 module=ne2k_pci multicast=yes

*********************************

---

### Post by Gipsy25 on 2007-12-30
The problem was resolved THANK YOU VERY MUCH TO ALL OF YOU FOR HELPING ME OUT HERE ... I REALLY APPRECIATE ...
wHAT I DID (I GUESS ...) was to install the WIcd as indicated before and that solved the problem .. now im wireless for first time and enjoying it ..

AGAIN THANK YOU GUYS FOR ALL THE ADVICE .. 
and i hope in the future i can help to someone the same way you guys helped me 

Regards
GIPSY

---

### Post by ugm6hr on 2007-12-30
Glad it is sorted!

Wicd is a good solution for many.

---

### Post by bwtranch on 2007-12-30
That's great! Hats off!!! See ya in the funny papers...

---

