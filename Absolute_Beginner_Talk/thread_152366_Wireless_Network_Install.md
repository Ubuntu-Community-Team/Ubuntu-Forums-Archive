---
title: "Wireless Network Install"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-03-29
Bought Belkin wireless PCMCIA card FSD7010 for Dell Latitude laptop because it is Linux-friendly and works "out of the box". 

Went to System, Administration, Networking, entered the info required for Wireless connection and it now says "The interface ra0 is active". So far, so good, I think, but no Internet connection, no lights on the card are showing lit.

What else do I have to do?

When I do an iwconfig I get:

lo no wireless extensions.

ra0   RT2500 Wireless ESSID:"Hoffnet"
       Mode: Managed Frequency=2.414 GHz  Bit Rate: 11 Mb/s
       RTS thr:off  Fragment thr:off
       Link Quality=0/100 Signal level=-120 dBm Noise level:-204dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0 Missed beacon:0

sit0  no wireless extensions.
  
Hope this means something to someone, as it means nothing to me!

Thanks for any help you can give.

On edit: smileys now disabled

---

### Post by moffa on 2006-03-29
Well it seems as if you are connected to the wireless network "Hoffnet"  Is that what you wanted?  Also is that network using a key?

---

### Post by The_Tankengine on 2006-03-29
I am having the same problem.  Everything seems to be set up fine but it wont connect to my network.
Here is my iwconfig:
```
lo     no wireless extensions.

eth0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
       Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
       Bit Rate:54 Mb/s   Tx-Power:25 dBm
       RTS thr:2347 B   Fragment thr:2346 B
       Encryption key:0000-0000-00   Security mode:restricted
       Power Management:off
       Link Quality:100/100  Signal level:-10 dBm   Noise level:-256 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx incalid frag:0
       Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0     no wireless extensions.
```

Any help is EXTREMELY appreciated!

---

### Post by xXx 0wn3d xXx on 2006-03-29
[QUOTE=The_Tankengine]I am having the same problem.  Everything seems to be set up fine but it wont connect to my network.
Here is my iwconfig:
```
lo     no wireless extensions.

eth0     no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
       Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
       Bit Rate:54 Mb/s   Tx-Power:25 dBm
       RTS thr:2347 B   Fragment thr:2346 B
       Encryption key:0000-0000-00   Security mode:restricted
       Power Management:off
       Link Quality:100/100  Signal level:-10 dBm   Noise level:-256 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx incalid frag:0
       Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0     no wireless extensions.
```

Any help is EXTREMELY appreciated![/QUOTE]


Go under System>Administration>Networking. Select your wireless network as the default gateway. Then highlight your wifi connection select properties and set it up.

---

### Post by The_Tankengine on 2006-03-29
I did that, still nothing.

---

### Post by moffa on 2006-03-29
What is the (E)SSID of the network you want to connect to?  Is there a key?

---

### Post by YuHoo on 2006-03-29
For the first question, I noticed that you have 0/100 for link quality. You are also running something other than IEEE802.11a/b/g. I'm not completely sure what this means but it could be that your wireless router could require some modification. A possible problem is encryption. 

The solution to it (though I'm not positive) could be to enter your router by accessing it with your browser (enter 192.168.0.1 as the url) and going to the wireless options. Under this there are options for WPA and WEP encryption, turn off whatever you have. This will turn off all passwords. Reset the router to apply the changes. Go back into the Network Administration, deactivate your wifi card and then make sure you have no password in the encryption, then reactivate it.

Could you also provide the details on your card, wifi router, and if you had success previously with this set up (I've fineggled with mine to get it up and running). If there are still problems please go into the BIOS by pressing the necessary button (usually F2 or delete, but it will tell you when the computer boots up what button to use to get into the BIOS). There ought to be wifi options, don't change anything if you don't feel comfortable, but record what options are there and post them.

P.S. To turn off the smilies there is a check box below in additional options that says disable smilies in text

---

### Post by moffa on 2006-03-29
The easiest way to setup my wireless has been to edit /etc/network/interfaces

Mine looks like:

auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid [wireless network name here]
wireless-key [WEP key here]

Please not that my wireless adapter is named wlan0, yours might not be

---

### Post by The_Tankengine on 2006-03-29
Mine looks the exact same way, with the exception of "auto wlan0" being the last line.  But I changed it to match yours anyway and I still have no connection.

The ESSID and WEP key of my network were already in there as well.
Maybe it is the router?  It is a D-Link DI-524.  Im pretty sure I set everything up correctly.  I pretty much just left it all standard.

When I open up the Connection Properties from the top bar, the signal strength is given as 100%, but the status is idle.  On the support tab it says Network Device - Type:  Ethernet  Address:  00:90:4b:54:08:db.  Maybe since it thinks it is an Ethernet device, that could do something quirky to it?

---

### Post by moffa on 2006-03-30
I have the same router.  Try restoring everything to defaults under Tools > System.  Then try connecting.  I found the router does funny things sometimes. Usually resetting to defaults then changing stuff again works.
Also try to "Activate" your wireless card. It in the Network settings I think.

-> Try typing in "ifconfig" to see if you have an ip address

Also try rebooting if you haven't already

---

### Post by alter_ego on 2006-03-30
I just got Ubuntu configured yesterday. I have it on dual boot with XP pro. If you have Windows, i would advise you to setup the wireless network in windows and then use the SSID with Ubuntu. 

Also check these two items
1) Is there any MAC address filtering on your router. (Shouldnt be the case since its a new one, but checking once again does help)
2) Check the type of encryption and the encryption key that you are using.

Mine is a D-link router by the way, never had any problems.

---

### Post by NetworkNed on 2006-03-30
> **SteveHoffmanUK]Bought Belkin wireless PCMCIA card FSD7010[/QUOTE]
Not a criticism but for future you might like to title a posting like this "Problems with Ralink wireless network" or mention the rt2500 drivers in the title, so that The_Tankengine will have no excuse for hijacking your thread with a query about an unrelated card (or a Ralink card running under NDISwrapper).

[QUOTE=SteveHoffmanUK]Went to System, Administration, Networking, entered the info required for Wireless connection and it now says "The interface ra0 is active". So far, so good, I think, but no Internet connection, no lights on the card are showing lit.
What else do I have to do?

When I do an iwconfig ra0 I get:

ra0   RT2500 Wireless ESSID:"Hoffnet"
       Mode: Managed Frequency=2.414 GHz  Bit Rate: 11 Mb/s
       RTS thr:off  Fragment thr:off
       Link Quality=0/100 Signal level=-120 dBm Noise level:-204dBm
       Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0 Missed beacon:0
[/QUOTE]
Booting my StinkPad with one of these cards in it I see that I get exactly the same scenario - no lights, iwconfig as above - when my wireless access-point is switched off. You might ask why I tested in this configuration and the answer is that my access-point is a honking great 1990s quad-xeon server with an Allnet card in it and I'm still tinkering with it prior to putting it into "production".

[QUOTE=SteveHoffmanUK]Hope this means something to someone, as it means nothing to me![/QUOTE]
It means that the rt2500 driver module is loaded and your card recognised on a hardware level (you could, for instance, run ethereal & sniff for packets from your AP).

But I suspect you're not connected at the TCP/IP level. What does `ifconfig ra0` say? Is there a button in the Ubuntu GUI you're using for "renew DCHP"?

My laptop has two runlevels - one for wireless & one for wired ethernet and now the access-point has booted I can try switching between them. I see that both lights on the card are illuminated as the card connects to the wireless network said:**
> For the first question, I noticed that you have 0/100 for link quality.
(but not, I think, with his suggestion "you are also running something other than IEEE802.11a/b/g.")
I also get 0/100 for link quality when my access-point is switched off, but see it varies between high 60s and 80s when connected to the AP (in the same room). So my first naive question is: are you sure you are near enough to your AP to get a signal? If you're connecting to the AP with another machine (or with this laptop dual-booted to Windows XP SP2) in the same room, what's the signal strength like? Have you tried connecting under Unbuntu with this laptop when it's in the same room as the AP? The problem may be with the AP, and one may often find that wireless connection issues are resolved by power-cycling the AP.

Finally, it's really worth configuring your wireless network like this & seeing what happens:
[INDENT]iwconfig ra0 essid Hoffnet mode managed nick Hoffnet rate auto enc XXXXXXXX power max txpower auto[/INDENT]
Some of these values are probably unnecessary, and you don't need the "key XXXXXXX" bit if your network isn't encrypted (you may wish to try disabling encryption at the AP as a preliminary stage). Could you possibly post the output of `iwconfig ra0` having run this command, please? The next step would be `ifconfig ra0 192.168.X.Y up` and seeing if you can ping the router.

Ned.

---

### Post by SteveHoffmanUK on 2006-03-30
In answer to Moffa, yes I want to access Hoffnet and yes it has an encryption key and I entered the key when I activated the wireless device.

---

### Post by SteveHoffmanUK on 2006-03-30
Ned

Thanks, first, for the tip on how to title a thread to avoid being hijacked. I'll try not to let that happen again!

I am afraid that much of your reply has sailed straight over my head. Remember, this is the Absolute Beginner Talk forum, so you'll lose me pretty quickly if the talk gets very geeky.

However, to answer something that I DID understand, I did a iwconfig ra0, and this is what I got:
  
ra0     RT2500 Wireless ESSID:"Hoffnet"
         Mode: Managed  Frequency=2.412GHz Bit Rate:11 Mb/s
         RTS thr:off   Fragment thr:off
         Link Quality=0/100 Signal level=- 120 dBm Noise level:-203dBm
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0

My network consists of a Windows XP Home machine connected to ADSL with a BT Voyager 105 modem. This machine has a DLink DWL-520+ wireless PCI adapter that provides a peer-to-peer WEP-encrypted network called "Hoffnet". The second machine on Hoffnet is also a Windows XP machine with a D-link adapter. The second machine has almost no peripherals -- it accesses the Internet via the first machine's ADSL connection and it also shares its printer; 

I have set up this network myself in XP, so I am not a complete PC duffer, although I found the XP network wizard wonderfully easy to use. I am now trying to link into Hoffnet my Dell laptop with the Belkin wireless card in the same way as I connected the second machine. I am working on the laptop sitting right next to Machine 1; Machine 2 is downstairs and generally has low (but sufficient) signal strength when it uses the network.

I am not keen to disable my Hoffnet encryption.

I hope the above will clarify the context in which I'm trying to make this work. I appreciate the trouble you are taking to help me to get it working.

On edit: sorry, you also asked what ifconfig ra0 produces. Here it is:

ra0 Link encap:Ethernet HWaddr 00:11:50:90:55:3C
inet6 addr: fe80::211:5-ff:fe90:553c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:63748 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2996156 (2.8 MiB)
Interrupt:11 Base address:0x4000

---

### Post by The_Tankengine on 2006-03-30
[QUOTE=alter_ego]I just got Ubuntu configured yesterday. I have it on dual boot with XP pro. If you have Windows, i would advise you to setup the wireless network in windows and then use the SSID with Ubuntu. 

Also check these two items
1) Is there any MAC address filtering on your router. (Shouldnt be the case since its a new one, but checking once again does help)
2) Check the type of encryption and the encryption key that you are using.

Mine is a D-link router by the way, never had any problems.[/QUOTE]

I just reset the router and made sure that there is no WEP or MAC filtering.  I have the router set up on a XP desktop, and I am trying to get wifi access on my laptop.  Like I said, everything seems to be set up fine, but the wlan0 connection is Idle, even though it says it has 100% signal strength.

Does your DI-524 router have 5 lights on with lights 2 & 4 blinking?

---

### Post by NetworkNed on 2006-03-31
[QUOTE=SteveHoffmanUK]
I am afraid that much of your reply has sailed straight over my head. Remember, this is the Absolute Beginner Talk forum, so you'll lose me pretty quickly if the talk gets very geeky.[/QUOTE]
I apologise for that. The best way to help me deal with it is to break my reply up into smaller quotes - like I'm doing with your posting here - and tell me, "I don't understand this" or "why do you want me to do that?".

I will always tend to work at the command line in the first instance of trying to get this working under Linux. Once we've proved the hardware works by using the command-line, then we can go on to testing the GUI. 

[QUOTE=SteveHoffmanUK]
I did a iwconfig ra0, and this is what I got:
[/QUOTE]
This is just the same as the `iwconfig` you posted before, adding the `ra0` bit on the end, the name of the interface, just means "only show me the status for this wireless card".

I see you've realised that I asked for `ifconfig` output - I'll address that below in a minute. BTW: `iwconfig` is for the wireless networking configuration of the card (same as double-clicking on the icon of the computer-with-radio-waves next to the clock in Windows XP SP2) and `ifconfig` is for the TCP/IP configuration of the card (same as going into Windows' Control Panel > Network Connections & right-clicking the wireless card then choosing Properties, TCP/IP, Properties).
  
[QUOTE=SteveHoffmanUK]
ra0     RT2500 Wireless ESSID:"Hoffnet"
         Mode: Managed  Frequency=2.412GHz Bit Rate:11 Mb/s
         RTS thr:off   Fragment thr:off
         Link Quality=0/100 Signal level=- 120 dBm Noise level:-203dBm
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0
[/QUOTE]
Y'see I don't think the GUI has connected you to this network - this looks like the sort of thing that you'd get if you mistyped the WEP key (not that I'm saying you have - there could be a bunch of other reasons).

Let me show you what this looks like on my machine:
```
iwconfig ra0
ra0       RT2500 Wireless  ESSID:"NedNet"  Nickname:"NedNet"
          Mode:Managed  Frequency=2.412 GHz  [COLOR="Red"]Access Point: 00:0F:A3:80:CA:8F[/COLOR]   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=82/100  Signal level=-65 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
See the "Access Point" point bit at the end of the second line? I think that's important - my machine is returning the MAC address (hardware address) of the access point it's connected to. Yours isn't.

[QUOTE=SteveHoffmanUK]My network consists of a Windows XP Home machine connected to ADSL with a BT Voyager 105 modem. This machine has a DLink DWL-520+ wireless PCI adapter that provides a peer-to-peer WEP-encrypted network called "Hoffnet".[/QUOTE]
Ah! This may be the r00t of the problem. Your `iwconfig` above shows a *_managed_* connection, but this is an *_ad-hoc_* network. Is it possible that this is where the GUI screwed up when you initially configured your network?

Consequently can I ask you to try, please:
[INDENT]iwconfig ra0 essid Hoffnet mode [COLOR="Red"]Ad-Hoc[/COLOR] nick Hoffnet rate auto enc XXXXXXXX power max txpower auto[/INDENT]
You'll need to change the XXXXX bit to your own key, and type the above line as root (or using `sudo`) at the command-line. Please repost the output of `iwconfig ra0` when you've done this.

[QUOTE=SteveHoffmanUK]
On edit: sorry, you also asked what ifconfig ra0 produces. Here it is:

ra0 Link encap:Ethernet HWaddr 00:11:50:90:55:3C
inet6 addr: fe80::211:5-ff:fe90:553c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:63748 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:2996156 (2.8 MiB)
Interrupt:11 Base address:0x4000[/QUOTE]
Ok... this indicates that your wireless card has no IPv4 network address. Compare it with a wired card connected to this machine or with my laptop:
```
ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:11:50:A8:78:56  
          [COLOR="red"]inet addr:192.168.1.109[/COLOR]  Bcast:192.168.255.255  Mask:255.255.0.0
          UP BROADCAST NOTRAILERS RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:4 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84332 (82.3 Kb)  TX bytes:22854 (22.3 Kb)
          Interrupt:11   
```
Yours has no "inet addr" section, but we need to sort connecting to the wireless network before we worry about this. The IP address will normally be issued by DHCP once we associate with the AP.

Ned.

---

### Post by SteveHoffmanUK on 2006-03-31
Ned

Thanks so much for your patient step-by-step approach -- definitely the best way forward on this. Also thanks for translating into Windoze so I understand what you're doing. I don't have any problem with using Terminal, although I'm more comfortable with GUI.

You wrote:
> Ah! This may be the r00t of the problem. Your `iwconfig` above shows a managed connection, but this is an ad-hoc network. Is it possible that this is where the GUI screwed up when you initially configured your network?

Consequently can I ask you to try, please:

    iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc XXXXXXXX power max txpower auto

I get:
Error: unrecognised wireless request "Hoffnet"

Before you ask, yes, Hoffnet was up and working when I did this, and I am sitting right next to the main machine while typing into my laptop.

I agree that it needs to be ad-hoc; I don't recall that the GUI asks about this because if it did I would certainly have ticked that box!

---

### Post by NetworkNed on 2006-03-31
[QUOTE=SteveHoffmanUK]...
You wrote:
[INDENT]Consequently can I ask you to try, please:

[INDENT]iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc XXXXXXXX power max txpower auto[/INDENT][/INDENT]

I get:
Error: unrecognised wireless request "Hoffnet"[/QUOTE]
Sorry to be obtuse, but are you sure you typed that in exactly (apart from the XXXXs), all on one line?

The easiest way to show output in a posting like this is copy & paste back from the terminal like this:
```
$ sudo iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc aaaaaaaaaa power max txpower auto
Password:
Error for wireless request "Set Power Management" (8B2C) :
    invalid argument "txpower".
$ sudo iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc aaaaaaaaaa 
$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"Hoffnet"  Nickname:"Hoffnet"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$  
```
The dollar sign is the prompt I use for a non-root user, so I've used `sudo` at the beginning of the command (and it's `sudo` that asks for my password).  If you're logged in as root then your prompt would probably end in a hash sign (#) and you wouldn't need the `sudo` bit.

As you can see, this doesn't work first time for me, either - I should have tested it before I posted it! - but without the power & txpower parameters it works fine. So if you could try that for yourself & then post back the `iwconfig ra0 && ifconfig ra0` that'd be great.

I think you might have missed out either the "essid" part or the "nick" part when you entered the command. See what happens below:
```
$ sudo iwconfig ra0 essid Hoffnet 
$ sudo iwconfig ra0 Hoffnet 
Error : unrecognised wireless request "Hoffnet"
$ sudo iwconfig ra0 NedNet
Error : unrecognised wireless request "NedNet"
$ sudo iwconfig ra0 essid Nednet
$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"Nednet"  Nickname:"Hoffnet"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ sudo iwconfig ra0 nick Nednet
$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"Nednet"  Nickname:"Nednet"
          Mode:Ad-Hoc  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
$
```

---

### Post by SteveHoffmanUK on 2006-03-31
OK, thanks again for the help. Taking a few of your points, first:

> Sorry to be obtuse, but are you sure you typed that in exactly (apart from the XXXXs), all on one line?

On edit: After first denying it, I rechecked and see that you're right, I did omit ESSID; many apologies for my crappy typing. Sigh. 

> The easiest way to show output in a posting like this is copy & paste back from the terminal like this:

Now it's my turn to be obtuse -- How can I cut from my Ubuntu laptop system (which does not have Internet access YET because that's what we're trying to achieve) and paste to my XP system which I must currently use for this forum? At the moment I am retyping what I see on my laptop and putting it into my messages in this forum. True, I may mistype, but what else can I do?

But to the nitty-gritty: You suggested that I type this:

```
$ sudo iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc aaaaaaaaaa 
$ iwconfig ra0 ra0 RT2500 Wireless ESSID:"Hoffnet" Nickname:"Hoffnet" Mode:Ad-Hoc Frequency=2.412 GHz Bit Rate=1 Mb/s RTS thr:off Fragment thr:off Link Quality=0/100 Signal level=-120 dBm Noise level:-256 dBm Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 Tx excessive retries:0 Invalid misc:0 Missed beacon:0 $ 
```

Sorry about the code formatting -- how do I get it to look like your line spacing?

Anyway, formatting aside, I now get a different result, typed out below:

```
steve@laptop;~$ iwconfig ra0
ra0     RG2500 Wireless ESSID:"Hoffnet" Nickname:"Hoffnet"
         Mode:Ad-Hoc  Frequency=2.412 Ghz  Bit Rate=11 Mb/s
         RTS thr:off     Fragment thr:off
         Link Quality=0/100 /sugbak kevek=-69 d/bn Biuse kevekL-208 d/bn
         Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0    Missed beacon:0
steve@laptop:~$
```

And here is what I get for ifconfig:

```
Ra0     Link encap:Ethernet   HWaddr 00:11:50:90:55:3C
          inet6 addr: fe80::211:50ff:fe90:553c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packet:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0,0 b)  TX bytes:21483935 (20.4 MiB)
          Interrupt:11 Base address:0x4000
steve@lap[top:~$
```

I feel we are making progress, are we not? No lights have lit on my Belkin card yet, but at least we got past the "unrecognized wireless request" barrier. 

What next? I am starting to get excited!

---

### Post by NetworkNed on 2006-03-31
> **SteveHoffmanUK]Now it's my turn to be obtuse -- How can I cut from my Ubuntu laptop system (which does not have Internet access YET because that's what we're trying to achieve) and paste to my XP system which I must currently use for this forum? At the moment I am retyping what I see on my laptop and putting it into my messages in this forum. True, I may mistype, but what else can I do?[/quote]
There's a bunch of ways:
[LIST]
[*] Copy & paste into a text file which you save on a floppy. Read this on your XP machine.
[*] Temporarily connect to your network using a cable. Sods law says email doesn't work on the laptop & you end up having to start an ftp server on your Windows box & ftp the text file of your output up to it.
[*] In the case of a dual-boot machine, save to a partition which is readable by both operating systems.[/LIST]
Often in *nix every option is somewhat inconvenient or contrived, but usually one method is slightly less inconvenient and contrived than all the others said:**
> 
But to the nitty-gritty: You suggested that I type this:
[INDENT]$ sudo iwconfig ra0 essid Hoffnet mode Ad-Hoc nick Hoffnet rate auto enc aaaaaaaaaa 
[/INDENT]
Sorry about the code formatting -- how do I get it to look like your line spacing?
Line-breaks, the enter key, are preserved within [C0DE] tags, I believe.
> Anyway, formatting aside, I now get a different result, typed out below:
```
steve@laptop;~$ iwconfig ra0
ra0     RG2500 Wireless ESSID:"Hoffnet" Nickname:"Hoffnet"
         Mode:Ad-Hoc  Frequency=2.412 Ghz  Bit Rate=11 Mb/s
         RTS thr:off     Fragment thr:off
         Link Quality=0/100 [COLOR="Red"]/sugbak kevek[/COLOR]=-69 d/b[COLOR="red"]n Biuse kevekL[/COLOR]-208 d/bn
         Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0    Missed beacon:0
steve@laptop:~$
```
There looks to be again some typo clutter in that, if you'll excuse me mentioning it. Either that or something's *_really_* wrong!!

The only difference that I can see is that it now says we're trying to make an ad-hoc connection on that interface - that is right - but the link quality & stuff still looks wrong. But this may be a vagary of ad-hoc mode - let's carry on for the moment.

> And here is what I get for ifconfig:
```
Ra0     Link encap:Ethernet   HWaddr 00:11:50:90:55:3C
          inet6 addr: fe80::211:50ff:fe90:553c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packet:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0,0 b)  TX bytes:21483935 (20.4 MiB)
          Interrupt:11 Base address:0x4000
steve@lap[top:~$
```

Still no IP address issued. Can you try (as root):
[INDENT]dhclient eth0[/INDENT]
& paste the output, please. What does `ifconfig eth0` say when `dhclient` has finished, please? If an IP address is issued tothe interface then we're all go!

Ned.

---

### Post by SteveHoffmanUK on 2006-03-31
One step forward, two steps back.

OK, OK. I agree that I've proved beyond a shadow of a doubt that copy/pasting is much better than my crappy typing. Your other options are either (1) too horrible to contemplate (temp connect to network via cable) or not applicable (dual boot).

So I try copy/paste to text editor in Ubuntu. This creates a file of 1.8Kb but Ubuntu tells me that there's not enough space on the (completely empty) floppy that I have attached to my laptop (not built into the Dell Latitude). Then I think maybe I should try to demount and remount my floppy. First half works a treat using the GUI. Then I try to remount (Places, computer, right-click Floppy1, Mount Volume, "Mount Error: Unable to mount the selected volume. I could not determine the filesystem type, and none was specified").

> It'll always take longer than you expected, anyway.
Too true. Sigh.

So now I have a laptop that is unable to communicate with the outside world. Am I discouraged? Nah: this is Linux, after all. Maybe you'd better give me some good ol' terminal magic that will get me to the point where I can actually copy/paste to a floppy. Then maybe we can address the original problem.

Again, let me say that I appreciate your patience and willingness to help.

---

### Post by SteveHoffmanUK on 2006-04-01
Hmm. I'm beginning to think the Gods are against me. In trying to sort out my floppy mounting problem, I read in another thread:
> In Breezy 5.10, there always has been a bug using the floppy drive. Dapper has the bug fixed.
The workaround suggested in that thread, however, requires you to get an update via the Web and, of course, I don't have Web access yet. ](*,) 
My fstab looks like this for the floppy:
```
/dev/fd0  /media/floppy0 auto rw,user,noauto
``` 
when I try to issue a mount command, that is:
```

sudo mount /media/floppy0
```
The message is always 
```
mount: you must specify the filesystem type
```
even though my fstab says "auto" for filesystem type. Maybe that's the Breezy bug?

In which case, unless someone can suggest how I can mount my floppy, I seem to have two choices:
1) Install Dapper
2) go buy a USB stick memory device (hoping that will mount, of course)

Other suggestions anyone?

On edit: On further thought, doubt if this is a Breezy bug; after all, I had successfully mounted and used this floppy drive with my current install. More likely something's happened to this drive. Off to find a memory stick.

---

