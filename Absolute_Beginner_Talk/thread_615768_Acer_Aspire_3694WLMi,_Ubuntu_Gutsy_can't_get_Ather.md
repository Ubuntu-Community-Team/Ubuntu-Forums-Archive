---
title: "Acer Aspire 3694WLMi, Ubuntu Gutsy can't get Atheros wifi card workin........Help"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by PogMoThoin on 2007-11-17
Hey all,

Got a new laptop for work yest [(Link)]("http://www.laptopsdirect.ie/Acer_Aspire_3694WLMi_LX.AY90Y.253/version-1.asp") & immediately wiped Vista & installed Ubuntu Gutsy but i've not managed to get wi-fi card goin. No wireless adapter shows up under admin/network. My boss talked me through a few things last nite & it shows up as an Atheros (can't rem the exact model no) wifi card. I've restrictive drivers enabled in the repository but its still not working.

 I've installed ndisgtk to try to install windows drivers for it but the funny thing is that the laptop gets no mention on the list of products on [www.acer.com](www.acer.com) so i've no idea what exact wi-fi card it is.

I've also downloaded madwifi to my desktop but have no idea what to do from here.

Can some1 tell me the command again to scan the pci bus so I can at least put a name on this device to help me with my googling.

Is there any way of getting it going without the windows driver?

Anyone have any ideas?

Thanks in advance,

Pog.

---

### Post by Flying caveman on 2007-11-17
```
lspci
```

Probably a broadcomm 43xx chipset.

---

### Post by PogMoThoin on 2007-11-17
lspci gives me this
> 05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)



Any advise on what to do next?

---

### Post by PogMoThoin on 2007-11-17
Ok, downloaded a windows driver for the card & tried to use ndisgtk & ndiswrapper to install it, but my problem is that this driver is a .exe not a .inf. Does anyone know how to get it working as i've seen loads of threads asking how, but not found 1 that succeeded.

I've got madwifi downloaded to my desktop also, but don't know what to do with it from there.

Can someone please help or even advise. Google has not given me any answers.

---

### Post by daimaru on 2007-11-17
i guess your card is already runniing its just not set up right to work with your wireless network.
post your output form
iwconfig 
and
ifconfig
EDIT: sry but does your connection tool show up on the top left of your desktop (ubuntu) ? what happens when u click it dont u get all available networks? or at least the option to configure manually?

---

### Post by PogMoThoin on 2007-11-17
This is not a wifi configuration problem, the wifi card is there but not running. It does not show up under admin/network, but it is present on a scan of the pci devices. I need to use a different driver to get it running.

LOOK:
> colm@l33t-str33t-2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

colm@l33t-str33t-2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:E4:3D:C5  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fee4:3dc5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14364864 (13.6 MB)  TX bytes:2160566 (2.0 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88 (88.0 b)  TX bytes:88 (88.0 b)

colm@l33t-str33t-2:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
[COLOR="Red"]05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)[/COLOR]
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by PogMoThoin on 2007-11-17
Ok.......update,

I have tried to install madwifi-tools from synaptics, but it just hangs & does not download from there. I already have madwifi in a .tar.gz on my desktop which i downloaded earlier. Does anyone know how to install it from there.

Can someone please help

---

### Post by PogMoThoin on 2007-11-17
here is all the information on this device:
> 05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at d0000000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [60] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 <64us
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <512ns, L1 <64us
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
                Vector table: BAR=0 offset=00000000
                PBA: BAR=0 offset=00000000



Can someone help........PLEASE

---

### Post by overdrank on 2007-11-17
HI and this link may help it worked for me on feisty and some users on gutsy,
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
I have a acer and vista identified it as a 5007 and ubuntu says it is a 5006. Hope this helps 
Good luck!

---

### Post by PogMoThoin on 2007-11-17
Your link is wrong m8, can you fix it please

---

### Post by overdrank on 2007-11-17
> **PogMoThoin said:**
> Your link is wrong m8, can you fix it please

Fixed :oops:

---

### Post by PogMoThoin on 2007-11-17
Cheers for that m8,


OK, got ndiswapper & Xp drivers using the commands, i get as far as extracting the archives, this is the output i get
> colm@l33t-str33t-2:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-32-0.2/
ar5007eg-32-0.2/ar5007eg/
ar5007eg-32-0.2/ar5007eg/net5211.inf
ar5007eg-32-0.2/ar5007eg/ar5211.sys
ar5007eg-32-0.2/README
colm@l33t-str33t-2:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

What am i doing wrong? Can some1 lookover it & tell me whats wrong.

---

### Post by PogMoThoin on 2007-11-17
Anyone, Please :)

I cannot extract the arhive, must be something simple wrong. I've copied & pasted straight from that guide. Please help

---

### Post by daimaru on 2007-11-17
use 
```
tar xzvf ar5007eg-*.tar.gz
```
cause gzip

---

### Post by dysolve on 2007-11-17
DO NOT install ndiswrapper unless it a last resort, it has caused heaps of issue with other hardware in my laptop. Do you have a wireless card you can attach to the PCMCIA slot? if so plug it in and see if that gets the other card to show up under the network applet. I have found with Ubuntu that it does not handle wifi cards in the same way as windows and sometimes it has problems "wakeing" them up. if it shows up in the networking applet i think your machine is having trouble wakeing the card up. my fix was to get the latest bios which forced bios to keep wifi on.

best of luck David

---

### Post by PogMoThoin on 2007-11-17
> **daimaru said:**
> use 
```
tar xzvf ar5007eg-*.tar.gz
```
cause gzip

thats identical to the line i'm using, its the following line that doesn't work. Full code is here:
> tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz

output here when i copy & paste both lines in2 terminal:
> colm@l33t-str33t-2:~$ tar xzvf ar5007eg-*.tar.gz
ar5007eg-32-0.2/
ar5007eg-32-0.2/ar5007eg/
ar5007eg-32-0.2/ar5007eg/net5211.inf
ar5007eg-32-0.2/ar5007eg/ar5211.sys
ar5007eg-32-0.2/README
colm@l33t-str33t-2:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


---

### Post by daimaru on 2007-11-17
might have to use tar -xzvf 
but your line is not identical meaning you left out the "z"

i mean its a gzip file so you have to use this command to decompress it 
tar xfvz [ARCHIV].tar.gz
you could also just right click it in your window manager and select extract here ...
and if it still does not work you do not have the decompression program installed. so install it through synaptic or apt-get

---

### Post by daimaru on 2007-11-17
well your first archive decompressed fine 
why didn' you use tar xvfz on the ndiswrapper one? you just used tar xvf again. so it wont work.

---

### Post by PogMoThoin on 2007-11-17
No luck

>  tar -xvcf ndiswrapper-newest.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.


> tar xvcf ndiswrapper-newest.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.


Can you modify these lines to get them 2 work? have tried every combination with xvf, xvcf & -xvcf

> tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz

---

### Post by daimaru on 2007-11-17
are you trying to BS me here or what ???
either you always copy the wrong lines into your CODE section or you just can't read:.-.
i said USE THE Z option that is ZZZZZZZZZZZ no CCCCCCCC so your tar command should be 
"tar -xvzf not "tar -xvcf"  or any other combination with C in it. 

> tar -xvcf ndiswrapper-newest.tar.gz
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.

as you might be able to see it says **tar -xvcf ndiswrapper-newest.tar.gz**
so just to rule out anymore mistakes your lines of code should read (and please copy paste them to console)
```
[COLOR="Red"]
tar -xvzf ar5007eg-*.tar.gz
tar -xvzf ndiswrapper-newest.tar.gz[/COLOR]
```
to your console and execute it. if that still does not work re-download the tar.gz file and just for the fun of it post the download link to the file so i can try it on my computer.

ok i just downloaded this tar.gz file :[here]("http://heanet.dl.sourceforge.net/sourceforge/typo3/dummy-4.0.5.tar.gz")
because i was seriously doubting myself, i used tar -xzvf dummy-40.5.tar.gz on it and it unpacked without a problem so ... plz tell me that it does the same for you.

---

### Post by PogMoThoin on 2007-11-18
Here is the full output, I'm still having no luck, dunno what i'm doing wrong, but it doesn't work for me.
> colm@l33t-str33t-2:~$ wget [http://wifix.sourceforge.net/software.php?title=ndiswrapper](http://wifix.sourceforge.net/software.php?title=ndiswrapper)
--12:14:11--  [http://wifix.sourceforge.net/software.php?title=ndiswrapper](http://wifix.sourceforge.net/software.php?title=ndiswrapper)
           => `software.php?title=ndiswrapper'
Resolving wifix.sourceforge.net... 66.35.250.209
Connecting to wifix.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download) [following]
--12:14:12--  [http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download)
           => `ndiswrapper-1.49.tar.gz?download'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download) [following]
--12:14:12--  [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?download)
           => `ndiswrapper-1.49.tar.gz?download'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz) [following]
--12:14:13--  [http://heanet.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz](http://heanet.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz)
           => `ndiswrapper-1.49.tar.gz.3'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 200,113 (195K) [application/x-gzip]

100%[====================================>] 200,113      109.48K/s             

12:14:15 (109.27 KB/s) - `ndiswrapper-1.49.tar.gz.3' saved [200113/200113]

colm@l33t-str33t-2:~$ wget [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)
--12:14:45--  [http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz)
           => `ar5007eg-32-0.2.tar.gz.6'
Resolving blakecmartin.googlepages.com... 72.14.203.118
Connecting to blakecmartin.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 285,621 (279K) [application/octet-stream]

100%[====================================>] 285,621       47.74K/s    ETA 00:00

12:14:52 (49.77 KB/s) - `ar5007eg-32-0.2.tar.gz.6' saved [285621/285621]

colm@l33t-str33t-2:~$ 
colm@l33t-str33t-2:~$ tar -xvzf ar5007eg-*.tar.gz
ar5007eg-32-0.2/
ar5007eg-32-0.2/ar5007eg/
ar5007eg-32-0.2/ar5007eg/net5211.inf
ar5007eg-32-0.2/ar5007eg/ar5211.sys
ar5007eg-32-0.2/README
colm@l33t-str33t-2:~$ tar -xvzf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
colm@l33t-str33t-2:~$ 


Please Help, I've spent hours at this & still no luck

---

### Post by PogMoThoin on 2007-11-18
Ok

Got it going by installing ndisgtk & extracting the file manually to my desktop & using ndisgtk(GUI for ndiswapper) to add the driver. It works now but i had probs connecting using WPA & had to use WEP, Problem is that my mam, brother & few friends all use WPA & I'll need WPA in their houses. Any ideas?

---

### Post by daimaru on 2007-11-20
thats kind of weird. wpa should work, but i haven't tried ndsiwrapper so i don't really know if it works with wpa. I can only point you in the direction.
on my laptop using backtrack I use wpa_supplicant to get wpa running same on my zaurus, because it only supports WEP. you have to install wpa_supplicant and edit the /etc/wpa_supplicant.conf file manually inserting your network details and wpa key. its pretty complex so I would suggest you try finding a different way to get the normal driver running.

---

### Post by daimaru on 2007-11-20
EDIT: heres a link to install madwifi drivers if they are not already preinstalled in gutsy, so first just try using them if they're not installed follow the link  [link]("http://ubuntuforums.org/showthread.php?t=485579&highlight=installing+madwifi+driver")


ok i'll give it a try but i can not guarantee that this will work. 

to get WPA2 CCMP PSK working:
(i hope that gutsy as wpa_supplicant preinstalled, I'm not sure but just try it otherwise maybe a sudo apt-get install wpa_supplicant will do the trick)

create a file called wpa_supplicant.conf in your /etc directory

```
sudo gedit /etc/wpa_supplicant.conf
```

paste the following into that file

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
# ap_scan=2 maybe 0 or 1 just try
ap_scan=2
fast_reauth=1

network={
ssid="your network SSID goes here"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
group=CCMP
psk="your passprase for wpa2 network goes here"
}
```

next make the file executable
```
chmod 777 /etc/wpa_supplicant.conf
```

then execute this command from terminal to connect to your wpa network
(you might have to exchange the -iath0 with your wifi device name. so -ieth0 of -iwlan0 you get the right one my executing iwconfig in terminal)

this should start the network and connect to your accesspoint. 
if it works you can add the -B option to the line which makes it run in the background 
```
wpa_supplicant -w -Dmadwifi -iath0 -B -c/etc/wpa_supplicant.conf
```

the only thing is that this works if your using the madwifi dirver ( -Dmadwifi ), so if you can't install that one I don't know how ndiswrapper should work with this.

hope this works. credit goes to Xploitz
heres another thread on ubuntuforums that might help [http://ubuntuforums.org/archive/index.php/t-392666.html]("http://ubuntuforums.org/archive/index.php/t-392666.html")

---

### Post by braveerudite on 2008-05-18
Dude I have same exact problem... How did you get is to work?  

rambo@Ubuntu64:~$ echo &#8220;blacklist ath_pci&#8221; | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for rambo: 
&#8220;blacklist ath_pci&#8221;
rambo@Ubuntu64:~$ wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
--17:30:03--  [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
           => `ar5007eg-64-0.2.tar.gz.3'
Resolving blakecmartin.googlepages.com... 209.85.141.118
Connecting to blakecmartin.googlepages.com|209.85.141.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 369,404 (361K) [application/octet-stream]

100%[====================================>] 369,404      138.38K/s             

17:30:16 (138.03 KB/s) - `ar5007eg-64-0.2.tar.gz.3' saved [369404/369404]

rambo@Ubuntu64:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-64-0.2/
ar5007eg-64-0.2/ar5007eg/
ar5007eg-64-0.2/ar5007eg/net5211.inf
ar5007eg-64-0.2/ar5007eg/net5211.cat
ar5007eg-64-0.2/ar5007eg/ar5211.sys
ar5007eg-64-0.2/README
rambo@Ubuntu64:~$ 
rambo@Ubuntu64:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
rambo@Ubuntu64:~$ 


I notice you got iy to work but I didn't understand how you did it... please help.

---

