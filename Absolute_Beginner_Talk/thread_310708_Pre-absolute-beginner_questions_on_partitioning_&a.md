---
title: "Pre-absolute-beginner questions on partitioning &amp; WiFi"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2006-12-01
Greetings, Ubuntu Community !

I believe you have a great product here & I really want to come on board, but have some serious doubts which I hope somebody can clear up, one way or the other.
I have spent several days trawling through forums & sites, but still feel very uneasy & not ready to plunge.

My 3 potential show-stopper are:

1.   I have Windows XP pre-installed (no CD to restore it) and need to keep it as a double-boot option so think I am at risk of losing everything if I make even a slight error in all this disk partitioning which seems to be necessary with Ubuntu. 
Is this true? 
Is there a way round it?

2.   Do I need to clear a big continuous space on my single 120Go disk (with 55% total free space) before I start to install Ubuntu?
I ask because I have done 3 consecutive defrags with Windows Defrag tool and still have red & blue lines scattered all over, with no big clear space.
If I try to install Ubuntu here, am I going to wipe out half my world?

3.   Can I reasonably hope (as an absolute novice) to get Ubuntu to deal with my USB WiFi set-up?
It is a Tiscali/Inventel DW-B-200 modem with Inventel USB-LAN dongle.
I have seen many forum postings on this subject & they go WAY over my head without necessarily getting resolved.

I had hoped to get some encouragement by booting from the 6.10 desktop CD which I downloaded, burnt, verified & booted just fine (that WAS encouraging!).
The applications open up fine but don’t get much further.
From Open Office, I can produce documents OK, but not print to my Canon BJC-6000, though my own Open Office under XP prints fine.
I couldn’t find any way of selecting other than “default” printer.

Firefox just says “Server not found” which I guess is not surprising as the WiFi has not been set up?
I did not see anywhere to do that.
My own Firefox under Windows is OK.

I tried to use Evolution but only got as far as “Error while fetching mail”.
I think I followed instructions in setting up the e-mail account, but never entered any password, which is certainly required to get into my ISP.
I tried to edit the account, but still could not find anywhere to enter a password.
My own Thunderbird under XP works OK with the same account settings.

So the CD is at best inconclusive, but I don’t dare to make a real installation yet.

I really hope somebody can help me (as a total Linux dummy) to believe it can work!

Thanks in advance  :)

---

### Post by 56phil on 2006-12-01
Welcome to Ubuntu
[LIST=1]
[*]It is possible to mess up your windows installation ... however, it's **very** unlikely.
[*]You need free space, but you don't need to clear space manually. That said, doing a defrag and a disk check before you start the install process is a good idea. The installer will resize the windows partition.
[*]I have no experience with USB WiFi. So I'll let someone else answer that question.
[/LIST]
Good luck.

---

### Post by mushroom on 2006-12-01
You'll probably want to obtain a restore CD from your vendor before you go partitioning; it's unlikely that it would mess anything up, but I've heard stories. The USB Wi-Fi may not play well with Ubuntu, but you should fire up the Live CD to see if your hardware is detected. As far as Wi-Fi goes, if the Live CD doesn't detect it, then today may not be your day to install Linux. I know that's rather disheartening, and there **may** be some hacks around it, but it won't be a simple process (but not necessarily hard). Also, make sure to back up everything important on your Windows partition. If you run into any problems, be sure to report back.

---

### Post by Sef on 2006-12-01
I would recommned that you use the alternate cd to install.  It is a text based installer, but very easy to use, and there is less problems with installing than with the Live CD.  Yes partitioning can be tricky the first time.  To help you, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").

---

### Post by SyvanX on 2006-12-01
1. There's an automatic partitioner in the installer that tries to make sure you don't destroy anything.  I've never had a problem with it.

2. You will need lots of contiguous space depending on how you plan on using Ubuntu.  The WinXP defragger is designed to spread your data out, rather than clump it all together.  It was supposed to erase the need for defragging, but didn't do the job.  There are some shareware programs for defragging you can use on a trial basis, but you only need once :-)]

3. It looks like your USB WLAN device is based on the Atmel at76C503 chipset.  The [Hardware List]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") shows that chipset works fine in Ubuntu (scroll to the bottom, look for atmel, not inventel), but you should make sure that your device is Atmel.  Chipset is what matters, since the drivers are based on the chipset, not so much the manufacturer.  

If your wireless is open or WEP, you can test is pretty easily.  Go to the Network [Manager] Preferences in the Administration menu, and if your USB WLAN device is recognized it should be in the profile list.  You can activate it from here, and set up some basic network settings to test.  If you're using WPA it's not impossible, but a little more involved to try with the Live CD.

---

### Post by 2CV67 on 2006-12-02
Thanks guys for those rapid responses.

I now have recovery CDs so feel more relaxed!
I will be trying an alternative defrag tool soon (recommendation?).

WiFi:
My dongle is PQP-WU221L   S/N24W0097350.
I think Windows sees it as:  ATMEL USB FastVNET(505A)

I found & downloaded the manual from [http://www.pesi.com.tw/products/spec.php?id=22](http://www.pesi.com.tw/products/spec.php?id=22)
But could not find details of chipset.
The only chipset reference I could find was on [http://www.brest-wireless.net/wiki/materiel:inventel_usb](http://www.brest-wireless.net/wiki/materiel:inventel_usb)
Which suggests some models (not my S/N) would have ATMEL at76c50x.
Several sales outlets claim WU221L is compatible with Linux…  :) 

I have WEP.

Sorry, SyvanX, I did not manage to follow your instructions for testing: “Go to the Network [Manager] Preferences in the Administration menu, and if your USB WLAN device is recognized it should be in the profile list.”
I guess I still don’t speak Linux, but I am working at it!

Should I follow: System > Administration > Device Manager > Devices ?
There I can see a big list of items I don’t understand (notable exception - my hp scanjet 4470c).
Nothing that says WLAN or ATMEL or…
What should it say or where should it be?

I also tried (blindly): System > Administration > Networking > Network Settings > Connections > Wireless Connection (“This network interface is not configured”) > Properties > Settings for interface wlan0: where I enabled the connection & introduced my SSID & WEP key.

Finally I tried: System > Administration > Network Tools > Devices > Network Device > Wireless Interface (wlan0): but could not see or do anything helpful.

After all this, I am still at the same place with WiFi.

Could someone possibly walk me through the next step or two please?

Thanks, guys!

---

### Post by 2CV67 on 2006-12-03
Defrag now Ok thanks to Auslogics. :)

No ideas for my WiFi concerns (above) ? :( :(

---

### Post by SyvanX on 2006-12-06
> Finally I tried: System > Administration > Network Tools > Devices > Network Device > Wireless Interface (wlan0): but could not see or do anything helpful.

That's what I was thinking, sorry for the mistake, I'm not looking at Ubuntu right now.  I'm not sure what you did in Network Tools, so I'll start from the beginning.


If you select your wifi connection, there should be a couple buttons on the right called "*Activate*" and "*Properties*."

Select *Properties*, and enter the information for your wlan (won't work for WPA - but there is another way)

Then click activate and hopefully your device picks up an IP address.  It's much faster if you assign an ip address manually.

Give that a go, if it doesn't work (especially for WPA), PM me, and I'll be able to respond to you more quickly.

---

### Post by 2CV67 on 2006-12-10
Long pause there, partly to actually get Edgy installed (no longer running from CD) & partly for non-Ubuntu affairs (sorry for that admission!).

So all my original partition questions are closed now for me, but WiFi is still at the same place – no place…

Before going any further, let me say again that I have been using the WiFi with XP for a couple of years with no real problems, but without really understanding many of the terms or concepts.
I am a total Ubuntu noobie too, so all in all…

As a reminder, my WiFi is:
Tiscali/Inventel DW-B-200 ADSL modem 
WEP security
WLAN Dongle is PQP-WU221L S/N24W0097350.
        I think Windows sees it as: ATMEL USB FastVNET(505A)

I assume (buts that’s dangerous for me) that the first step in diagnosis is to check if Ubuntu can see the Dongle?

Should I be able to see something under: System > Administration > Device Manager & if so, what should it look like?
I see “RTL-8139….” & under that “Networking interface” but nothing that sounds like ATMEL or anything.

Following SyvanX’s lead above:
System > Administration > Networking > Network Settings > Wireless Connection > Properties…..
I Ticked “Enable the connection”
Network name (ESSID): I put DW-B-200-3D555
Network password:  I put the 26-digit WEP key (is that right?)
Password type:   As WEP key has numerals & letters A thru E I assume it’s Hexadecimal
Configuration:  Automatic Configuration (DHCP)
Click “OK”

System > Administration > Network Tools > Devices > Network device….
Select “Wireless Interface (wlan0) :  the “Configure” button stays grayed out & all the information is blank or 0.

Suggestions for next logical move please?

Thanks guys!

---

### Post by SyvanX on 2006-12-10
> **2CV67 said:**
> 

System > Administration > Networking > Network Settings > Wireless Connection > Properties…..
I Ticked “Enable the connection”
Network name (ESSID): I put DW-B-200-3D555  **<-- Correct (Should be same as how Windows sees it)**
Network password:  I put the 26-digit WEP key (is that right?)
Password type:   As WEP key has numerals & letters A thru E I assume it’s *Hexadecimal*  **<-- Correct**
Configuration:  Automatic Configuration (DHCP)
Click “OK” 

System > Administration > Network Tools > Devices > Network device….
Select “Wireless Interface (wlan0) :  the “Configure” button stays grayed out & all the information is blank or 0.

Suggestions for next logical move please?

Thanks guys!

What happens after you click "OK" in the Wireless Connection Properties?
If you didn't get any errors, open a terminal (Applications > Accessories > Terminal) and check the output of the following commands:

```
iwconfig
```
This should show which device name (e.g. ath0) is your wireless device.  If you post this, feel free to remove your WEP key.

```
ifconfig ath0 # or whatever the device from above is
```
In this one, check that inet addr: has an ip address, it should look something like this

```
$ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:90:4B:E7:82:52  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fee7:8252/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97782967 (93.2 MiB)  TX bytes:5655962 (5.3 MiB)
```

if you don't have anything suspicious to this point, make sure your wireless is the only connection you have to the internet, and enter the following code

```
ping -c 5 www.ubuntu.com
```

If that doesn't work, substitute [www.ubuntu.com](www.ubuntu.com) with the ip address of your router.  If you can get to your router, but not the internet, your wireless *is* working, but isn't configured completely.

---

### Post by 2CV67 on 2006-12-11
Thanks for your continuing patience SyvanX - much appreciated!  

Here is the result of ipconfig & ifconfig:

:::::::::::::::::::::::::

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3D555"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:F4:07:DB:3C  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

::::::::::::::::::::::::::::::::::::::::::::

Is it serious, doctor???

---

### Post by igknighted on 2006-12-11
Actually, this is great news!!!  wlan0 is the name of your wireless card in Ubuntu, and it appears that it has recognized it properly.  As far as managing wireless networks, Ubuntu's default program (system->admin->networking) isn't very good, but do not worry.  You should download a program called wifi-radar.  There are other options, but this is the one I am familiar with.  It is available in the Ubuntu repositories (via Synaptic Package Manager or apt-get) if you are online.  If you can plug the laptop into an ethernet connection that would be ideal, otherwise you might need to browse the repositories manually to find the program and use a disk or usb drive to transfer the file.  This should allow you to see available wireless networks and configure them with ease, which I think is where you are hung up.  If you need help finding the wifi-radar package post back and we can help.

---

### Post by hyper_ch on 2006-12-11
I'd also like to suggest while you are trying to get the wifi card running, just deactivate the WEP on your access point :)
So that there is one thing less to worry about... once you get the card properly working without WEP then you can activate it again...
Always start as simple as possible :)

---

### Post by 2CV67 on 2006-12-11
Your replies are encouraging... :) 

I don't have any Internet access at all from Ubuntu, but I have downloaded   "wifi-radar_1.9.7-0ubuntu2_all.deb"   from   "packages.ubuntu.com"   with XP & can transfer it to ubuntu via my shared space.

What do I do with it to get it installed, once I get it to my ubuntu desktop (or wherever) - in VERY simple instructions if possible!

By the way, the download site suggests I (may?) need some other items to go with wifi-radar, quote:

"Depends:
 _dhcp3-client_	DHCP Client 
 _python_	An interactive high-level object-oriented language (default version) 
 _python-gtk2_ (>= 2.0)	Python bindings for the GTK+ widget set 
 _wireless-tools_	Tools for manipulating Linux Wireless Extensions 

Recommends:
 _wpasupplicant_	Client support for WPA and WPA2 (IEEE 802.11i) "

Unquote.

Guidance please?

sjau suggests "just deactivate the WEP on your access point" but I re-read my 145-page Inventel Manual & still do not know how to "just ..."

I guess that's enough material for a next small step.

Thanks!

---

### Post by 2CV67 on 2006-12-11
I found from Synaptic Package Manager (first visit) that I already have the "Depends" & "Recommends" programs:
   dhcp3-client
   python
   python-gtk2
   wireless-tools
   wpasupplicant

I shifted my downloaded copy of wifi-radar_1.9.7-0ubuntu2_all.deb to ubuntu desktop.

So I am now staring dumbly at the wifi-radar ikon sitting next to the Synaptic Package Manager window (am I allowed to use that word here?) but I can't find out how to get it in there.

Just a little hint, please guys ](*,) 

Thanks!

---

### Post by igknighted on 2006-12-11
Put the .deb file on your desktop and the open a terminal and type the following:
```
cd Desktop
```
```
sudo dpkg -i wifi-radar_1.9.7-0ubuntu2_all.deb
```
This should complete the install, but if there are errors post them back here.  Check in system->administration for it in the menus, but if it isnt there just type 'sudo wifi-radar' in the terminal to run it.

---

### Post by tempest152 on 2006-12-11
The distro I tried before ubuntu, was SUSE, it didnt support my PCI dialup modem,  I ended up tinkering around quite a while with  [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)   and go it to work..  

It says ndiswrapper is designed for wireless cards, but works on other things too..  I remember copying the driver and needed files over from windows partition, and running ndiswrapper on them, and like magic, linux utilized the M$ driver.

---

### Post by 2CV67 on 2006-12-12
Well, I'm inching along here (feels more like "millimetering along though - I wonder how many potential Linux users fall by the wayside...?).

I finally got WiFi-Radar installed.
After many attempts, I did eventually realize I had downloaded
wifi-radar_1.9.7-0ubuntu2_all.deb and not
wifi-radar_1.9.7-Oubuntu2_all.deb
but even then I only won when I got Ubuntu to list Desktop contents & Copy/Pasted the name in...
Too late now for this one, but is there really no way of doing this with a mouse?

So - still no Firefox or Evolution connections, but when I run WiFi-Radar I do get the WiFi-Radar screen, which is blank in the center, but does say (under the screen:
"Connected to DW-B-200-3D555 ip(None)"
I suppose this is progress??

Having got WiFi-Radar to say I am connected with ip(None), what should be my next step?
Do I have to tell it somewhere the IP's I can see in Inventel XP  : 192.168.1.9 (192.168.1.1)
or...?

My head is buzzing with questions like:
How come I have never entered my "ADSL username & p/w"?
How come I have never entered my "normal username's p/w"? - I can tick to have Evolution remember it, but never get asked to input it...
I downloaded my ISP (Alice) parameters & don't find anything about SSL or Authentification, but those boxes are unticked in XP-Thunderbird, so I guess can stay empty for Evolution-ubuntu too?

After all this, I am MUCH more patient with my wife's PC ineptitudes.
Going through such un-obvious procedures must be good for the soul, but is very bad for the nerves!

Thanks for next small clue, somebody...

---

### Post by 2CV67 on 2006-12-12
Inching blindly ever onward, I have managed to ping my router, but cannot ping [www.ubuntu.com](www.ubuntu.com) or find internet via Firefox or Evolution.

These are terminal shots:

1. After previous post, where WiFi-Radar sees "connected ip(None)

:::::::::::::::::::::::::::::::::::::::

chris@salon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3D555"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chris@salon:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:F4:07:DB:3C  
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

chris@salon:~$ ping -c 5 [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [www.ubuntu.com](www.ubuntu.com)
chris@salon:~$ ping -c 5 192.168.1.9
connect: Network is unreachable
chris@salon:~$ ping -c 5 192.168.1.1
connect: Network is unreachable
chris@salon:~$ 

::::::::::::::::::::::::::::::::::::::::::::::::::

2.After changing "Automatic DHCP" to "Static" 
& inputting IP:  192.168.1.9 

::::::::::::::::::::::::::::::::::::::::::::::::::

chris@salon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3D555"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chris@salon:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:06:F4:07:DB:3C  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

chris@salon:~$ ping -c 5 [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [www.ubuntu.com](www.ubuntu.com)
chris@salon:~$ ping -c 5 192.168.1.9
PING 192.168.1.9 (192.168.1.9) 56(84) bytes of data.
64 bytes from 192.168.1.9: icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from 192.168.1.9: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 192.168.1.9: icmp_seq=3 ttl=64 time=0.037 ms
64 bytes from 192.168.1.9: icmp_seq=4 ttl=64 time=0.038 ms
64 bytes from 192.168.1.9: icmp_seq=5 ttl=64 time=0.037 ms

--- 192.168.1.9 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 0.037/0.040/0.051/0.005 ms
chris@salon:~$ 
::::::::::::::::::::::::::::::::::::

I can't say I really understand what I have done or if I should have done it differently, but I would again appreciate any suggestions for a next move!

Is that IP enough, as XP-Inventel shows me 
"192.168.1.9 (192.168.1.1)"

By the way, I am NOT just sitting here waiting for help, I AM frantically Googling practically full-time, but little of what I find is comprehensible to an "Absolute Beginner" as this forum is attractively called...

---

### Post by igknighted on 2006-12-12
wifi-radar should show you a list of available wireless networks that you can connect to.  Do you have the SSID broadcast enabled on your router?  If you enable it wifi-radar can assist you in connecting.

---

### Post by 2CV67 on 2006-12-12
Duh!

WiFi-Radar does not seem to find anything inside it's main screen.
Just the mention "Connected to DW-B-200-3D555 ip(192.186.1.9)" underneath.
Screenshot attached (I hope...).

Re-read the 145-page manual, but no mention of enabling or dissabling SSID broadcast.
The modem system parameters printout says:
"LAN broadcast address  192.168.1.255"
Maybe that means it's enabled?

---

### Post by 2CV67 on 2006-12-13
Sliding backwards now...

Previously I thought I had pinged my router, but I no longer believe that.
Not even sure I am getting to the USB-WLAN.

Not sure how to find the right IP to ping for the router...

Following some Microsoft Help sheet, I successfully pinged in XP (not in Ubuntu):
127.0.0.1 (loopback, whatever that means)
192.168.1.9 (local computer??)
192.168.1.1 (IP LAN ?)
212.129.9.68 (gateway?)
[www.ubuntu.com](www.ubuntu.com)

Disconnecting the ADSL lead to router then I could ping:
127.0.0.1 
192.168.1.9 
192.168.1.1 

Powering down the router:
127.0.0.1 
192.168.1.9 

Disconnecting WLAN from USB:
127.0.0.1 

:::::::::::::::::::::::::::::::::::

Back in Ubuntu, I can ping only:
127.0.0.1 
192.168.1.9 

:::::::::::::::::::::::::::::::::::

This looks to me as though Ubuntu is only getting to the WLAN but not connecting to the router.
I would appreciate a more-knowledgable opinion!

I tried "forcing" WiFi-Radar, by "Disconnect" and then "New" - filling in as much as I could.

This fills the screen nicely (see attached) but has no effect on connection or pings.

Can somebody throw me a lifebelt please?

---

### Post by igknighted on 2006-12-13
hmm, it looks like you are connected, but you don't have any connectivity?  This is very strange.  Something isn't quite right somewhere... when I use wifi-radar, all networks broadcasting within range appear in that middle screen (like you see in your second screenshot).  The only reasons I can think of that you can't see it are a) somewhere we missed a step and the card isn't configured properly; or b) there is a setting in the router that is conflicting.  I would post this issue in the network & wireless forum, more people who know these issues better will see it there.

---

