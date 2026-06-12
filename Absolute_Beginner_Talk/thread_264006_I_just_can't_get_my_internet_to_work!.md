---
title: "I just can't get my internet to work!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by theknave on 2006-09-24
Okay, I'm getting really close.

I've managed to get the computer to recognize that my adapter is connected (hurray!), and I've managed to enable the wireless connection without my computer freezing (hurray!), but I just can't get the darn thing to connect.

I've connected it on Windows many times - my network SSID is default, my WEP key is my phone number, and it's not got a static IP.

I've got all of the settings right, but firefox still refuses to load internet pages! Why? Can anyone help me?

---

### Post by Henry Rayker on 2006-09-24
What is the card? What chipset?

---

### Post by theknave on 2006-09-24
The card is a Linksys WUSB54G USB device.

I'm not sure what a chipset is, let alone what the chipset of mine is.

---

### Post by macthemaths on 2006-09-24
I have to do this:

In the FFox URL bar type

 about:config

In the filter bar that appears type

ipv6

Double click to toggle the value to 

TRUE

Then try a site - should work.

---

### Post by theknave on 2006-09-24
Thanks, mac, but that didn't work.

Anybody have more thoughts?

---

### Post by theknave on 2006-09-24
I'm sorry to bump this but I need to get this issue resolved tonight if possible as tomorrow I will not have this laptop for internet purposes while I resolve the problem with my desktop.

---

### Post by wieman01 on 2006-09-24
I have got a WUSB54G V4 as well.

Please post the contents of this file:
> sudo gedit /etc/network/interfaces
Then run these commands from a terminal & post the output:
> iwconfig
ifconfig
Also tell us a bit more about your network:

1. DHCP or Static IP (you mention static IP) and if Static IP please highlight the IP range & router address.
2. ESSID and whether broadcasting is enabled.
3. WEP, correct?
4. NDiswrapper, correct? Or RTxxx driver?

Then we'll see what we can do.

---

### Post by theknave on 2006-09-24
That file's contents are:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid default
wireless-key s:9058266900


auto eth0



That's that. Moving on to your questions:

1. DHCP. I mentioned static because I couldn't remember the initials for DHCP.

2. ESSID is default, broadcasting may or may not be enabled. I don't know what it is.

3. WEP, yes.

4. ndiswrapper. I had to use the graphical interface to set it up because I am such a noob.

Thanks in advance!

---

### Post by wieman01 on 2006-09-24
Can you still do:
> ifconfig
iwconfig
It's important to see what's going on there. :-)

---

### Post by wieman01 on 2006-09-24
Please also post this one:
> sudo gedit /etc/resolv.conf
Perhaps there is something wrong with your DNS settings.

Also... Are you running a firewall (e.g. Firestarter)? Is MAC authentication enabled by chance?

---

### Post by theknave on 2006-09-24
Somehow I missed that part. This is going to be a lot of typing, but here goes!

eth0      Link encap:Ethernet HWaddr 00:E0:18:29:38:69
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:o txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10472 (13.7 KiB)  TX bytes:14072 (13.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:73:AD:46
          inet6 addr: fe80::212:17ff:fe73:ad46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


And that's the end of that chapter. As far as iwconfig goes:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"hockey"
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s  Tx-Power:20 dBm  Sensitivity=-115 dBm
          RTS thr:2347 B  Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

The end. Now, one thing I've noticed is the ESSID was "hockey" which is one of my neighbours protected connections that I pick up as an option in windows sometimes.

Sorry it took so long, I had to type that all out by hand.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Please also post this one:

Perhaps there is something wrong with your DNS settings.

Also... Are you running a firewall (e.g. Firestarter)? Is MAC authentication enabled by chance?

That one gave me this:

search wlf.phub.net.cable.rogers.com
nameserver 192.168.0.1

I recognize the nameserver as what Windows said my DNS was yesterday.

I'm not running a firewall (I've only installed ubuntu and tried to get internet to work, nothing else), and I don't think MAC authentication is enabled. I've connected from two seperate windows computers, starting from scratch, and not had to worry about MAC anything.

---

### Post by wieman01 on 2006-09-24
Obviously you are hooked up to the wrong network. Strange thing.

Can you try this:
> sudo /etc/init.d/networking restart
Does your computer associate with your network ("default") now? Run this command twice.

Do you happen to have a USB memory device? Just highlight the terminal output with the mouse pointer to copy, then press the scroll-wheel or both left and right button of the touchpad to paste. Spares you the typing.

---

### Post by theknave on 2006-09-24
When I ran the networking restart command, it started listing off a whole lot of text, and it's not finished yet. The last thing it said was "No working leases in persistent database - sleeping.

I'm going to run it again just now.

---

### Post by wieman01 on 2006-09-24
Do you have a Firewall?

---

### Post by wieman01 on 2006-09-24
Also try this command... Is your own wireless network listed?
> iwlist wlan0 scan

---

### Post by theknave on 2006-09-24
I have no firewall to my knowledge. Upon running that command, it listed four different networks, the first of which was mine.

Would you like to see that insanely large block of text? I could try some negotiations with a floppy disk if it would help.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Would you like to see that insanely large block of text? I could try some negotiations with a floppy disk if it would help.
No, don't worry, I have enough information on hand. :-) Let me think for a minute.

---

### Post by wieman01 on 2006-09-24
Does the output for your own network say "Encryption key:on" or something similar? Or does it say "off"?

---

### Post by theknave on 2006-09-24
Okay. Thank you so much for the help thus far!

Also, if it helps, I just ran iwconfig again and now I'm connected to "peter", another wireless network that's not mine.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Does the output for your own network say "Encryption key:on" or something similar? Or does it say "off"?
```

Encryption key:on

```

---

### Post by wieman01 on 2006-09-24
Ok, weird... Let's do some housekeeping and bring your "/etc/network/interfaces" in order:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid default
wireless-key [COLOR="Red"]wireless_hex_key[/COLOR]
You don't need the remaining lines, so don't worry. Please reboot the computer and check afterwards if you're connected:
> iwconfig
Specify the WEP key in a hexadecimal format as given by the router (red block with no ""). The current one is in plain text... Let's try hex & see how it goes.

---

### Post by wieman01 on 2006-09-24
Should you still have no connection after the reboot, use the networking GUI and deactive & activate you wireless network adapter... This sometime helps in that it "shakes up" the system.

---

### Post by theknave on 2006-09-24
I'm not sure what it is you want me to do, so this is what I did.

I went in to network settings and changed the dropdown menu from Plain to Hexidecimal. Is that correct? Then restart?

---

### Post by wieman01 on 2006-09-24
Sorry... Ok, step by step:
> sudo gedit /etc/network/interfaces
This opens a file that controls the network adapters & your settings. Then paste this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid default
wireless-key [COLOR="Red"]wireless_hex_key[/COLOR]
...**wireless_hex_key** being your WEP key in hexadecimal format given by the router (NOT plain text this time). Simply replace **wireless_hex_key** with the hex key before you save the file. Once saved, you can reboot.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Sorry... Ok, step by step:

This opens a file that controls the network adapters & your settings. Then paste this:

...**wireless_hex_key** being your WEP key in hexadecimal format given by the router (NOT plain text this time). Simply replace **wireless_hex_key** with the hex key before you save the file. Once saved, you can reboot.

Okay, so do you want me to replace all of the text in the file with what you gave me in that little "code" section? As in, delete everything that's there?

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Okay, so do you want me to replace all of the text in the file with what you gave me in that little "code" section? As in, delete everything that's there?
Yes, replace the whole thing. All the other entries are Ubuntu default settings that don't apply to you anymore. It's absolutely safe to replace the contents with my stuff.

---

### Post by decoherence on 2006-09-24
If he had the same hardware working under Windows, it wouldn't be a MAC filtering thing...

I've found the best method for troubleshooting network connectivity is as follows

Open Applications>Accessories>Terminal and type

```
ping www.ubuntu.com
```

if this succeeds, then likely whatever network problem that prompted you to check isn't on your computer but one somewhere between your computer and the network resource you were trying to access. Of course, you can use whichever server you like, as long as it responds to ping. if it fails move on to

```
ping *nameserver-IP*
```

your name server IP is a dotted quad (204.181.101.4, for example) that would've been set up with DHCP. You can see your nameserver ip by typing 

```
cat /etc/resolv.conf
```

you probably have two or three of them. ping them all, one after the other. As long as one of them responds it means you're connected to the internet but your browser isn't loading pages for some other reason. Check proxy (firefox preferences Advanced>Network>Connections... at least in this Bon Echo beta i'm using) and firewall settings (type in the IP address of your router in a web browser.) 

Assuming that fails, the next thing to try pinging your router.
```
ping *router-IP*
```

you can get your router IP by typing

```
route
```

It should give you something like

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.10    0.0.0.0         UG    0      0        0 eth0


The specific numbers may vary, but if it just gives you the top two lines (kernel IP routing table and Destination Gateway etc) then something is misconfigured. In fact, you may wish to run the route command first, as it's usually a good test of your basic LAN connectivity.

Rather than step you through the process of troubleshooting a network interface (it's 4AM and i think i might finally be able to sleep after writing this) I'll just show you how to report the problem on here so somebody else can figure it out. Copy/paste this in to your Terminal (and remember, Ctrl-V doesn't work in the Terminal!)

```
iwconfig &> ~/netreport.txt ; ifconfig >> ~/netreport.txt ; route >> ~/netreport.txt ; cat /etc/network/interfaces >> ~/netreport.txt
```

this will create a text file called "netreport.txt" in your home directory. Copy and paste it's contents to the forum and people should have more than enough information to help out.

---

### Post by wieman01 on 2006-09-24
Another note... Check the router's settings once again with regard to:

1. DHCP
2. ESSID
3. WEP key (!)

The reason why I am saying this is that very often it turns out that a minor spelling mistake, etc. trips you up. I am trying to avoid that if you know what I mean. :-)

---

### Post by theknave on 2006-09-24
Okay, iwconfig says I'm connected to my proper network, but the internet still doesn't work.

---

### Post by wieman01 on 2006-09-24
Can you ping your router?
> ping 192.168.xxx.xxx
Use your router IP address.

Then try google:
> ping [www.google.com](www.google.com)
What happens if you do that?

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Another note... Check the router's settings once again with regard to:

1. DHCP
2. ESSID
3. WEP key (!)

The reason why I am saying this is that very often it turns out that a minor spelling mistake, etc. trips you up. I am trying to avoid that if you know what I mean. :-)

Yeah, I just checked them all right now on this computer, aside from the WEP key. The WEP key I was only able to get from the other computer when in Windows mode installing the router software.

---

### Post by wieman01 on 2006-09-24
Do you know how to access your router? Fire up a browser & type in the IP address of your gateway/router. E.g.
> [http://192.168.168.230/](http://192.168.168.230/)
Just to validate the key...

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Can you ping your router?

Use your router IP address.

Then try google:

What happens if you do that?

I must not know my router's IP because when I entered what I THOUGHT was my router's IP, it said "connect: Network is unreachable"

Google said "ping: unknown host www.google.com"

---

### Post by wieman01 on 2006-09-24
What does "/etc/resolv.conf" say now? This would be your router's IP.

---

### Post by chrisfay on 2006-09-24
type:
```
route
```

it will output something like this:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

The bottom line (default gateway) should be your routers IP...

---

### Post by decoherence on 2006-09-24
/etc/resolv.conf should be his nameserver. his router IP can be got with the "route" command. The router IP should appear under the "Gateway" column.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> What does "/etc/resolv.conf" say now? This would be your router's IP.


Okay. I've got that. I can't access it in a web browser because the username and password for that is not the same as for connecting to it, and i don't know it offhand.

pinging my router gives me:

network is unreachable

---

### Post by wieman01 on 2006-09-24
> **decoherence said:**
> /etc/resolv.conf should be his nameserver. his router IP can be got with the "route" command. The router IP should appear under the "Gateway" column.
Yes, right. In my case (static IP) is my router's IP address.

---

### Post by theknave on 2006-09-24
> **decoherence said:**
> /etc/resolv.conf should be his nameserver. his router IP can be got with the "route" command. The router IP should appear under the "Gateway" column.

When I type the "route" command, I don't get any numbers, it just prints the titles and that's it.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Okay. I've got that. I can't access it in a web browser because the username and password for that is not the same as for connecting to it, and i don't know it offhand.

pinging my router gives me:

network is unreachable
Ok, but the WEP key is the same one as you're using in Windows, is that correct? Just want to validate it, that's all.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> When I type the "route" command, I don't get any numbers, it just prints the titles and that's it.
That's because you're not connected...

---

### Post by theknave on 2006-09-24
Yeah, same WEP key as in Windows.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> That's because you're not connected...

Makes sense.

Is that my problem?

---

### Post by wieman01 on 2006-09-24
Ok, so the relevant section in "/etc/network/interfaces" looks something like this?
> wireless-essid default
wireless-key F2PE46EBD3FA94FAFB925489C4
F2PE46EBD3FA94FAFB925489C4 is the mentioned hex_key... Just an example to give you something to compare with.

---

### Post by chrisfay on 2006-09-24
> That's because you're not connected...

Even though he's not connected, shouldn't he still have a default route to his router? When I disable my eth0 connection/shutdown my lan connection to the net, I still get a route to 192.168.1.1 listed as my default gateway.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Makes sense.

Is that my problem?
Yes, that's the problem we are trying to solve right now. Your PC won't connect unless the WEP authentication has been successful.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Ok, so the relevant section in "/etc/network/interfaces" looks something like this?

F2PE46EBD3FA94FAFB925489C4 is the mentioned hex_key... Just an example to give you something to compare with.

:eek: Mine doesn't look like that at all!

Mine says:

35:60:09:40:F2

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> Even though he's not connected, shouldn't he still have a default route to his router? When I disable my eth0 connection/shutdown my lan connection to the net, I still get a route to 192.168.1.1 listed as my default gateway.
Probably because you're using Static IP?

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> :eek: Mine doesn't look like that at all!

Mine says:

35:60:09:40:F2
Ok, that's the problem. Eliminate the ":"... You need to get the key right.

---

### Post by chrisfay on 2006-09-24
> Probably because you're using Static IP?

lol....good call

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> lol....good call
Haha... Just a thought. ;-)

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Ok, that's the problem. Eliminate the ":"... You need to get the key right.

Okay, I've managed to figure out how to get to the website that I'm told is my router. The WEP key is still listed as my phone number, and I'm unable to locate the hex version of it. Where would it be?

---

### Post by theknave on 2006-09-24
> **theknave said:**
> Okay, I've managed to figure out how to get to the website that I'm told is my router. The WEP key is still listed as my phone number, and I'm unable to locate the hex version of it. Where would it be?

I also see a MAC address:

  	00-0f-3d-3e-7a-2c

---

### Post by chrisfay on 2006-09-24
Why don't you just temporarily disable WEP until you're sure your connection is good...no use in encrypting something you don't even have yet...

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> I also see a MAC address:

  	00-0f-3d-3e-7a-2c
This would be the machine you are using just now to post your stuff... :-)

---

### Post by theknave on 2006-09-24
> **chrisfay said:**
> Why don't you just temporarily disable WEP until you're sure your connection is good...no use in encrypting something you don't even have yet...

I'd like to, but my father uses this wireless internet connection for his business - it is used for his VOIP system as well as his company files - and he likes to keep that stuff safe.

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> Why don't you just temporarily disable WEP until you're sure your connection is good...no use in encrypting something you don't even have yet...
That's a good suggestion just to see what's going on. But the problem is that the other machine will be disconnected temporarily until you have disabled encryption there as well. But worth a try.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> I'd like to, but my father uses this wireless internet connection for his business - it is used for his VOIP system as well as his company files - and he likes to keep that stuff safe.
Ok.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> This would be the machine you are using just now to post your stuff... :-)

Ahh, okay.

But I'm pretty sure this screen is telling me that my hex key IS 9058266900, as I'd had before.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Ahh, okay.

But I'm pretty sure this screen is telling me that my hex key IS 9058266900, as I'd had before.
That's the "plain text" key, not HEX.

Ok, let's try again this one. Edit your interfaces file & restart the network:
> wireless-key s:9058266900
Restart:
> sudo /etc/init.d/networking restart
What does it say?

---

### Post by theknave on 2006-09-24
> **theknave said:**
> Ahh, okay.

But I'm pretty sure this screen is telling me that my hex key IS 9058266900, as I'd had before.

Okay, I'm 100% sure that this was what my computer was trying to say, so I went back into that interfaces file and changed the key to 9058266900 and rebooted. It's rebooting now and when it's back up I can only hope it will be fixed.](*,)

---

### Post by wieman01 on 2006-09-24
The little "s:" in front is important. But you could also try without it. Try both options, perhaps we are missing something here.

You don't need to reboot all the time. This should do:
> sudo /etc/init.d/networking restart

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> That's the "plain text" key, not HEX.

Ok, let's try again this one. Edit your interfaces file & restart the network:

Restart:

What does it say?

I don't know that I had the s: before. I've put that all in and the nteworking restart is going, but it's doing the same thing as last time; No working leases in persistent database - sleeping.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> I don't know that I had the s: before. I've put that all in and the nteworking restart is going, but it's doing the same thing as last time; No working leases in persistent database - sleeping.
Try to add the "s:"... This indicates that it's a plain text key rather than HEX.

---

### Post by theknave on 2006-09-24
> **theknave said:**
> I don't know that I had the s: before. I've put that all in and the nteworking restart is going, but it's doing the same thing as last time; No working leases in persistent database - sleeping.

And upon further inspection, it's back on that damn "hockey" network again.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Try to add the "s:"... This indicates that it's a plain text key rather than HEX.

Yeah, I added the s that time. No such luck.

---

### Post by wieman01 on 2006-09-24
Another question... You are sure it's WEP and not WPA? I am running out of ideas. What are we missing? Can you compare the settings with your Windows machine's?

---

### Post by chrisfay on 2006-09-24
You may try doing a hard reset on the router as well...

...I would also try giving your pc a static ip and bypass the whole DHCP issue.

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Another question... You are sure it's WEP and not WPA? I am running out of ideas. What are we missing? Can you compare the settings with your Windows machine's?

The router page says it's WEP for sure. I could compare the settings with windows machines if I knew what I was doing.

---

### Post by wieman01 on 2006-09-24
Yes, there is a point to Chrisfay's comment. I am beginning to suspect that your network uses Static IPs. Can you check this on your Windows machine? Somehow it's Network Settings->Properties, but not sure.

You can also check out the router to confirm.

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> You may try doing a hard reset on the router as well...

...I would also try giving your pc a static ip and bypass the whole DHCP issue.
Chris, are we missing something here? I have the feeling the solution is so obvious we don't see the wood for the trees.

---

### Post by chrisfay on 2006-09-24
It's so difficult sometimes in situations like this where we can't see everything ourselves. It would probably jump out at us but we're polking around in the dark...

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> It's so difficult sometimes in situations like this where we can't see everything ourselves. It would probably jump out at us but we're polking around in the dark...
Perhaps it's static IPs after all... Then we'd know the solution immediately. It's just ironic: My WPA2 network has been less of a hassle than this. I thought WEP was a piece of cake.

---

### Post by chrisfay on 2006-09-24
> It's just ironic: My WPA2 network has been less of a hassle than this. I thought WEP was a piece of cake.

Agreed...

I am also running out of ideas at this point if his router is configured for DHCP. For some reason, he's unable to receive IP leases. Not sure why....

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Yes, there is a point to Chrisfay's comment. I am beginning to suspect that your network uses Static IPs. Can you check this on your Windows machine? Somehow it's Network Settings->Properties, but not sure.

You can also check out the router to confirm.

Looks DHCP to me, but I could be wrong, so I screenshotted it!

[IMG]http://i9.photobucket.com/albums/a72/knave_13/DHCP.jpg[/IMG]

---

### Post by wieman01 on 2006-09-24
MAC filtering enabled? Perhaps your router does not allow your Ubuntu PC to connect. Can you check that through the router's web interface? There should be a section.

---

### Post by chrisfay on 2006-09-24
I would say your best bet is to find a time when you can disable the WEP, retry the connection, and if it connects you've got yourself a WEP issue. If not, you may have some hardware incompatabilities or driver issues..

---

### Post by wieman01 on 2006-09-24
Could also post a screenshot of the "wireless security settings" (WEP, etc.)?  Later on make sure you change the password... ;-)

---

### Post by wieman01 on 2006-09-24
> **chrisfay said:**
> I would say your best bet is to find a time when you can disable the WEP, retry the connection, and if it connects you've got yourself a WEP issue. If not, you may have some hardware incompatabilities or driver issues..
I tend to agree. Normally you start with simplest setup and gradually work towards your targeted one.

---

### Post by chrisfay on 2006-09-24
> I tend to agree. Normally you start with simplest setup and gradually work towards your targeted one.

Definately....helps to debugg without excess variables.

---

### Post by theknave on 2006-09-24
> **chrisfay said:**
> I would say your best bet is to find a time when you can disable the WEP, retry the connection, and if it connects you've got yourself a WEP issue. If not, you may have some hardware incompatabilities or driver issues..

Okay, I've done that just now. Trying to connect...aaaannnndddd

(if you were reading this in real time there'd be a pause here)

No such luck. Damned if I can find anything about MAC filtering, either.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Okay, I've done that just now. Trying to connect...aaaannnndddd

(if you were reading this in real time there'd be a pause here)

No such luck. Damned if I can find anything about MAC filtering, either.
Mate, this is no surprise. If you connect after disabling WEP, you need to remove the corresponding key line in the interfaces file:
> wireless-key xxxxxxxxx
Try now!

---

### Post by chrisfay on 2006-09-24
> Okay, I've done that just now

If by that you mean disabling WEP on your router, did you remove the wep option in your network config?

EDIT: Nice, you beat me to it..:p

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Mate, this is no surprise. If you connect after disabling WEP, you need to remove the corresponding key line in the interfaces file:

Try now!

Yeah, I'd done that. I'm catching on a little.

Well, I'm giving up for the night on account of it's 5:30 AM where I am and I haven't slept yet. Thank you so much for your help thus far, I'll bump this thread tomorrow in the hopes that someone else can help me (or you guys again, if you're around.)

---

### Post by wieman01 on 2006-09-24
And perhaps show us a screenshot of the "wireless security" section. Maybe we something that we have not been aware of up to now.

---

### Post by wieman01 on 2006-09-24
> **theknave said:**
> Yeah, I'd done that. I'm catching on a little.

Well, I'm giving up for the night on account of it's 5:30 AM where I am and I haven't slept yet. Thank you so much for your help thus far, I'll bump this thread tomorrow in the hopes that someone else can help me (or you guys again, if you're around.)
Ok, sorry to hear it. Open a new thread and post your "interfaces" file immediately so that people know what's going on. Have a good night.

---

### Post by chrisfay on 2006-09-24
> Well, I'm giving up for the night on account of it's 5:30 AM where I am and I haven't slept yet. Thank you so much for your help thus far, I'll bump this thread tomorrow in the hopes that someone else can help me (or you guys again, if you're around.)

Good luck!

---

### Post by theknave on 2006-09-24
> **wieman01 said:**
> Ok, sorry to hear it. Open a new thread and post your "interfaces" file immediately so that people know what's going on. Have a good night.

Thanks, bud, you too.

---

### Post by xpod on 2006-09-24
> Well, I'm giving up for the night on account of it's 5:30 AM where I am and I haven't slept yet. Thank you so much for your help thus far, I'll bump this thread tomorrow in the hopes that someone else can help me (or you guys again, if you're around.)
Reply With Quote

Thats what i like to see........determination!!
Your a better man than me as i usually have to "give up" about midnight..zzz
Good luck once you get some shut eye

---

### Post by wieman01 on 2006-09-24
> **xpod said:**
> Thats what i like to see........determination!!
Your a better man than me as i usually have to "give up" about midnight..zzz
Good luck once you get some shut eye
You again... Sneaky little... I see you post counter has gone up considerably. Do you have a life outside this forums ;-)

---

### Post by chrisfay on 2006-09-24
> Your a better man than me as i usually have to "give up" about midnight..zzz

Midnight shmidnight....When your internet's at stake, you do what it takes! ;)

---

### Post by xpod on 2006-09-24
> Do you have a life outside this forums 

Leave me alone you:D LOL...It`s a bit of a novelty at first BUT yes you better believe i got a life outside here.
Break rocks by day and break my back of an evening with my mini clan of 4 girls and 1 boy.........OH....AND theres the missus,Who makes my new computing problems pale into insignifigance the minute she "opens" that mouth
of hers...THIS IS MY ESCAPE....LOL

She thought i was on some sleazy chat room when she heard me talking about the difficulties with my B.U.M and my Gimp..:oops: ;)

EDIT: I havent actually began THAT many threads with issues but i do like to give the doubters and swearers a bit o motivation if and when their lambasting this thing cause THEY cant suss the  ISO out or dont like brown

EDIT2...And at least IM over the shame and aint got MINE hidden ...lol

---

### Post by theknave on 2006-09-24
Okay, here's the situation:

I'm making this post from inside Ubuntu (hurray!) and it's on the wireless internet (hurray!), but WEP is disabled (boo). It wouldn't let me enable it again last night, so I'll get to that another day (hurray!)


Thank you so much everyone who helped me in this thread. Your help was much appreciated and I'm happy to finally get this thing up and running. :D

---

### Post by wieman01 on 2006-09-25
> **theknave said:**
> Thank you so much everyone who helped me in this thread. Your help was much appreciated and I'm happy to finally get this thing up and running. :D
No problem. Our pleasure. Let us know when you're ready to take on WEP (or WPA).

---

