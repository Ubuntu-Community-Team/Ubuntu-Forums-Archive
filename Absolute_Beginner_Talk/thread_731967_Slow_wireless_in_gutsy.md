---
title: "Slow wireless in gutsy"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by awiggin on 2008-03-22
I upgraded to gutsy last night and for the last 24 hours I have thought I couldn't connect to the internet via my wireless adapter (which worked fine in feisty).

However, I just booted up and in my upper left corner, I noticed that I had the temperature and weather for today.  That would mean I am connected, right?  In the manual config GUI for the network, I see that my computer recognizes my wireless internet (I also checked using lwconfig and it was correctly identified there), but when I open Firefox it says it cannot find the website.  When I click on "Connection Properties: wlan0", it says the signal strength is zero ( "0%").

Any ideas what is going on here?

Thanks all!

-awiggin

P.S.  The ubuntu community rocks.  I really appreciate all your help, folks.

---

### Post by kazamx on 2008-03-22
I'm not very good with wireless but here are some resources that may (or may not) help

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by awiggin on 2008-03-22
I went to the troubleshooting site you mentioned and it did clarify some things.

For one, I disabled ipv6 in Firefox.  I am able to connect to websites, but very slowly (slower than my old dialup).  

When I tried this line "Open the file /etc/modprobe.d/aliases" so I could disable ipv6 system wide, I got this response:  

bash: /etc/modprobe.d/aliases: Permission denied

I don't know if that matters or explains why my internet is still so slow, but I am glad to know I am connected.  I just need to know how to get back to normal speeds.

Thanks for your continued help.

-awiggin

---

### Post by jan quark on 2008-03-22
you can blacklist the ipv6 so it is not loaded doing the following

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add this line and the end of the file

```
blacklist ipv6
```

now save the file and reboot

---

### Post by awiggin on 2008-03-22
I did that.  I have disabled ipv6 in Firefox and added it to the blacklist in /etc/modprobe.d/blacklist .

But the connection is still slow to nonexistent.  Basically, I can't connect to anything.

The computer recognizes my wireless router via my wireless adapter (Linksys WUSB54G ver. 4, which is supposed to be fully functional - at least it was in Feisty).

Thanks for the attention you're giving this.  I appreciate it very much.

-awiggin

---

### Post by ghost_ryder35 on 2008-03-22
have you tried restarting your router?  Now that you have disabled your ip6 what is the output of iwconfig?

---

### Post by ghost_ryder35 on 2008-03-22
You could also try to download another browser and see if the problem persists.  another thought would be to try pinging your default gateway and check to make sure you are not dropping any packets.

---

### Post by awiggin on 2008-03-22
I have not tried restarting the router.  How would I do that?  Just disconnect it and then re-connect it?

The output I get from iwconfig is like this:

lo                    no wireless extensions
eth0               no wireless extensions
wmaster0       no wireless extenstions\

wlan0             IEEE 802.11g  ESSID: <My ESSID Name>
                      Mode: Managed   Frequency: 2.417 Ghz    Access Point:  00:19:58:57:5C:EF
                      Retry  min limit:7   RTS thr:off     Fragment thr=2346 B
                      Encryption key:off
                      Link Signal level=-52dBm
                      Rx invalis nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                      Tx excessive retries:0   Invalid misc:0   Missed beacon:0

I don't know what hardly any of that means, but that's what it says.

Can you help me?

---

### Post by jan quark on 2008-03-22
try 

```
sudo /etc/init.d/networking restart
```
to restart you network

---

### Post by ghost_ryder35 on 2008-03-22
> **awiggin said:**
> I have not tried restarting the router.  How would I do that?  Just disconnect it and then re-connect it?

The output I get from iwconfig is like this:

lo                    no wireless extensions
eth0               no wireless extensions
wmaster0       no wireless extenstions\

wlan0             IEEE 802.11g  ESSID: <My ESSID Name>
                      Mode: Managed   Frequency: 2.417 Ghz    Access Point:  00:19:58:57:5C:EF
                      Retry  min limit:7   RTS thr:off     Fragment thr=2346 B
                      Encryption key:off
                      Link Signal level=-52dBm
                      Rx invalis nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                      Tx excessive retries:0   Invalid misc:0   Missed beacon:0

I don't know what hardly any of that means, but that's what it says.

Can you help me?
Yea just unplug it and plug it back in and or turn it off and turn it back on if it has a power button.

---

### Post by awiggin on 2008-03-22
I tried restarting the network using /etc/init.d/networking restart and it went through that process.

Then, I tried a ping.  When I pinged my router, it came back 4x4 with 0% package loss in 2997 ms.

When I tried to ping an external ip address (216.239.5.99), I go 0 back with 100% package loss.  So, I am unable to go out to the internet.  But I knew that already.

Does that tell you anything you could use to help me?

Thanks,
awiggin

---

### Post by ghost_ryder35 on 2008-03-22
try to ping google.com
a lot of the times your router will have a firewall that will not respond to ping reqests.  2997ms is a huge amount of time....

---

### Post by awiggin on 2008-03-22
I tried to ping google.com and I got nothing back.

I unplugged and restarted my router.

So far, nothing.  I don't know what is blocking my internet connection.  I don't even have any idea where to look.

Have I set something up wrong?  (Or not set something up that needs to be set up?)

Thanks for the continued help.

-awiggin

---

### Post by unutbu on 2008-03-22
Let's see if the problem is between the router and the net, or between you and the router.

Point your browser at your router. You should get a web page back which allows you to poke around and configure your router. Look for a menu option which allows you to ping from the router itself.

---

### Post by ghost_ryder35 on 2008-03-22
i think you have a DNS issue,
try setting up a static DNS server with this IP
a) 4.2.2.1
b) 4.2.2.2
c) 4.2.2.3

---

### Post by awiggin on 2008-03-22
In Firefox, I tried to access my router (with my ip address, right? - like a 192.168.x.x kind of number) and firefox told me it cannot establish a connection.

So, I can't get to the router.

What does that mean?

________

As for the other suggestion, setting the DNS entry, how do I do that?

---

### Post by ghost_ryder35 on 2008-03-22
settings, advanced, networking, and then there is a DNS tab I belive and just add those servers.... but if you cant get to your router you got issues... what is the ip of your router?

---

### Post by ghost_ryder35 on 2008-03-22
you could also try a hard reset on the router by holding down the small button on the back of the router with a pen or equivilant.

---

### Post by awiggin on 2008-03-22
OK, so I know this is a total noob question, but where do I find the "settings" you refer to in order to get to the advanced and the DNS option?

Is there any danger in posting my ip address on this message board (sorry if it's a dumb question - I'm just a little paranoid someone could get on and do something to my router that would totally screw me.)

-awiggin

---

### Post by ghost_ryder35 on 2008-03-22
LOL, posting your local address is no problem, but you already posted your external address which is the one you didnt want to post :) 
216.239.5.99

---

### Post by ghost_ryder35 on 2008-03-22
oh yea and I believe it is the third option titled "System" then go to "Administration" then "Network"  I belive I boo booed the way there earlier

---

### Post by awiggin on 2008-03-22
That external ip address I listed earlier was just an ip address I got from an ubuntu tutorial to check my connection (via ping).  I have no idea what the ip address even is.  It's not mine.

So I got to the DNS tab in the Network settings.  Do I just add in those that you listed?

And does this even matter if I can't even access my router via my ubuntu box?

My ip address that I am trying to type in is 192.168.0.1 which works on the machine I am currently using to connect to the internet (the one I am on right now).

If I am not even able to connect to the ip address of my router, what would the next step be?

Thanks,
awiggin

---

### Post by ghost_ryder35 on 2008-03-22
I would make sure you are connected to the network, once you have verified that I would check to make sure your computer is pointing to your router for information (Gateway, DNS)  you can do that with the Network app you have up right now or ifconfig (i belive).  I would also make sure you have a correct IP address for your network.

---

### Post by unutbu on 2008-03-22
To check where your computer is "pointing", type

```
route
```

Look for a line that looks like

```
default         routerip        0.0.0.0         UG    100    0        0 wlan0
```

routerip should be the name of your gateway. Depending on your setup, the numeric ip address may be given there instead.

In fact, please post the output to route.

---

### Post by awiggin on 2008-03-22
The output (for the line you specified) is:

default       lance-desktop.l   0.0.0.0       UG    100   0         0 wlan 0


Obviously, that is not my ip address.  Also, "lance-desktop.l" is not the name of my router, either.  It's the name of my desktop.

I think the computer is sort of connected (if that makes any sense) because occasionally, my weather icon updates itself with a new temperature and weather.  But I cannot connect to any websites.

Please :confused: tell me the above information gives you some clue as to what is going on.

-awiggin

---

### Post by jan quark on 2008-03-22
ok some new input please

post the results of these terminal commands:

```
iwconfig
sudo iwlist scan
cat /etc/network/interfaces
sudo lshw -C network
```

---

### Post by awiggin on 2008-03-22
Here is the output for iwconfig:

lo no wireless extensions
eth0 no wireless extensions
wmaster0 no wireless extenstions\

wlan0 IEEE 802.11g ESSID: <My ESSID Name>
Mode: Managed Frequency: 2.417 Ghz Access Point: 00:19:58:57:5C:EF
Retry min limit:7 RTS thrff Fragment thr=2346 B
Encryption keyff
Link Signal level=-52dBm
Rx invalis nwid: 0 Rx invalid crypt:0 Rx invalid frag: 0
Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

I don't know what hardly any of that means, but that's what it says.

________

For sudo iwlist scan, I get the following:

lo                 Interfac doesn't support scanning.

eth0            Interfac doesn't support scanning.

wmaster0    Interface doesn't support scanning.

wlan0          No scan results

_________

For cat /etc/network/interfaces, I get the following:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

ahto eth1
#ifcace eth1 inet dhcp

auto eth2
#ifcace eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

iface rausb0 inet static
wireless-essid Huffman Family NEtwork
wireless-key <My Password>
address 192.168.0.171
netmask 255.255.255.0
gateway 192.168.0.1



auto rausb0

auto eth0



iface wla0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Huffman Family Network

auto wlan0

________

For sudo lshw - C network, I received the following:

*-network
       description:  Ethernet interface
       product: 82573E Gigabit Ethernet Controller (Copper)
       vendor:  Intel Corporation
       physical id:  0
       bus infor:  pci@0000:02:00.0
       logical name:  eth0
       version:  03
       serial:  00:16:76:44:cf:01
       capacityL  1GB/s
       clock:  33Mhz
       capabilities:  pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bd-fd autonegotiation
       configuration:  autonegotiation=on brodcast=yes driver=e1000 driverversion-7.3.20-k2-NAPI firmware=3.0-7 latency=0 link=no module=e1000 multicast=yes port=twisted pair

*-network
      description: Wireless interface
      physical id:  1
      logical name:  wlan0
      serial:  00:12:17:9c:0d:24
      capabilities:  ethernet physical wireless
      configuration:  broadcast=yes ip=192.168.0.1 multicast=yes wireless= IEEE 802.11g


_________

Now, I had to type all that since I can't cut and paste it from that other computer.  I hope that all tells you something. 

Thanks again for taking the time!  :)

---

### Post by ghost_ryder35 on 2008-03-22
iface wla0 inet **static**
**address 192.168.0.1**
netmask 255.255.255.0
**gateway 192.168.0.1**
wireless-essid Huffman Family Network
thats a problem, your address cant be the same as your gateway.

change static to DHCP :)

---

### Post by ghost_ryder35 on 2008-03-22
you have two wireless networks set up,
one is wlan0 and the other is rausb0, you should only have one configured....

---

### Post by awiggin on 2008-03-22
OK.  I changed it in the Network Settings GUI.

Then, when I typed cat /etc/network/interfaces, I got the following:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

ahto eth1
#ifcace eth1 inet dhcp

auto eth2
#ifcace eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

iface rausb0 inet static
wireless-essid Huffman Family NEtwork
wireless-key <My Password>
address 192.168.0.171
netmask 255.255.255.0
gateway 192.168.0.1



auto rausb0

auto eth0



iface wla0 inet DHCP
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Huffman Family Network

auto wlan0

_________

So, at the end it lists it as DHCP, but up above it still lists it as static.  Also, the addresses are still the same.

Is there some other way I should edit this, besides in the network manager GUI?

---

### Post by ghost_ryder35 on 2008-03-22
sudo /etc/init.d/networking restart

---

### Post by ghost_ryder35 on 2008-03-22
are you using a **usb **wireless adapter to connect wirelessly?
if you arent follow these steps

sudo gedit /etc/network/interfaces
then change "iface wla0 " to iface wlan0

and delete
"iface rausb0 inet static
wireless-essid Huffman Family NEtwork
wireless-key <My Password>
address 192.168.0.171
netmask 255.255.255.0
gateway 192.168.0.1
"

---

### Post by ghost_ryder35 on 2008-03-22
> **ghost_ryder35 said:**
> are you using a wireless adapter to connect wirelessly?
if you arent follow these steps

sudo gedit /etc/network/interfaces
then change "iface wla0 " to iface wlan0

and delete
"iface rausb0 inet static
wireless-essid Huffman Family NEtwork
wireless-key <My Password>
address 192.168.0.171
netmask 255.255.255.0
gateway 192.168.0.1
"

edit 
I just thought about what I typed and you might want to comment out the interface i told you to delte like so

#iface rausb0 inet static
#wireless-essid Huffman Family NEtwork
#wireless-key <My Password>
#address 192.168.0.171
#netmask 255.255.255.0
#gateway 192.168.0.1

---

### Post by awiggin on 2008-03-22
I did what you said.

the wla0 was a typo on my part, so I just left it as wlan0.

I eliminated the other step, then I restarted the network.

Still, nothing.  I am sorry to be such a pain.  But I don't want to give up on this.  I know this can work.

-awiggin

---

### Post by ghost_ryder35 on 2008-03-22
r u using a usb device to connect wirelessly?

---

### Post by awiggin on 2008-03-22
Yes.  It's a Linksys WUSB 54G ver. 4 (well supported) and it worked great right out of the box with Feisty.

---

### Post by unutbu on 2008-03-22
Please forgive the daunting length of this post. I think part of the problem with our previous attempts has been that we've been giving advice on a moving target. Your configuration went from static to DHCP, your router and computer might have had a connection, then the connection was lost probably after you restarted the router, the gateway and address have been the same (a mistake) for much of our conversation so far. (Pinging the gateway was really nothing but pinging yourself :)) It's not your fault, it's just no wonder things haven't worked... yet!

Getting networking to work is like getting planets to align. We need to get all the planets aligned at the same time or else its just no use.

We need to address the following issues:

1) We need a DHCP client running on your computer, usually dhclient (provided by dhcp3-client). The DHCP client allows your computer to set its ip address dynamically.
2) We need the router set to "DHCP Server Private LAN" (or something similar). Basically, get DHCP enabled on your router.
3) We need DHCP Start Address and End Address set to appropriate ranges. One of these addresses will be assigned to your computer. If you only have one wireless connection on your network, the start and end addresses can be the same.
4) We need the ip address of the gateway set in /etc/network/interfaces. Edit /etc/network/interfaces so the part about wlan0 looks like this:
```

iface wlan0 inet dhcp
#address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Huffman Family Network
auto wlan0
```

Note that the address line is commented-out because we are shooting for a DHCP connection. The router will assign your ip address for you.

Make sure that gateway really is 192.168.0.1. If we get this number wrong, we'll be pinging up the wrong tree. :) Please go to another computer connected to the router and put 192.168.0.1 into the browser. You should see the configuration/status page of the router. Confirm in your next post that you've seen the configuration/status page.

Once you get those 4 items configured, then run:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Huffman Family Network"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```
(This is straight out of kevdog's excellent guide, [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)).

This may or may not be enough to make things work. 
If it doesn't work, please post 

1) All output of the commands above (some might not have any output).
2) The output from the following commands:

```
ps auxw | grep dhcp                 # to test if dhclient is running
cat /etc/network/interfaces         # to see dhcp, no address, netmask, gateway, etc.
ifconfig wlan0                      # to see what inet addr you've been given
route                               # to see the entire routing table
iwconfig wlan0                      # to see that we've connect to the access point
sudo iwlist wlan0 scan              # just for fun

```

---

### Post by awiggin on 2008-03-23
I followed all the directions listed above.  I am still not connected.  Is there something specifically from the output I should tell you?  THere is a lot to type in and I don't want to type anything that is unnecessary.  I don't have any way of copying it easily and putting it in here since I don't have a connection to the internet on that computer (obviously).

Here are the outputs of the commands you gave me:

from ps auxw | grep dhcp :

dhcp     4154 0.0 0.0  2420  748  ?         S<s  09:48   0:00 djc;oemt3 -e IF_METRIC=100  -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
dhcp     5852 0.0  0.0  2420  520 ?         Ss    09:56    0:00  dhclient wlan0
lance    5858 0.0  0.0  2972  748 pts/0   R+  09:57    0:00  grep dhcp

_____________________
When I typed in cat /etc/network/interfaces, I got what I have always got (exactly as you told me to type it in.)

______________________
From ifconfig wlan0, I received the following:

wlan0               Link encap:Ethernet    HWaddr  00:12:17:9C:0D:24
                        Up BROADCAST MULTICAST  MTU:1500  Metric:1
                        RX packets:367 errors: 0  dropped: 0  overruns: 0  frame: 0
                        TX packets:156 errors: 0  dropped: 0  overruns: 0 carrier: 0
                        collisions: 0 txqueuelen: 1000
                        RX bytes: 62641 (61.1KB)  TX bytes:17241 (16.8 KB)

_______________________

When I typed in sudo iwlist wlan0 scan, I got the following:

wlan0              No scan results

________________

That's all I know for now.  I can tell you the outputs of the other stuff.  Tell me if you want the whole thing, or if there is something specifically to look for.

Thanks,
awiggin

---

### Post by ghost_ryder35 on 2008-03-23
i think we are all barking up the wrong tree..
"iface rausb0 inet static
wireless-essid Huffman Family NEtwork
wireless-key <My Password>
address 192.168.0.171
netmask 255.255.255.0
gateway 192.168.0.1
"

I belive the interface we should be configuring is the **rausb0** interface...

```
iwlist rausb0 scan
```

---

### Post by awiggin on 2008-03-23
OK.  I am happy to do that.  Should I just take off the # of the rausb0 section?  

Also, as a side question, when I click on propertyies of my wireless connection, do I need to type in the password to my router or would that only be to actually log in to the router?  And which password type should I use (wpa, wpa2, ascii, hexadecimal)?

I don't think I type in any password on my other windows computer to log into the internet.  It's just always on.

Sorry for the side diversion.

---

### Post by ghost_ryder35 on 2008-03-23
For cat /etc/network/interfaces, I get the following:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

ahto eth1
#ifcace eth1 inet dhcp

auto eth2
#ifcace eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp



**auto rausb0**  <----- Move it up here 
[B][COLOR="Red"]iface rausb0 inet dhcp[/COLOR]
#wireless-essid Huffman Family NEtwork
#wireless-key <My Password>
#address 192.168.0.171
#netmask 255.255.255.0
#gateway 192.168.0.1[/B]




auto eth0



[B]#iface wlan0 inet dhcp
#address 192.168.0.10
#netmask 255.255.255.0
#gateway 192.168.0.1
#wireless-essid Huffman Family Network[/B]

auto wlan0

---

### Post by ghost_ryder35 on 2008-03-23
> **awiggin said:**
> OK.  I am happy to do that.  Should I just take off the # of the rausb0 section?  

Also, as a side question, when I click on propertyies of my wireless connection, do I need to type in the password to my router or would that only be to actually log in to the router?  And which password type should I use (wpa, wpa2, ascii, hexadecimal)?

I don't think I type in any password on my other windows computer to log into the internet.  It's just always on.

Sorry for the side diversion.

yea I changed your interfaces to what I belive it should look like, change it to that and let us know.  Your windows connection is probally already have the password but we will worry about that later.  If we can get it to scan we are good :)

---

### Post by awiggin on 2008-03-23
I removed the comment marks (#) from the rausb0 section, and then typed in

sudo iwlist rausb0 scan

I received this output:

rausb0    Interface doesn't support scanning.

________

I will be away from my computer for a while (Easter with the fam).  BUt I will try whatever you post when I get back.

Thanks again.

-awiggin

---

### Post by ghost_ryder35 on 2008-03-23
CHECK THIS WEBSITE OUT BEFORE ANYTHING!!!!   [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)   #an exact how-to with your setup!

change your interface file to this:
```

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#ifcace eth1 inet dhcp

auto eth2
#ifcace eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

#Linksys WUSB 54G ver. 4 interface
auto rausb0 
iface rausb0 inet dhcp

#WLAN0 interface
auto wlan0
iface wlan0 inet dhcp

```

You should be able to copy and paste that in there.  Then you should

```

sudo /etc/init.d/networking restart

```

```

sudo iwlist wlan0 scan 

```

Then hopefully the Network Manager Applet in the upper right hand corner will be able to work and let you connect (if the scan worked)

---

### Post by awiggin on 2008-03-24
I edited my /etc/network/interfaces file to read as you said, then I ran "sudo /etc/init.d/networking restart"

I received a bunch of stuff, but the most significant seemed to be this:

rausb0: ERROR while getting interface flags:  No such device

and

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

____________

When I typed in sudo iwlist wlan0 scan , I received the following:

wlan0              No scan results

____________

I don't know how to get the "build essential" package from the other website since I can't connect to the internet on the computer.  I got gutsy from an upgrade, not a CD.  So I can't get the build essential from the CD.


____________

What do we try next?  (And I am kicking myself at this point for even upgrading.  I should have stuck with Feisty; it was working fine.)

____________

---

### Post by awiggin on 2008-03-24
Any ideas folks?  I am beating my head against a wall here.

I have little to no connection.  I have already disabled ipv6 in firefox and added it to my blacklist.  

I seem to have a small/weak connection since I have a temperature up in my weather icon that matches the temperature on my windows machine.  But I can't get anything else.

And when I look at my connection properties for wlan0, it reads that I have 0% signal strength and the status goes back and forth from sending to idle.

Do I need different drivers for my linksys wusb 54G ver. 4?  And if so, how do I get those if I can't connect to the internet and I don't have the boot CD for gutsy (I got gutsy by upgrading from feisty)?

Any help would be most appreciated.

Thanks,
awiggin

---

