---
title: "[SOLVED] HELP!!!  Rookie in trouble, need wireless help!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-05-27
Hi all!  This is my first post here, ever...  And yes, I realize that this has been asked before....but....

I am an absolute newbie to Ubuntu/Linux.  Not too bad on Windows (yeeechh!) but I've always wanted to switch to Linux.  Well, the collapse of my laptop was the trigger.  Dead HD, so I switched it out with a bigger one (good excuse...), now I have a HP Pavillion dv 5220us notebook without an operating system....
So, I installed Ubuntu 6.06 onto the new unformatted drive (I had the disk, came with the *_Moving to Ubuntu Linux [_*book).
BUT....  No internet connection, at all.  The OS doesn't "see" my Lynksis WRT54G wireless router at all.  Even on direct hookup to my cable modem (Motorola SB5120 Surfboard Cable Modem) nothing is visible.  Nada.  I be sending this out via my wifes Compaq using XP.  I REALLY do NOT want to use Microsnot anymore, I've never liked them, less now.
As for me going into the shell itself...heh (nervous laugh), so long as you guys use one syllable words and are VERY specific as to what to code, I'll give it a try.  As long as my wife still can access via Microsnot.
Thanks, in advance
John

---

### Post by ryanVickers on 2007-05-27
I have also a linksys router similar to that one, or it is the same, don't remember, but go into System > Administration > Network and make sure the ra0 (wireless) connection is enabled, but that's just the first step.  after that, go into properties

1. disable roaming mode
2. enter the router name (**not** the make/model/company)
3. enter your key and type
4. pick (probably) Automatic configuration (DHCP)

then click ok and wait, make sure a window pops up with a progress bar.  If so, continue, if not, click stuff til it happens :p

then in a terminal, enter these commands:

> sudo iwconfig ra0 channel 1 probably nor channel 1, maybe 6 or 9.  You can also do frequency

> sudo iwconfig ra0 ap 00:00:00:00:00:00 replace the 0's with your mac address

> sudo iwconfig ra0 key restricted blahblahblah enter the key you typed earlier here as well

wait about 10 minutes and you should get a connection

Hop everything goes ok, for more info in the iwconfig command, go System > Help and Support then type in iwconfig.

---

### Post by john wagner on 2007-05-27
Thanks, I'll give that a try...nothing to lose!  Heh...
john

---

### Post by ryanVickers on 2007-05-27
If it takes a while, don't give up - It took me like a week to figure everything out when I was brand new to this.  I would recommend you to do 2 things as soon as you get it working:

1. download all the plug ins and extra packages you need
2. watch the clip on my signature link so You'll know what your "missing" by not using windows :lolflag:

---

### Post by Austin_KW on 2007-05-27
Your router type is less important than your wireless adapter.
The instructions above assume that you have a ralink (rt2500 chipset?) adapter which creates a ra0 interface. 

If you go into a terminal and enter the command "lspci" you should see a line for your wireless adapter. From that someone can figure out the right howto for your driver.
You will also need your wireless details; encryption type (none/wep/wpa), encryption key and Essid (network name)

---

### Post by john wagner on 2007-05-28
Nope, didn't work......
no ra0, I got eth1 and eth0, so I enabled em, went into properties and picked DHCP.  Picked the name off the wifes wireless list...Lynksis (Automatic), keyless.  Progress bar etc.....  all good so far.  Did the sudo (substituting eth for ra.....)  It accepted it.  Then did the mac address (on wife's, it's called physical address????  Same format, 00-00-00-00-etc...).  Does not accept that command.
BUT, the light for wireless link has sped up the blinking by 4-5 times.  Its trying....

> **ryanVickers said:**
> I have also a linksys router similar to that one, or it is the same, don't remember, but go into System > Administration > Network and make sure the ra0 (wireless) connection is enabled, but that's just the first step.  after that, go into properties

1. disable roaming mode
2. enter the router name (**not** the make/model/company)
3. enter your key and type
4. pick (probably) Automatic configuration (DHCP)

then click ok and wait, make sure a window pops up with a progress bar.  If so, continue, if not, click stuff til it happens :p

then in a terminal, enter these commands:

 probably nor channel 1, maybe 6 or 9.  You can also do frequency

 replace the 0's with your mac address

 enter the key you typed earlier here as well

wait about 10 minutes and you should get a connection

Hop everything goes ok, for more info in the iwconfig command, go System > Help and Support then type in iwconfig.

---

### Post by john wagner on 2007-05-28
No sir, doesn't show up.  It lists my ethernet card as Intel Corp:  Unknown device 1092 (rev 01)
Network Controller:  Intel Corp:  Unknown device 4222 (rev 02)
The website (was an online purchase/gift to me), says it has a RJ-45 LAN ethernet, RJ-11 modem.  
Oh, and its disabled  encryption, and the ssid is just linksys.

> **Austin_KW said:**
> Your router type is less important than your wireless adapter.
The instructions above assume that you have a ralink (rt2500 chipset?) adapter which creates a ra0 interface. 

If you go into a terminal and enter the command "lspci" you should see a line for your wireless adapter. From that someone can figure out the right howto for your driver.
You will also need your wireless details; encryption type (none/wep/wpa), encryption key and Essid (network name)

---

### Post by ryanVickers on 2007-05-28
Interesting, I'd say it's not quite functional, but your on the right path.  I thought that the eth was just for wired connections, but ok, try that then.  I would just look around for little tricks and things, no big walkthroughs; like I said, your on the right track.  Play around with it a bit and see if it works.  Remember not to expect a connection immediately - if you happen to do something that will cause it to work, it may not begin to do so for up to 15 minutes for some reason (at least on mine).  Look up more info on a commit command as well, this may speed things up if your card supports it.

---

### Post by medley on 2007-05-28
> **john wagner said:**
> Nope, didn't work......
no ra0, I got eth1 and eth0, so I enabled em, went into properties and picked DHCP.  Picked the name off the wifes wireless list...Lynksis (Automatic), keyless.  Progress bar etc.....  all good so far.  Did the sudo (substituting eth for ra.....)  It accepted it.  Then did the mac address (on wife's, it's called physical address????  Same format, 00-00-00-00-etc...).  Does not accept that command.
BUT, the light for wireless link has sped up the blinking by 4-5 times.  Its trying....

Hi John

Getting wireless working in Ubuntu can be a bit trying, but you'll get there. A couple of things:

If you start a terminal session and type 'iwconfig' what do you get?
Also, assuming your wireless interface is working, you could try configuring your interface for static rather than dynamic IP to start and see what happens.

Phil

---

### Post by john wagner on 2007-05-28
Okay.....  I get:
eth1  unassociated ESSID: "linksys"
         Mode: Maneged  Frequency=2.412 GHz  Access Point:  Not - Associated
         Bit Rate: 0kb/s    Tx - power: 16  dBm
         Retry Limits:  15   RTS thr: off  Fragment thr: off
         Power Management: off
         Link Quality: 0 Signal level: 0  Noise level: 0
         Rx invalid nwid: 0   Rx invalid crypt: 0  Rx invalid frag: 0
         Tx excessive retries: 0  Invalid misc:  733  Missed beacon: 0
         
I hope that all means something to you all!  Oh yeah, I already tried the static route......nada 


> **medley said:**
> Hi John

Getting wireless working in Ubuntu can be a bit trying, but you'll get there. A couple of things:

If you start a terminal session and type 'iwconfig' what do you get?
Also, assuming your wireless interface is working, you could try configuring your interface for static rather than dynamic IP to start and see what happens.

Phil

---

### Post by medley on 2007-05-28
> **john wagner said:**
> Okay.....  I get:
eth1  unassociated ESSID: "linksys"
         Mode: Maneged  Frequency=2.412 GHz  Access Point:  Not - Associated
         Bit Rate: 0kb/s    Tx - power: 16  dBm
         Retry Limits:  15   RTS thr: off  Fragment thr: off
         Power Management: off
         Link Quality: 0 Signal level: 0  Noise level: 0
         Rx invalid nwid: 0   Rx invalid crypt: 0  Rx invalid frag: 0
         Tx excessive retries: 0  Invalid misc:  733  Missed beacon: 0
         
I hope that all means something to you all!  Oh yeah, I already tried the static route......nada

You're actually in pretty good shape, John. At least your card is working. It's likely you need to match your encryption and whatnot with your wrouter. What the above is saying is that it has detected a signal from that linksys router. Verify that your settings on your card (n/w configuration through network settings) and do a cold boot.

---

### Post by Austin_KW on 2007-05-28
You have not associated with the network.

SSIDs are case sensitive, are you sure you have it right?

---

### Post by Austin_KW on 2007-05-28
> **medley said:**
> Y... What the above is saying is that it has detected a signal from that linksys router. ....

Where does it say that?

---

### Post by john wagner on 2007-05-28
> **Austin_KW said:**
> Where does it say that?

Yes!  Where????  Not being rude or anything, just ignorant.  Where does it say that?  Seriously, I need to learn this stuff...

---

### Post by john wagner on 2007-05-28
> **medley said:**
> You're actually in pretty good shape, John. At least your card is working. It's likely you need to match your encryption and whatnot with your wrouter. What the above is saying is that it has detected a signal from that linksys router. Verify that your settings on your card (n/w configuration through network settings) and do a cold boot.

HOT DIGGITY DAWG!!!!  You be right!  I played arround with the settings, and this is being written/posted via my wireless router right now!  For others with this problem, this is what I did (pretty much Medley's advice)

OK,
Went into network and verified my wireless was/is enabled (no ra, I had eth)

no option for roaming mode, so no problem

entered name of router (lynksis)

unencypted/keyless

ended up having to go static IP (dynamic wasnt allowing me to connect, see below)

in terminal, 
sudo iwconfig eth1 channel 6

sudo iwconfig eth1 ap 00:00:00:00:00:00  DIDN'T accept, bash error...why I went to static
  IP setting

filled in all fields for static address

then a reboot

a quick check of iwconfig shows 
 a new address and a signal level 34dBm,Link Quality at 93/100,  and a bit rate of 54 mb/s

I AM VERY HAPPY RIGHT NOW!!!!  Thank you!  Everyone!  

john

---

