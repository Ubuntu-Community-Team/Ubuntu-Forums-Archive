---
title: "T60 Atheros vs. Intel?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by patrickk on 2007-05-06
hey there

So I'm still having trouble with the wireless on my lenovo t60...i have a dual boot setup, and i think i may have found the issue.  When I check device information on the windows partition, it says I have a intel pro/wireless 3945 A/B/G card...however in ubuntu, it says I have a AR5212 802.11abg NIC atheros card....i'm assuming this mix up is whats causing my wireless to work fine in windows, but not at all in ubuntu...or am i wrong?

can someone offer some advice on how to switch the ubuntu settings so that it detects the right card?  or is this possible?  or possibly install intel drivers over the atheros one?

am i being an idiot??  :confused: 

please help if you can...i love every part of ubuntu, but the lack of wireless is really getting on my nerves....thanks for your help.

---

### Post by gradedcheese on 2007-05-06
open a Terminal and run 'lspci', Intel wireless looks like this:

```

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

'hope you have that and not Atheros :)  However if it was Intel, it would be working now... I suspect yours is Atheros.

---

### Post by patrickk on 2007-05-06
i get this:

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

where should i go from here to get the wireless working?

and why the mismatch for atheros in ubuntu vs. intel in windows?

thanks again for any and all help

---

### Post by Mr.Beast on 2007-05-06
> **patrickk said:**
> i get this:

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

where should i go from here to get the wireless working?

and why the mismatch for atheros in ubuntu vs. intel in windows?

thanks again for any and all help

The intel driver is for your hardwired ethernet connection, the Atheros is your wireless.  Although in windows you may find it uses a driver badged as intel, if you look under the hood of the driver you wil probably find that it actually uses an Atheros chipset, and it's this that Ubuntu is detecting.

Via a package called network-manager I found that it worked fine, but the Atheros driver under ubuntu is what is classed as a restricted driver.  this means that it has propriatary company code that is not free / open source and is therefore harder to manipulate. but it's a similar chipset to my PCCARD netgear chipset, and I managed to get this connecting to my wireless networking (although getting WPA was a little tricky)  
One point to note is that I tried to connect to my dads wireless network yesterday and the laptop was just hanging. oh well.  Hope that this helps you some.

---

### Post by patrickk on 2007-05-07
so....do I need a different wifi manager apart from the standard gnome one?  how do you suggest I move forward so i'm not tethered to my desk??

it's getting really annoying to have to boot back into windows everytime i want to work on my laptop while sitting on my couch.  plus....the more i use ubuntu, the more i like it..everytime i go back into windows i find myself being less and less satisfied.

-patrick

---

### Post by gradedcheese on 2007-05-08
I believe that, for the AR5212 chipset, you need to download and built the latest madwifi driver.  You may wish to check google for more info.  This is not as hard as it sounds, there are extensive instructions here: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

With your LAN connection, make sure you're online and get the following packages:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

Now follow madwifi's instructions to build and load the driver.  As for the manager issue, NetworkManager is what comes on Feisty (7.04) and it did not come on older Ubuntu versions (6.10, etc).  You'll probably like NetworkManager better, so if you're on 6.10 you can install it.  If you're on 7.04, then you already have it.  The driver, though (madwifi) is what 'supports' the WiFi chipset, NetworkManager is just a user interface.

---

### Post by jrusso2 on 2007-05-08
I am going to recommend this forum for you as a T-60 owner.  There is a linux section and these guys know every trick to getting the most from Linux on a Thinkpad.

[http://forum.thinkpads.com/](http://forum.thinkpads.com/)

---

### Post by patrickk on 2007-05-08
great..thanks a ton guys I appreciate your help...ill give it a try

--patrick

---

### Post by jimrz on 2007-05-08
> **jrusso2 said:**
> I am going to recommend this forum for you as a T-60 owner.  There is a linux section and these guys know every trick to getting the most from Linux on a Thinkpad.

[http://forum.thinkpads.com/](http://forum.thinkpads.com/)
also might try thinkwiki.org

both my T42 and the netgear card in my older 600x have the same atheros 5212 chipset and work out of the box with feisty (also breezy/dapper/edgy).

is yours seeing anything or just missing a specific AP?

only issue i've ever had with mine is that in feisty (none of the earier versions) using n-m neither one was able to see networks that do not broadcast their essid., therefore i could not see my router although could connect to others in the area. changing my router settings fixed the issue.

---

### Post by patrickk on 2007-05-09
ok i worked on it for a while, got madwifi off my system then built it and re-installed it...when i try to connect through a console, all goes well until i try to use dhcpclient and i get:

patrick@patrick-laptop:~/madwifi-0.9.3$ wlanconfig ath0 list scan
SSID            BSSID              CHAN RATE  S:N   INT CAPS
WFUguest        00:0f:f7:14:1b:40    6   54M 34:0   100 ESsR WME
WFUguest        00:11:5c:5c:24:80   11   54M 27:0   100 ESR  WME
patrick@patrick-laptop:~/madwifi-0.9.3$ sudo iwconfig ath0 essid "WFUguest"
patrick@patrick-laptop:~/madwifi-0.9.3$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:ce:7a:a0:40
Sending on   LPF/ath0/00:16:ce:7a:a0:40
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


can anyone offer any help as to where to go/what to try next?  i know this network has working dhcp because i use it all the time in windows

where do i go from here?

---

### Post by patrickk on 2007-05-10
would ndiswrapper be a solution to this issue?

---

### Post by gradedcheese on 2007-05-10
After asking to associate:

```

sudo iwconfig ath0 essid WFUguest

```

(note: no quotes needed) ...wait a few seconds and take a look at the result:

```

iwconfig ath0

```

...what does it say?  "associated"?  If not, then that's a problem... let us know.  Make sure scanning works:

```

sudo iwlist ath0 scan

```

Finally, once it's associated, you should ask for the dhcp lease.  However, does your WiFi router require a WEP key or other authentication?  if so, you haven't provided it yet...

---

### Post by patrickk on 2007-05-10
aha!  you're clever...and right..it's not associated:

patrick@patrick-laptop:~$ sudo iwconfig ath0 essid "WFUguest"
patrick@patrick-laptop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"WFUguest"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/94  Signal level=-59 dBm  Noise level=-97 dBm
          Rx invalid nwid:165456  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


i know for a fact scanning is working, but just in case the output will help you:

patrick@patrick-laptop:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:0F:F7:14:1B:40
                    ESSID:"WFUguest"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/94  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101860003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:0F:F7:14:23:60
                    ESSID:"WFUguest"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s
                              12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101850003a4000027a4000042435e0062322f00

---

### Post by gradedcheese on 2007-05-10
Looks like you have APs on 6 and 11, and your card is on channel 11.  Hmm... try reloading the driver and doing this again using either channel 6 or 11:

```

sudo rmmod ath_pci
sudo modprobe ath_pci
sudo ifconfig ath0 up
sudo iwconfig ath0 essid WFUguest mode managed channel 6
sudo iwconfig ath0

```

associated?  If so:

```

sudo dhclient eth0

```

---

### Post by RippeRGuy on 2007-05-12
Hi there,

I am new to Ubuntu. 
I had the same issues with the wireless .... have gone through all the instructions as mentioned.
It seems to work only if I turn off the security (WEP or WPA).

Any suggestions?

---

### Post by dustigroove on 2007-05-14
[FONT=Arial][SIZE=2][COLOR=Black]I too have a T60 with the [COLOR=Blue][ThinkPad 11a/b/g Wireless LAN Mini PCI Express Adapter]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-52527&velxr-layout=printLenovo#version")[/COLOR], and from [COLOR=Blue][this ticket]("http://madwifi.org/ticket/936")[/COLOR] on the Madwifi.org site it appears that lspci is incorrectly reporting the chipset as an AR5212 (my D-Link DWL-G650 reports the exact same chipset and revision through lspci and works just fine with the madwifi ath_pci module in the repos). From another thread (sorry, have been unable to locate it) someone had success with getting our adapter working through ndiswrapper using the Windows drivers (link is above).

Cheers,
[/COLOR][/SIZE][/FONT]

---

### Post by stchman on 2007-05-14
> **patrickk said:**
> hey there

So I'm still having trouble with the wireless on my lenovo t60...i have a dual boot setup, and i think i may have found the issue.  When I check device information on the windows partition, it says I have a intel pro/wireless 3945 A/B/G card...however in ubuntu, it says I have a AR5212 802.11abg NIC atheros card....i'm assuming this mix up is whats causing my wireless to work fine in windows, but not at all in ubuntu...or am i wrong?

can someone offer some advice on how to switch the ubuntu settings so that it detects the right card?  or is this possible?  or possibly install intel drivers over the atheros one?

am i being an idiot??  :confused: 

please help if you can...i love every part of ubuntu, but the lack of wireless is really getting on my nerves....thanks for your help.

GO to my website.  I have a procedure to get Atheros cards working using madwifi.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

Hope it helps as it worked on my laptop.

---

### Post by gradedcheese on 2007-05-14
stchman -- your website tells him to do exactly what we have already told him to do (and he has done, presumably).  That is: get the build-essential and linux-headers packages, get the source, make and make install, and modprobe.

---

### Post by stchman on 2007-05-14
> **gradedcheese said:**
> stchman -- your website tells him to do exactly what we have already told him to do (and he has done, presumably).  That is: get the build-essential and linux-headers packages, get the source, make and make install, and modprobe.

Treu, but the thread skips all over the place and can be very confusing to someone that is new to Linux.  I just gave him clear step by step instructions to follow.  They worked for me so hopefully they will work for him.

---

### Post by dustigroove on 2007-05-16
[COLOR=Black]stchman,

Just to clarify: your instructions work for building and installing the madwifi module, but is this tested to work on a T60?

The issue here seems to be an incorrect reporting of the chipset:
--- Reports: AR5212
--- Actual: AR5BXB6

In my experience the AR5212 works just fine with the ath_pci module, however I do not believe that the [/COLOR][COLOR=Black]AR5BXB6 does.


Please correct me if I am wrong.

Cheers,

[/COLOR]

---

### Post by stchman on 2007-05-17
> **dustigroove said:**
> [COLOR=Black]stchman,

Just to clarify: your instructions work for building and installing the madwifi module, but is this tested to work on a T60?

The issue here seems to be an incorrect reporting of the chipset:
--- Reports: AR5212
--- Actual: AR5BXB6

In my experience the AR5212 works just fine with the ath_pci module, however I do not believe that the [/COLOR][COLOR=Black]AR5BXB6 does.


Please correct me if I am wrong.

Cheers,

[/COLOR]

According to [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros) that card should work with Feisty out of the box.

The card I have in my Toshiba laptop is a 5006EG and with Edgy I had to make the madwifi drivers.  I have upgraded my laptop to Feisty and the wireless is supported out of the box with a restricted driver loaded on install.  Feisty does have its quirks, but it is better with drivers than Edgy.

Are you using Edgy or Feisty?  Edgy you will need to make the madwifi drivers, Feisty should just work, if not install the madwifi drivers.

---

### Post by gradedcheese on 2007-05-17
> I have upgraded my laptop to Feisty and the wireless is supported out of the box with a restricted driver loaded on install.

that restricted driver is madwifi (whcih contains a closed-source HAL module that taints your kernel).  If you build their latest release, it can't be that much different (if it all) from what Fiesty 'ships' with.

---

### Post by dustigroove on 2007-05-17
[FONT=Arial][SIZE=2][COLOR=Black]Thanks, that is interesting as I know for sure the default Madwifi driver install on Fiesty (using the Restricted Drivers Manager) didn't work for me, nor did manual installation based upon a number of guides and multiple clean installs.

Will revisit when time permits.  Would be curious if any other T60 owners w/ this card have had any success without using ndiswrapper though.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by stchman on 2007-05-18
> **gradedcheese said:**
> that restricted driver is madwifi (whcih contains a closed-source HAL module that taints your kernel).  If you build their latest release, it can't be that much different (if it all) from what Fiesty 'ships' with.

Taints?!!!!!  I am a just works guy.  What possible impacts could it have.  Feisty installed the kernel by default.  So you are saying I should downgrade to a different kernel and make the madwifi drivers?

---

### Post by patrickk on 2007-05-18
how hard is ndiswrapper to get working?  that seems to be the solution.

---

### Post by stchman on 2007-05-18
> **patrickk said:**
> how hard is ndiswrapper to get working?  that seems to be the solution.

You don't need ndiswrapper for either an Intel or Atheros (non draft N) wireless card as Feisty supports them out of the box.

---

### Post by dustigroove on 2007-05-19
[FONT=Arial][SIZE=2][COLOR=Black]Well, I can most enthusiastically say that Fiesty does not support this atheros based PCI-express card "out of the box" with the default restricted madwifi drivers. I have tested this with another fresh install on this T60, and simultaneously on 2 other T60's (same build specs) with the official copy of the Desktop install CD as well as a burned copy of the downloaded Desktop install CD iso.

Going to give the guide stchman provided another go. If that doesn't work, will then try the ndiswrapper route. Will report back.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by joe.turion64x2 on 2007-05-19
My Atheros wireless card was supported out of the box in Ubuntu 7.04 (yes, it told me it was gonna use restricted drivers). According to posts I have read in other Linux forums, Atheros cards are better than Intel's. At least in the model you mention.

Haven't tried proved it myself because I don't have an Intel card to test.

Joe.

P.D. Try the madwifi-ng drivers, they are better.

---

### Post by dustigroove on 2007-05-19
[FONT=Arial][SIZE=2][COLOR=Black]Joe,  are you confirming this on a Lenovo Thinkpad T60 with the ThinkPad 11a/b/g Wireless LAN Mini PCI Express Adapter? I can also confirm that my D-Link DWL-G650 PCMCIA (Atheros based) card works out of the box on Fiesty with the madwifi drivers, but the internal card does not.

**EDIT:**  It still does not work after following stchman's guide, although it did make Network Manager Applet aware of the presence of the wireless adapter which was not the case before.

Will keep plugging away at this...

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by joe.turion64x2 on 2007-05-19
> **dustigroove said:**
> [FONT=Arial][SIZE=2][COLOR=Black]Joe,  are you confirming this on a Lenovo Thinkpad T60 with the ThinkPad 11a/b/g Wireless LAN Mini PCI Express Adapter? My D-Link DWL-G650 PCMCIA card works out of the box on Fiesty with the madwifi drivers, but the internal card does not.

Cheers,

[/COLOR][/SIZE][/FONT]
Check this [http://www.fedoraforum.org/forum/showthread.php?t=126266&highlight=T60](http://www.fedoraforum.org/forum/showthread.php?t=126266&highlight=T60) it might help you make your Atheros card work.

Mine is not a Lenovo laptop but has an Atheros wireless adapter and, following the procedure shown in the above link works for me (I use the madwifi-ng drivers).

Cheers.
Joe.

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]Okay, after much head-banging this past week and yesterday, I finally listened to [this post]("http://ubuntuforums.org/showthread.php?p=2635173&highlight=T60+wireless#post2635173") by fallingleaf as he went through the same headaches with the madwifi driver and this card.

Within 5 minutes I had a perfect connection using ndiswrapper, even works through the Network Manager applet.


Summary of what was done:

Removed madwifi drivers:
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo rmmod ath_pci
sudo rmmod ath_rate_sample
sudo rmmod ath_hal
```Blacklisted madwifi drivers:
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo nano /etc/modprobe.d/blacklist
```[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Add "blacklist ath_pci" and "[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]blacklist ath_hal" to the end of this file and save.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Install ndiswrapper:
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo apt-get -y install ndisgtk
```[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]Note: this will also install the actual ndiswrapper and utils packages.
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]
Then: [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo ndisgtk
```Click on the Install New driver button and select the .inf file from the Windows driver package for the card. Click on Close.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] Restart networking:
[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]```
sudo /etc/init.d/networking restart
```[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]
Now go up to Network Manager and you should see any available networks. Configure accordingly for your own network.

I'm mostly happy as can be... it would have been nice for everything to work out of the box without having to resort to bringing over the closed-source driver blobs, but I feel that I gave it way more of a go than was necessary doing the preferred method without much success. This was quick, easy, and provided me with the functionality I needed.

Hope my headaches help someone else...  ;)


Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by BenWhitey on 2007-05-26
Could this be done in kubuntu?  I tried and it looks like ndiswrapper uses Gnome.

EDIT: nvm I was being stupid.  It works great !

---

### Post by ThinkBuntu on 2007-06-02
this didn't do the trick for me...maybe the wireless driver was faulty. Back to madwifi and sub-par performance!

---

### Post by BenWhitey on 2007-06-02
Interesting.  Do you have this problem in madwifi:

[http://www.madwifi.org/ticket/1343](http://www.madwifi.org/ticket/1343)

---

### Post by insert_name_here on 2007-06-18
what is the name of the correct .inf file to use with ndiswrapper?  Also, how do you obtain this .inf from the .exe provided on the Lenovo site?

---

### Post by BenWhitey on 2007-06-18
I just got it from searching my windows install for it.  Its called: "net5211.inf"

---

### Post by insert_name_here on 2007-06-18
Awesome, thank you.

I even have that one ;-)

---

