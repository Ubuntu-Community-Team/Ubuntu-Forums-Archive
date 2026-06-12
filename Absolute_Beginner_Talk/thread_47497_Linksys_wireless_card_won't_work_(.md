---
title: "Linksys wireless card won't work :("
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by Zarkoth on 2005-07-08
Hi, I just went and installed my older comp with Ubuntu, and it's my first time running Linux.  Right now I'm on my XP, which is connected to the router.  How do I set up Ubuntu to use my card?  I've tried doing the DHCP settings and entering the IP manually, but it still won't get me a connection.  It's a 802.11b card from Linksys.  I'd really appreciate any help, thanks! :)



"Fear is uncertainty, and uncertainty is forever." 
              - Zarkoth the Shadow King

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=Zarkoth]Hi, I just went and installed my older comp with Ubuntu, and it's my first time running Linux.  Right now I'm on my XP, which is connected to the router.  How do I set up Ubuntu to use my card?  I've tried doing the DHCP settings and entering the IP manually, but it still won't get me a connection.  It's a 802.11b card from Linksys.  I'd really appreciate any help, thanks! :)
[/QUOTE]

Whats the exact card? I mean model number and version.

I have three WPC11 cards. The version 2 and 3 work really easy. The version 4 only works with ndiswrapper- a feat I never had success with.

So...more details please.

---

### Post by Zarkoth on 2005-07-10
It's a WMP11 v 2.0 I believe...

---

### Post by poofyhairguy on 2005-07-10
[QUOTE=Zarkoth]It's a WMP11 v 2.0 I believe...[/QUOTE]

Mine of that works out of the box...how close are you to the router?

---

### Post by Zarkoth on 2005-07-13
I'm not entirely sure....close to 30 or 40 feet though.

It used to work when I had Windows 98 on it, so I know it's in range.

---

### Post by Nequeo on 2005-07-13
Hi,

I've got a few questions that could shed some light on the matter...

Do you happen to know if your wireless card radio is on?

One way to test this is to open a terminal window and type 'iwconfig'. That will show you the name Linux has given your wireless card. On my home machine it's eth0, but at work it's wlan0... 

On the other hand, if you type 'iwconfig' and don't see any cards listed with wireless extensions, it means your card hasn't been installed properly. 

Once you know the name of your wireless card, type 'iwlist wlan0 scanning' (assuming your connection is named wlan0) and report back here what you see. 

I'll try and take it from there.

Cheers!

---

### Post by Zarkoth on 2005-07-18
I did the iwconfig, and it didn't list any (it called it eth0, btw) so this means that it's installed wrong?

How would I go about installing it correctly?

---

### Post by damonw5 on 2005-07-18
[QUOTE=Zarkoth]I did the iwconfig, and it didn't list any (it called it eth0, btw) so this means that it's installed wrong?

How would I go about installing it correctly?[/QUOTE]
 Try the next step of Nequeo's suggestion: type "iwlist eth0 scanning"

You can also fiddle around with Network settings under the System->Administration menu.

---

### Post by Nequeo on 2005-07-18
[QUOTE=Zarkoth]I did the iwconfig, and it didn't list any (it called it eth0, btw) so this means that it's installed wrong?

How would I go about installing it correctly?[/QUOTE]
 Hi Zarkoth - When you said 'it didn't list any', do you mean that every device came up like this...?

```

sit0      no wireless extensions.

```

If your wireless card was installed correctly, you would see something like this:

```

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-74 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4520141   Missed beacon:0

```

Please let me know,

Cheers!

---

### Post by poofyhairguy on 2005-07-19
Hmm...

See if ndiswrapper can get it to work:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by Declan on 2005-07-19
I'm asking the same kind of question here and there, but am having difficulty establishing the meaning of:

lo no wireless extension
eth0 no wireless extension
sit0 no wireless extension

What does this mean precisely? Does it just mean that I haven't got the card configured correctly?  Or that the system isn't even ready for a card, having nowhere to put it?
In other words: what is a "wireless extension"?

Declan

---

### Post by Zarkoth on 2005-07-20
Every device said "no wireless extensions".

And if I can manage to get ndiswrapper to work then I'll tell you if that works.

---

### Post by Zarkoth on 2005-07-20
Well I've been attempting to install ndiswrapper

Everything was going fairly smoothly up until it came time for me to "install the needed module".  I, naturally, followed the directions and said to the computer via a terminal window....

"sudo modprobe ndiswrapper"

And the computer said....

"FATAL: Error inserting ndiswrapper (lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation Not Permitted"

Something tells me that maybe I didn't do things quite right....

So what should I do?

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=Zarkoth]Well I've been attempting to install ndiswrapper

Everything was going fairly smoothly up until it came time for me to "install the needed module".  I, naturally, followed the directions and said to the computer via a terminal window....

"sudo modprobe ndiswrapper"

And the computer said....

"FATAL: Error inserting ndiswrapper (lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation Not Permitted"

Something tells me that maybe I didn't do things quite right....

So what should I do?[/QUOTE]

try doing 

> modprobe ndiswrapper

in the ROOT terminal.

---

### Post by Zarkoth on 2005-07-21
If by "root terminal", you mean to type "sudo su", which then puts me at "root@Zarkoth's-Lair.." and so on, then I tried that and it got the exact same response. :?
hmm

Well that's what's up so far.

But thanks for the suggestion!

---

### Post by poofyhairguy on 2005-07-21
This might be only way:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

---

### Post by Zarkoth on 2005-07-21
Well I tryed that link you put up there and we have made some progress....while following the instructions, I finally came up on the dreaded(for me, hehe) "modprobe ndiswrapper"...and it worked!  glee!

But the thing is, now every .inf file I've tried..(there are three, I tried them all) it says "invalid driver!" on them....

Soo....what should I do from here?

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=Zarkoth]Well I tryed that link you put up there and we have made some progress....while following the instructions, I finally came up on the dreaded(for me, hehe) "modprobe ndiswrapper"...and it worked!  glee!

But the thing is, now every .inf file I've tried..(there are three, I tried them all) it says "invalid driver!" on them....

Soo....what should I do from here?[/QUOTE]

Where did you get these .infs from?

---

### Post by Zarkoth on 2005-07-22
On the HowTo's for ndiswrapper they say to get htem from the driver downloads for windows...so I went and downloaded and unzipped the driver, and I tried all three .inf's that were there...the thing is, there are four different drivers, each for a different version of Windows...should I just try them all, or the one for the form of Windows I used to have?

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Zarkoth]On the HowTo's for ndiswrapper they say to get htem from the driver downloads for windows...so I went and downloaded and unzipped the driver, and I tried all three .inf's that were there...the thing is, there are four different drivers, each for a different version of Windows...should I just try them all, or the one for the form of Windows I used to have?[/QUOTE]

This site tells you which one you need (I hope):

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

---

### Post by Zarkoth on 2005-07-22
Alright, I went and tried the two .infs I got from the driver for my card via that link you just gave me, and one of them worked!  So now whenever I type "ndiswrapper -l" it'll display the driver, and at least it says, "driver present"....but I understand that it should also say "hardware present"  so how do I get it to recognize the hardware?

---

### Post by poofyhairguy on 2005-07-22
[QUOTE=Zarkoth]Alright, I went and tried the two .infs I got from the driver for my card via that link you just gave me, and one of them worked!  So now whenever I type "ndiswrapper -l" it'll display the driver, and at least it says, "driver present"....but I understand that it should also say "hardware present"  so how do I get it to recognize the hardware?[/QUOTE]

Hmm....does the network tool recognize it?

---

### Post by Snodgrass on 2005-07-23
I've just installed Ubuntu 5.04 on a Thinkpad R51. It's beautiful, and I'm so grateful to Ubuntu. The only problem is getting wireless to work. From System->Administration->Networking I am now told

Wireless Connection
the interface ath0 is active

In its Properties I've put the SSID name and WEP key I registered with Linksys when the Thinkpad was running Windows XP. I went over to 192.168.1.1, the Linksys registration page, and poked around there but didn't see anything I thought could help.

It's configured for DHCP, and there are two DNS servers from my ISP (I think).  

The IBM wireless icon glows promisingly, and so does the Linksys WRT54G monitor.

But as soon as I remove the cable connection from Linksys to the Thinkpad, the connection is broken.

Here are the results from iwconfig:
-------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"BACH"
          Mode:Managed  Frequency:2.472 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
---------------------

And "iwlist ath0 scanning" gives:
------------------------
ath0      Scan completed :
          Cell 01 - Address: 00:06:25:F7:5A:66
                    ESSID:"Bach"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
--------------------


A hundred dollar donation to Ubuntu for information leading to a solution.

TIA,

Snod

---

### Post by Zarkoth on 2005-07-23
Sorry, I didn't manage to find time to find out, mostly because I'm off to bike across Iowa, w00t!....lol   So I won't be back until August 1st, so I suppose I'll be seeing ya then??  Who knows, but that's when I'll be back.  See ya!

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=Snodgrass]I've just installed Ubuntu 5.04 on a Thinkpad R51. It's beautiful, and I'm so grateful to Ubuntu. The only problem is getting wireless to work. From System->Administration->Networking I am now told

Wireless Connection
the interface ath0 is active

In its Properties I've put the SSID name and WEP key I registered with Linksys when the Thinkpad was running Windows XP. I went over to 192.168.1.1, the Linksys registration page, and poked around there but didn't see anything I thought could help.

It's configured for DHCP, and there are two DNS servers from my ISP (I think).  

The IBM wireless icon glows promisingly, and so does the Linksys WRT54G monitor.

But as soon as I remove the cable connection from Linksys to the Thinkpad, the connection is broken.

Here are the results from iwconfig:
-------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:"BACH"
          Mode:Managed  Frequency:2.472 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
---------------------

And "iwlist ath0 scanning" gives:
------------------------
ath0      Scan completed :
          Cell 01 - Address: 00:06:25:F7:5A:66
                    ESSID:"Bach"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
--------------------


A hundred dollar donation to Ubuntu for information leading to a solution.

TIA,

Snod[/QUOTE]

Can you start a new thread?

---

