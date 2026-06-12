---
title: "Edgy slower than XP? I must have a problem..."
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-21
OK - I know Ubuntu can be faster than the speed of light, but I am not interested in getting there - I would just appreciate a little (understandable...) help in getting mine up to the speed of my XP.

I recently installed 6.10 Edgy to dual-boot with XP/SP2 on my modest PC with AMD Athlon XP 3000+ 2.16GHz & only 256Mo RAM. I know that is not much.
I also live happily with 512K ADSL, so you can see I am not asking for a miracle.

This set-up has always been adequate for me (after I switched from Norton to Active Virus Shield!) & in XP it continues to be OK even after installing Ubuntu.

Ubuntu itself normally seems to be about equivalent to XP, until I add Internet connectivity by Ethernet cable, at which point it becomes painfully slow, even if I am not using any Internet application.

For instance:
To open Terminal - 26sec
Open OOo writer or calc - 27sec
and internet applications:
Open Evolution - 45sec
Open new pages in Firefox - 10 to 60sec

All this is about 10 times longer than OOo & Firefox under XP.
XP speed does not seem affected by adding ethernet or usb-wifi.

I looked in System Monitor & it seemed pretty empty to me (no experience) with RAM not topping out even while openning applications or browsing.
Screenshots attached.
The Resources shots show opening OOo writer with nothing else running.
....with & without ethernet cable.
Don't know why there is any internet activity shown...

Any suggestions as to what to look at next?
I mean just to get it to normal state, not to tune it up.
.....preferably in beginner baby-talk! 

Thanks!  :)

---

### Post by riven0 on 2006-12-21
Definitely sounds like a networking issue. What network card are you using?

Try copying and pasting this command in the terminal and then post the output here:

> sudo /etc/init.d/networking restart

Edit: Oh, and paste the output of this command, too:

> cat /etc/network/interfaces

---

### Post by wpshooter on 2006-12-21
Did you make a /linux swap partition on your hard drive ?

---

### Post by 2CV67 on 2006-12-22
Thanks for your replies!

Yes, I have a 517Mb swap partition at /dev/hda2 - it shows on the "resources" screenshots but not on the "file system" tabs. Is that normal?

From XP, I think my network card is:
"Realtek RTL 8139/810x Fast Family Ethernet NIC"

Here are the dumps from the 2 manips you suggested.
These are with ethernet cable connected (& working OK) but USB-WLAN disconnected.
I blanked out part of the WEP code.

:::::::::::::::::::::::::::::::::::::
[I]chris@DESKTOP:~$ sudo /etc/init.d/networking restart 
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4458
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:5b:00:29:37
Sending on   LPF/eth0/00:11:5b:00:29:37
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:5b:00:29:37
Sending on   LPF/eth0/00:11:5b:00:29:37
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCADDRT: File exists
bound to 192.168.1.10 -- renewal in 350791 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]
chris@DESKTOP:~$ 

:::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 212.129.9.68
wireless-essid DW-B-200-3d555
wireless-key 260E**********************

auto wlan0
chris@DESKTOP:~$ [/I]

::::::::::::::::::::::::::::::::::::::::::::

Hope that means more to you than it does to me...

Thanks again!

---

### Post by 2CV67 on 2006-12-24
I have now progressed from ethernet connection to USB Wifi connection (very long story...) and note the same effect - when the connection is OK, then opening everything else slows to a crawl.
Whenever the connection is not OK (but still physically wired up) then things run at normal speed.
In fact I can tell from the speed of getting from log-in to desk, whether the connection will be OK or not.

I removed Wifi-radar & Network Manager which I had been trying at various times, but that did not make any (much?) difference.

Suggestions?

What to try next?

Thanks guys! :)

---

### Post by orb9220 on 2006-12-24
Most issues of slow apps or desktop threads I have seen have to do with having the right video drivers installed. The default are not 3d and are not optimized for the paticular card.

Sorry couldn't be more help.

---

### Post by riven0 on 2006-12-24
That can't be right. Your network didn't restart. :confused: 

> **2CV67 said:**
> 
chris@DESKTOP:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 212.129.9.68
wireless-essid DW-B-200-3d555
wireless-key 260E**********************

auto wlan0
chris@DESKTOP:~$ [/I]



Okay, let's try this: 

> sudo gedit /etc/network/interfaces

Now change the last part of the file to look like this:

> iface wlan0 inet dhcp
#address 192.168.1.9
#netmask 255.255.255.0
#gateway 212.129.9.68
wireless-essid DW-B-200-3d555
wireless-key 260E**********************

I'm going on the assumption that perhaps you may not have a static address. Not sure if this is going to work since I don't have wireless, but it doesn't hurt to try.

---

### Post by 2CV67 on 2006-12-25
Maybe I should start again, as I have made several changes since the original post, notably shifting from ethernet to usb-wifi & dropping wifi-radar & network manager, as well as incorporating numerous updates.

So, now I am using usb-wifi, I still notice very slow performance, typically opening new applications, whenever the wifi connection is OK (even when no internet applications are running) but much quicker behaviour when the wifi connection is no good, either by physically disconnecting the usb-wlan or by disabling 'Wireless Connection' in Network Settings.

Examples of slow performance.  (Quick performance with usb-wlan disconnected - in brackets)
Login to clean desk - 60sec (11sec)
Open 'System Monitor' - 12sec (1sec)
Open 'Terminal' - 12sec (1sec)
Open OOotext - 23sec (12sec)

I tried your suggestion of hashing out 3 lines in /etc/networking/interfaces (without understanding why...) so the new situation is:[I]
::::::::::::::::::::::::::::::::::::::

chris@DESKTOP:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
#address 192.168.1.9
#netmask 255.255.255.0
#gateway 192.168.1.1
wireless-essid DW-B-200-3d555
wireless-key restricted 260E*****************
auto wlan0
chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::::::::::::::

...but did not find any difference in performance or anything else!

Normally I should be set up for DHCP not static address, I think.

For the moment I have left the hashes in place.

Grateful for any other ideas & ready to try anything....

Thanks ! :)

---

### Post by riven0 on 2006-12-25
Alright, let's try this from the very top now. :) 

First, post the output of:

>  sudo lshw -businfo

This way we know what wireless card you're using. Now, lets try to reconfigure the wireless network:

> sudo iwconfig

Post the output of that command, too. If you have a working wireless device it should reconfigure. If not, we can try reinstalling the drivers.

---

### Post by 2CV67 on 2006-12-26
Hi riven0 & thanks for your patience! :D 

Here are the printouts of the 2 manips you requested:
::::::::::::::::::::::::::::::::::::

[I]chris@DESKTOP:~$ sudo lshw -businfo 
Password:
Bus info      Device     Class          Description
===================================================
                         system         Aspire T120
                         bus            E22M
                         memory         BIOS
cpu@0                    processor      AMD Athlon(tm) XP 3000+
                         memory         L1 cache
                         memory         L2 cache
                         memory         System Memory
                         memory         None
                         memory         None
pci@00:00.0              bridge         VT8378 [KM400/A] Chipset Host Bridge
pci@00:01.0              bridge         VT8237 PCI Bridge
pci@01:00.0              display        RV280 [Radeon 9200 SE]
pci@01:00.1              display        RV280 [Radeon 9200 SE] (Secondary)
pci@00:0a.0              communication  HSF 56k HSFi Modem
pci@00:0d.0              bus            IEEE 1394 Host Controller
pci@00:0e.0   eth0       network        RTL-8139/8139C/8139C+
pci@00:10.0              bus            VT82xxxxx UHCI USB 1.1 Controller
usb@1         usb1       bus            UHCI Host Controller
usb@1:1       scsi0      storage        USB Storage Device
scsi@0:0.0.0  /dev/sda   disk           USB Storage-CFC
              /dev/sda   disk           
scsi@0:0.0.1  /dev/sdb   disk           USB Storage-SMC
              /dev/sdb   disk           
scsi@0:0.0.2  /dev/sdc   disk           USB Storage-MMC
              /dev/sdc   disk           
scsi@0:0.0.3  /dev/sdd   disk           USB Storage-MSC
              /dev/sdd   disk           
usb@1:2                  generic        HP ScanJet 4470c
pci@00:10.1              bus            VT82xxxxx UHCI USB 1.1 Controller
usb@2         usb2       bus            UHCI Host Controller
usb@2:1                  generic        Generic USB device
usb@2:2                  input          Microsoft IntelliMouse
pci@00:10.2              bus            VT82xxxxx UHCI USB 1.1 Controller
usb@3         usb3       bus            UHCI Host Controller
pci@00:10.3              bus            USB 2.0
usb@4         usb4       bus            EHCI Host Controller
pci@00:11.0              bridge         VT8235 ISA Bridge
pci@00:11.1              storage        VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
ide@0         ide0       bus            IDE Channel 0
ide@0.0       /dev/hda   disk           WDC WD1200BB-22FTA0
ide@0.0,1     /dev/hda1  disk           W95 FAT32 (LBA) partition
ide@0.0,2     /dev/hda2  disk           Linux swap / Solaris partition
ide@0.0,3     /dev/hda3  disk           Linux filesystem partition
ide@0.0,4     /dev/hda4  disk           W95 FAT32 partition
ide@1         ide1       bus            IDE Channel 1
ide@1.0       /dev/hdc   disk           DVD-ROM DVD-16X6S
              /dev/hdc   disk           
ide@1.1       /dev/hdd   disk           HL-DT-ST DVDRAM GSA-4082B
              /dev/hdd   disk           
pci@00:11.5              multimedia     VT8233/A/8235/8237 AC97 Audio Controller
              wlan0      network        Wireless interface
chris@DESKTOP:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3d555"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4B:84:34:15   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Encryption key:260E-A904-9B2D-48D1-0B10-A877-73   Security mode:restricted
          Power Management: off
          Link Quality=0/0  Signal level=50/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::::::::::::::

I don't see the wireless card there, do I?

Actually WLAN Dongle is PQP-WU221L S/N24W0097350.
Windows sees it as: ATMEL USB FastVNET(505A)
lsusb sees it as ID 03eb:7614 Atmel Corp. :
:::::::::::::::::::::::::::::
[I]
chris@DESKTOP:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 03eb:7614 Atmel Corp. 
Bus 002 Device 003: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1019:0c55  
Bus 001 Device 004: ID 03f0:0805 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
chris@DESKTOP:~$ 
[/I]::::::::::::::::::::::::::::::::::::

Note I have the same (slow) behaviour with ethernet & with usb-wifi but I have now physically removed the ethernet cable & also disabled 'Wired Connection' in Network settings.

Thanks for any lead to try! :)

---

### Post by Dafydd on 2006-12-26
> **2CV67 said:**
> Note I have the same (slow) behaviour with ethernet & with usb-wifi but I have now physically removed the ethernet cable & also disabled 'Wired Connection' in Network settings.

I have a cheeky answer - try a new distribution! I only used Ubuntu until Edgy but have switched to Vector Linux for day-to-day computing because Vector is sooooo fast. It's great - you click on a program and it opens up straight away (almost). Ubuntu was never that fast (I have 512MB RAM).

I still use Ubuntu though because I have not found some software in the Vector/Slackware repositories... Probably I'll be back to Ubuntu when I have more RAM or a new machine.

Dafydd

---

### Post by 2CV67 on 2006-12-27
I just saw that Warmspell in this thread:[http://www.ubuntuforums.org/showthread.php?t=317242](http://www.ubuntuforums.org/showthread.php?t=317242)
had my problems & fixed them by (quote):
:::::::::::::::::::::::::::::::::::::[I]
"Thanks kd_pease - that solved the slow app startup problem!
My /etc/hosts originally read
127.0.0.1 localhost
127.0.1.1 d11.123ab
(and then some IPv6 stuff, and then amazingly it included the fixed addresses of d8 and nas2).
Now I've changed it to read
127.0.0.1 localhost d11 d11.123ab
and deleted the 127.0.1.1 line.

System startup (from login to fully working desktop) is now about 1 second (was more like 30 - I didn't mention that), and app startup is easily less than a second. Bravo!"[/I]
::::::::::::::::::::::::::::::::::

Sounds good to me, but I would really appreciate knowing if I should do the same, or similar.

My /etc/hosts currently looks like this:
::::::::::::::::::::::::::::::::::::::::
127.0.0.1 localhost
127.0.1.1 DESKTOP..NEUGARTHEIM
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
:::::::::::::::::::::::::::::::::::::::::::::
Hostname is: DESKTOP.
:::::::::::::::::::::::::::::::::::::::::::

What, if anything, should/could I remove?
NOTE I am a noobie, so need clear instructions, please!

Thanks for all/any help! :D

---

### Post by riven0 on 2006-12-27
> **2CV67 said:**
> I just saw that Warmspell in this thread:[http://www.ubuntuforums.org/showthread.php?t=317242](http://www.ubuntuforums.org/showthread.php?t=317242)
had my problems & fixed them by (quote):
:::::::::::::::::::::::::::::::::::::[I]
"Thanks kd_pease - that solved the slow app startup problem!
My /etc/hosts originally read
127.0.0.1 localhost
127.0.1.1 d11.123ab
(and then some IPv6 stuff, and then amazingly it included the fixed addresses of d8 and nas2).
Now I've changed it to read
127.0.0.1 localhost d11 d11.123ab
and deleted the 127.0.1.1 line.

System startup (from login to fully working desktop) is now about 1 second (was more like 30 - I didn't mention that), and app startup is easily less than a second. Bravo!"[/I]
::::::::::::::::::::::::::::::::::

Sounds good to me, but I would really appreciate knowing if I should do the same, or similar.

My /etc/hosts currently looks like this:
::::::::::::::::::::::::::::::::::::::::
127.0.0.1 localhost
127.0.1.1 DESKTOP..NEUGARTHEIM
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
:::::::::::::::::::::::::::::::::::::::::::::
Hostname is: DESKTOP.
:::::::::::::::::::::::::::::::::::::::::::

What, if anything, should/could I remove?
NOTE I am a noobie, so need clear instructions, please!

Thanks for all/any help! :D

Hmm, okay, I guess you can try that. So, first make a backup of your hosts file:

> sudo cp /etc/hosts /etc/hosts.backup

Now open it:

> sudo gedit /etc/hosts

Delete everything and replace with this:
> 
::::::::::::::::::::::::::::::::::::::::
127.0.0.1 localhost
#127.0.1.1 DESKTOP..NEUGARTHEIM

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
:::::::::::::::::::::::::::::::::::::::::::::

If that doesn't work, try this instead:

> ::::::::::::::::::::::::::::::::::::::::
127.0.0.1 localhost
127.0.0.1 DESKTOP

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
::::::::::::::::::::::::::::::::::::::::::::

See if it works. If not, I guess we can do exactly what the other guy did, I just have no idea what *d11 d11.123ab* is and whether that something unique to his own connection.

---

### Post by 2CV67 on 2006-12-27
Thanks, riven0, for that detailed reply!

In fact that did not fix it, but by related playing around I have just stumbled on the solution, without understanding anything.

I simply rewrote the first line as:
127.0.0.1 localhost DESKTOP.
where "DESKTOP." is the Host Name already present in /etc/hostname file.
I suppose that is what Warmspell did too?

This works perfectly - opening applications is now as quick with connection as without - and I rechecked the change a couple of times to make sure the effect was 100%.

In the meantime, I had tried deleting the ip6 lines & the 127.0.0.1 line - with no effect.

Any explanation - for the problem or for the solution - gratefully received!

Anyway - I'm Happy :D :D

---

### Post by mtbsoft on 2007-08-31
Oh... what can I say, I am truly in the presence of Gods!  2CV67 and riven0, thank you, thank you, thank you, thank you!

I've been suffering the very same problem for about a week now and been crawling throught the threads, looking for a solution and trying all sorts of things, when I came across this thread.  The rewrite of the first line of my hosts file fixed it for me too - even gedit was taking fifteen seconds to come up and VM was over a minute, now it is mere seconds.

Please accept this bucket of kudos and get someone to pat you on the back on my behalf.

---

