---
title: "Problem connecting to Internet"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by sunumbrella on 2007-07-10
Hi.
I've just installed Ubuntu 7.04. I found that my wireless network adaptor couldn't be detected and from having a quick search on how to make it work, I was overwhelmed with how complicated it looked without internet access, so I bought a Ralink USB adaptor which was recommended as being very linux-friendly. However, I can now get it to detect the network sometimes, but when it tries to connect it can't. I'm sure it's really close to working but there's probably something simple missing. Please help.

For anyone who can help me, 
Computer specs: Pentium 4 desktop with 160GB hard drive, 2GHz CPU

Network specs: EDIMAX wireless network adaptor 802.11g
                         Ralink rt73 chipset
                         logical name: wmaster0/wlan0
                         network essid: usr9106
                         dchp address
                         no WEP key

I'm not sure what other info might be useful. Does it matter what kind of router I use? I'm using a US Robotics ADSL SureConnect USR9106 4-port by the way.

If you can help, please give really basic step-by-step instructions and realise I can't connect to the internet from Linux (I have Windows XP on a separate hard drive that can connect if I really need to, or another computer nearby)

Thanks.

---

### Post by dmfield on 2007-07-10
There are linux drivers, but having had a similar chipset on another USB Dongle, i would use the Windows drivers which came with the product, and NDISwrapper

If you're not familiar with NDISwrapper, it uses the windows drivers in linux to get network cards to work..

Let me know if you want to know how to get this working, the basic syntex would be to find the XP drivers on the CD whcih came with the Wifi card

Copy them to you linux PC

navigate using the terminal to the folder they are in

then type in 
> [B]
ndiswrapper -i <*drivername*>.inf[/B]

The driver will generally be a .inf file which typing ls -l will show a direcotry listing (for a broadcomm for example its bcmwl5.inf)

> ndiswrapper -l 

If you don't have ndiswrapper then load [automatix]("http://ubuntuforums.org/www.getautomatix.com/wiki/index.php?title=Installation"), and load it from here.. also the network manager app will make using the Wifi a lot easier (in my humble opinion)
will show you if the driver is loaded..

as i said, i can give you more assistance if you need it.

---

### Post by sunumbrella on 2007-07-12
Hi.
I tried what you suggested dmfield but it didn't work because 1) there was no .inf windows driver, and 2) apparently I didn't have ndiswrapper. I've downloaded automatix and I'll give that a go but are you sure I can't use the debian drivers that came with the adaptor?

The CD has a Windows drivers folder with a autorun.inf setup file and 1.0.2.0.exe
There is also a Debian drivers folder with the following files:
  iwpriv_usage.txt
  load
  readme
  rt73.bin
  rt73.ko
  rt73sta.dat
  unload
  RT73STAV1000_k2.6.8-2-386_DBN31.tar.gz

What do I do with automatix? And does it have any dependencies that I should know about?

Thanks

---

### Post by dmfield on 2007-07-12
Hi, 

OK, that EXE in the windows folder, you need to decompress it with 

unzip -r 1.0.2.0.exe

This should decompress the file, and you should see some sort of Drivers folder..

Alternativly, you could use the Debian drivers, i'm sure the readme document has instructions on how to install the files? 

I suggested the ndiswrapper was as i know it works, and i seem to remember the debian drivers being a bit of a pain to setup.. but this may have changed.

---

### Post by sunumbrella on 2007-07-13
Problem 1) 
I tried to install automatix but I got a message saying that I need python 2.4, but I checked synaptic package manager and I already have python 2.5 installed. I don't know how to make automatix work

Problem 2)
I tried to unzip that 1.0.2.0.exe file like you said and I got two error messages; first that -r is not a valid switch, and second that the exe cannot be unzipped (even without any switches)

Problem 3)
I extracted the debian driver .tar.gz and inside was a copy of the other files I mentioned above in the Debian folder. I read the readme file and this is the summary (I'm running a 2.6 series kernel by the way)

> 
**For 2.4 series kernel:**
a. $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz  (the name of my driver is actually RT73STAV1000_K2.6.8-2-386_DBN31.tar.gz)
     go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory (no directory called module in the extracted folder)

b.  use 'chmod' command to change access right of following script files : 'load', 'unload', Configure' (no Configure script file in folder)

c.  run 'cp Makefile.4 Makefile'
d.  #make config
e.  $make all
f.  $cp rt73.bin /etc/Wireless/RT73STA/
g.  $load


**For 2.6 series kernel:**
a.  go to 'STA/Module' directory  (I can't find it)
     run 'cp Makefile.6 Makefile'

b.  $make all
c.  cp rt73.bin /etc/Wireless/RT73STA/  (folder doesn't exist, I assume it would be created during make)

d.  run '/sbin/insmod rt73.ko' as root
     run '/sbin/ifconfig rausb0 inet YOUR_IP up'

Then there are instructions about configuration


So I don't really understand how to follow the instructions for the debian driver when I can't find the folders or the files don't exist.

Celebration 1) Using advice from another forum question, I installed ndiswrapper-common and ndiswrapper-utils. Is that all I need to make ndiswrapper work, or do I need to install ndiswrapper-1.47.tar.gz as well?

So, I'm totally confused now as I've tried all the different ways I can think of (which is not many, lol).  I really appreciate your help and any more suggestions would be welcome.

---

### Post by dmfield on 2007-07-13
If you type sudo ndiswrapper in to the console and get the help feedback, you are good to go

my sincearest apologies, its 
unzip -a *filename*

---

### Post by sunumbrella on 2007-07-14
Hi.
I downloaded the right debian driver and installed it according to the readme file instructions. I modified the configuration file rt73sta.dat and saved it. I used the network manager to set up the network with a static address.

I checked the /etc/network/interfaces file and it said:
> 
...
iface wlan0 inet static
auto wlan0


In the terminal I typed 'iwconfig' and this is the output:
> 
**lo **               no wireless extensions
**eth0**           no wireless extensions

**wmaster0**   
IEEE 802.11g                         Frequency: 2.462 GHz
                   RTS thr: off                           Fragment thr=2346 B

**wlan0  **      
 IEEE 802.11g                         ESSID:"USR9106"
                  Mode: Managed                     Frequency: 2.462 GHz            Access Point: 00:C0:49:5D:89:C1
                  RTS thr: off                            Fragment thr=2346 B
                  Link Quality: 0                        Signal level: 0                          Noise level: 0
                  Rx invalid nwid: 0                   Rx invalid crypt: 0                   Rx invalid frag: 0
                  Tx excessive retries: 0           Invalid misc: 0                         Missed beacon: 0                   


I also tried typing 'sudo ifconfig wlan0 up' and got no message.

What else do I need to do to get it working?

---

### Post by dmfield on 2007-07-14
Excellent news,  just out of curiosity, could you paste the wholw /etc/network/interfaces

should be a little longer than what you posted

also if you type 
> 
sudo iwlist scan

does it come back with anything? it should do, this is a check to see if its actually seeing the wireless network..

If you have the opportunity to use DHCP just for testing, that may at least again, eliminate  other issues...

---

### Post by sunumbrella on 2007-07-17
Hi. 
Ok, so with wlan0 set to static, this is what I get from the /etc/network/interfaces file:
> 
auto lo
iface lo inet loopback
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid USR9106
auto wlan0

And **$ sudo iwlist scan**:
> 
lo  Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning: Operation not supported
wlan0  No scan results


So then I changed the wlan0 to dhcp like you suggested and /etc/network/interfaces read:
> 
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
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid USR9106
auto wlan0
auto eth0

And **$ sudo iwlist scan** with wlan0 set to dhcp:
> 
lo  Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning: Operation not supported
wlan0  Scan completed:
  Cell 01 - Address: 00:C0:49:5D:89:C1
  ESSID:"USR9106"
  Mode:Master
  Frequency:2.462 GHz
  Signal level=-140dBm  Noise level=-160dBm
  Encryption key:off
  Extra:tsf=00000052038b7648


So is the network being detected properly?

---

### Post by dmfield on 2007-07-17
OK, so with DHCP you get 

>  wlan0  Scan completed:
  Cell 01 - Address: 00:C0:49:5D:89:C1
  ESSID:"USR9106"
  Mode:Master
  Frequency:2.462 GHz
  Signal level=-140dBm  Noise level=-160dBm
  Encryption key:off
  Extra:tsf=00000052038b7648


but with a static IP you get

>  wlan0  No scan results


So the good news at least is, that with DHCP Enabled, you do get to see the Wireless network

> USR9106

Which is a start.

OK, revert back to DHCP, run sudo iwlist scan again, just to ensure the same result, then type in

> sudo ifconfig wlan0

And see if your being assigned an IP Address..

If it is, see if you can ping the router.

> ping *<ip address or router>*

or at very least ping google

> ping [www.google.com](www.google.com)

One reason it might not be working, with the static IP is, that some routers are setup to have DHCP Assigned to all IP Addresses, and you might need to setup a range of IP Addresses (The first 10 say) which are outside the DHCP Scope, without knowing your router, and setup thats a little outside this scope.

Why did you need to use a static IP Address? 


You could edit your **/etc/network/interfaces** file to look like this
[INDENT]> auto wlan0
iface wlan0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        [/INDENT]Let me know what router you have, I used to work for an ISP so i've got a bit of experience with some of them.

---

### Post by dmfield on 2007-07-17
I'm going to take a guess that you have a 
u.s. robotics, inc

Internet router?

---

### Post by sunumbrella on 2007-07-18
You're right, I'm using a US Robotics ADSL SureConnect USR9106 4-port router.

With the IP address set as DHCP:

> 
**sudo ifconfig wlan0**

wlan0 Link encap:Ethernet  HWaddr 00:0E:2E:CD:7D:31
_inet addr:192.168.1.4 _ Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::20e:2eff:fecd:7d31/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:51 errors:0 dropped:0 overruns:0 frame:0
TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:13763 (13.4 KiB)  TX bytes:5847 (5.7 KiB)


It looks like it found my IP address. I pinged the IP and got a reply, then pinged google and got the following similar reply (it got to icmp_seq=52 then I pressed ctrl-c and got the statistics summary, I'll just record the first three packets received to give an indication of the results - the rest of the packets were similar)

> 
**ping [www.google.co.nz](www.google.co.nz)**

PING [www.l.google.com](www.l.google.com) (66.249.89.99) 56(84) bytes of data.
64 bytes from jp-in-f99.google.com (66.249.89.99): icmp_seq=3 ttl=246 time=193 ms
64 bytes from jp-in-f99.google.com (66.249.89.99): icmp_seq=6 ttl=246 time=193 ms
64 bytes from jp-in-f99.google.com (66.249.89.99): icmp_seq=9 ttl=246 time=195 ms
...
--- [www.l.google.com](www.l.google.com) ping statistics ---
52 packets transmitted, 20 received, 61% packet loss, time 59521ms
rtt min/avg/max/mdev = 189.418/195.048/211.430/4.232 ms


That seems to be quite a high packet loss rate, but at least some packets are being received.

As for why I was using a static IP address, it was just to see if by providing the information it might be able to find it easier. I guess not.

---

### Post by dmfield on 2007-07-18
Well your working, thats a start... is this ok? or would you like to setup the static IP, personally i would use DHCP just because its easier to move around networks (if your using a laptop, if your using a desktop, its a bit too heavy:))

The packet loss, is a bit high, do you have a wall, doors or anything like that between the PC and the Wifi box. Or a bit of a distance. 

As you'll know from reading the net about wifi, things such as distance, walls, can cause signal loss..

---

### Post by sunumbrella on 2007-07-20
I'm happy using DHCP and yes there are two walls between my desktop PC and the router, but only about 12m between them in a straight line.

I just had the strangest thing happen: I went into Linux and I got a message saying there were two system updates to download, I said ok, download them, it did so successfully, but when I tried to connect to the Internet using the network manager or Firefox, I couldn't connect. Furthermore, when I restarted the computer so I could use Windows, there were a heap of error messages relating to the network before it actually restarted (I'm not sure how to access the log files, otherwise I would show you the messages).

So I'm not sure if it actually connected briefly to download the updates, or whether they came from somewhere else in the system? And what else do I need to do to connect to the Internet? I was so excited for a minute, and then so disappointed.

---

### Post by sunumbrella on 2007-07-21
I don't know what I've done, but I can't ping as much as I could before:

ping 192.168.1.4 (router) = ok
ping 192.168.1.1 (gateway) = "destination host unreachable"
ping [www.google.com](www.google.com) = "unknown host www.google.com"

The /etc/network/interfaces file is correct
iwconfig still gives me the same response as before
iwlist scan still gives me the same response as before

sudo ifconfig wlan0:
```

wlan0     Link encap:Ethernet  HWaddr  00:0E:2E:CD:7D:31
              inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
              inet6 addr: fe80::20e:2eff:fecd:7d31/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:365 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
              RX bytes:0 (0.0 b)  TX bytes:86278 (84.2 KiB)

```

No packets being received.

My understanding is that the communication between the access-point (my computer) and the router is ok, but the communication between the router and the WWW is broken somewhere.

---

### Post by dmfield on 2007-07-22
Sounds to me like your ADSL connection is down? Or did you install a frewall?

If its your ADSL turn off the router for 1 minute, and turn it back on again..

usually the router is the default gateway, and not on another IP.. are you sure 192.168.1.4 is the router?

---

### Post by sunumbrella on 2007-07-24
Hi.
I'm sure my ADSL wasn't down: went I went into windows after restarting the computer, the internet was working fine. I haven't installed any firewalls either.

So I've set up the wlan0 to be dhcp. Now, these are the IP addresses and the results when I ping them:

address 192.168.1.4     "From 169.254.7.234 icmp_seq=1 Destination Host Unreachable"
netmask 255.255.255.0     "connect: Invalid argument"
network 192.168.1.0     "From 169.254.7.234 icmp_seq=1 Destination Host Unreachable"
broadcast 192.168.1.255     "From 169.254.7.234 icmp_seq=1 Destination Host Unreachable"
gateway 192.168.1.1     "From 169.254.7.234 icmp_seq=1 Destination Host Unreachable"

However, I went into Network Tools and looked at the list of interfaces and found wlan0 and wlan0:avahi. When  I selected wlan0:avahi and clicked "configure" I got an error message saying that the interface does not exist. Yet it displayed a list of IP addresses that I tried pinging:
IP = 169.254.5.187     "From 169.254.5.187 icmp_seq=1 ttl=16 time=0.07ms"
netmask = 255.255.0.0     "connect: Invalid argument"
broadcast = 169.254.255.255     "do you want to ping broadcast? Then -b"

What has happened do you think?

---

### Post by kevdog on 2007-07-24
Sorry to chime in in the middle of your parade, but I thought that actually using the serial monkey drivers for the rt73 chipset worked a lot better than the ndiswrapper approach -- particularly with feisty as there is known to be some issues with ra chipsets (where they worked better in Edgy).

I know this is kind of taking a step backwards, but if you would like to try, I would help you proceed.

---

### Post by sunumbrella on 2007-07-29
Hi. I haven't given up yet, but now my ADSL router really is down and I can't connect to the internet on any computer at home. My ISP said it was a problem with the router, not their service (PS. dmfield if you're there, you said you worked for an ISP, do you know what it means when a USRobotics router has a flashing ADSL light and the WAN IP light is off?).

Before it crashed though, I downloaded the serial monkey rt73 drivers and installed it but it said something about having to delete or move some configuration files because I still have the original debian driver for the rt73 that came with my wireless adaptor in the system. 

Do I need to uninstall the other driver first, or since I have no important files in Ubuntu yet would it be easier to reinstall Ubuntu and start from scratch when the internet is working again?

---

