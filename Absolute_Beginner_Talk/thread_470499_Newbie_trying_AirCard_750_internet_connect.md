---
title: "Newbie trying AirCard 750 internet connect"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by linxuser14 on 2007-06-11
Go to 3rd posting

---

### Post by linxuser14 on 2007-06-11
Go to 3rd posting

---

### Post by linxuser14 on 2007-06-13
This is a cut and paste of my post on kubuntuforum.org

I've had no replies there, still waiting. Anybody's help

is welcome. Using Distro Kubuntu 6.06 LTS

## The following is best I can remember, how i gained temporary

## access to internet with my Sierra Wireless AirCard 750
##
## Via [http://www.sierrawireless.com/SupportDownload/downloads/AirCard7x0.zip](http://www.sierrawireless.com/SupportDownload/downloads/AirCard7x0.zip)
## 
## Downloaded and unzip AirCard7x0.zip

## ac750

## ac750chat

## SW_7xx_SER.dat
## 
## Used Kate to edit /etc/pcmcia/config 

## under Modems and other serial devices
## 
## Added

## card "Sierra Wireless AC710/AC750 GPRS Network Adapter R1"
## manfid 0x0192, 0x0710
## cis "cis/SW_7xx_SER.dat"
## bind "serial_cs"
## 
## Copied the file SW_7xx_SER.dat to /etc/pcmcia/cis/
## 
## Restarted computer

## Inserted AirCard. It didn't make two beeps indicating it was detected.
## 
## KSystemlog shows it was detected with only two lines

   kernel   [17180031.284000] pccard: PCMCIA card inserted into slot 0

   kernel   [17180031.292000] pcmcia: registering new device pcmcia0.0

## Copied files ac750 and ac750chat into /etc/ppp/peers
## 
## Editied file /etc/ppp/peers/ac750chat second line to

## OK AT+cgdcont=1,"IP","INTERNET2.VOICESTREAM.COM"
## 
## /usr/share/doc/kppp/README.Debian says to

## uncomment "noauth" in /etc/ppp/peers/kppp-options
## 
## KSystemlog now shows

   kernel   [17180283.576000] pccard: card ejected from slot 0

   kernel   [17180289.916000] pccard: PCMCIA card inserted into slot 0

   kernel   [17180289.916000] pcmcia: registering new device pcmcia0.0

   kernel   [17180289.944000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

## KPPP says it errored or couldn't find /lib/firmware/SW_7xx_SER.cis
## 
## So I copied SW_7xx_SER.dat to /lib/firmware/SW_7xx_SER.dat

## and copied SW_7xx_SER.dat to /lib/firmware/SW_7xx_SER.cis
## 
## My KPPP connect program is configured as follows

## -> Accounts
##              -> Connection name: T-Mobile
##              -> Phone number:    *99#
##              -> Authentication:  PAP
##                                    -> Store password is checked
## ----------------------------------------------------------------------

## -> Modems
##              -> Device
##                        -> Modem name:        AirCard 710/750
##                        -> Modem device:      /dev/ttyS0
##                        -> Flow control:      Hardware [CRTSCTS]
##                        -> Line termination:  CR
##                        -> Connection speed:  921600
## -> Use lock file is un-checked
## -> Modem timeout: is set at 60 sec
##

## -> Modems
##              -> Modem
##                     -> Wait for dial tone is un-checked
##                     -> only one addition to edit modem commands is
##
##             -> Initialization string 2: at+cgdcont= 1,"IP","INTERNET2.VOICESTREAM.COM"
##
## Both Login ID and Passord I've double single quote

## This is the KSystemlog output for the connect. as you see it terminated at 2 minutes

   kernel   [17182113.032000] pccard: card ejected from slot 0

   kernel   [17182119.556000] pccard: PCMCIA card inserted into slot 0

   kernel   [17182119.556000] pcmcia: registering new device pcmcia0.0

   kernel   [17182119.600000] 0.0: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A

   pppd[5539]   Connect: ppp0 <--> /dev/ttyS0

   pppd[5539]   pppd 2.4.4b1 started by ds2, uid 1000

   pppd[5539]   Using interface ppp0

   kernel   [17182185.284000] PPP BSD Compression module registered

   kernel   [17182185.356000] PPP Deflate Compression module registered

   pppd[5539]   appear to have received our own echo-reply!

   pppd[5539]   PAP authentication succeeded

   pppd[5539]   Remote message: TTP Com PPP - Password Verified OK

   pppd[5539]   Cannot determine ethernet address for proxy ARP

   pppd[5539]   local  IP address 10.172.93.90

   pppd[5539]   primary   DNS address 66.94.9.120

   pppd[5539]   remote IP address 169.254.85.170

   pppd[5539]   secondary DNS address 66.94.25.120

   pppd[5539]   appear to have received our own echo-reply!

   pppd[5539]   appear to have received our own echo-reply!

   pppd[5539]   appear to have received our own echo-reply!

   pppd[5539]   Connection terminated.

   pppd[5539]   Connect time 2.0 minutes.

   pppd[5539]   Exit.

   pppd[5539]   No response to 4 echo-requests

   pppd[5539]   Sent 57010 bytes, received 216199 bytes.

   pppd[5539]   Serial link appears to be disconnected.

## Here is the first of an endless stream of attempt by pppd (KPPP) to reconnect.

   pppd[5714]   Connect: ppp0 <--> /dev/ttyS0

   pppd[5714]   pppd 2.4.4b1 started by ds2, uid 1000

   pppd[5714]   Using interface ppp0

   pppd[5714]   Connection terminated.

   pppd[5714]   Exit.

   pppd[5714]   Hangup (SIGHUP)

   pppd[5714]   Modem hangup

This Added via Windows Connect. When I first posted this I did it thru Kubuntu via

my WIFI connection. (have to drive to a WIFI HotSpot)

The continueing attempts by KPPP to connect via aircard are unchanged.

I can only connect via Windows to check this forum. Anyone see what I'm doing
                      ( from home )

wrong. I know Kubuntu can establish a connection cause it did for 2 minutes.

I just don't know what to try next. This 2 minute connect was after having installed

Kubuntu 3 months ago and several times since. Any suggestions are welcome

Thanks

XXXXXXX

linxuser14

P.S. An additional attempt

 I got an idea to look for things to edit in files of /etc/ppp and /etc/pcmcia etc....

opened one file /etc/ppp/config i think, uncommented things like passive, something

to do with LTP or something like noLTP not ending pppd after an event. I don't recall

it all. unfortunately its on the Kubuntu partition of my hard drive so its not available to me

from this my Windows partition. But this connection via aircard is stable. Anyway after

editing these changes KPPP connected and remained connected for 10 minutes. When

it no longer communicated I had to manually disconnect, presumably cause of the passive

thing or something. KPPP when restarted couldn't find my aircard, so I reinserted it and

waited for the led to flash green, meaning it had a connection available. Then KPPP was

able to recognize the aircard, intialize and connect for an additional 5 minutes. More tries

proved unsuccessful. Thing is when I rebooted into windows the aircard's led light remained

steady red. After 2 attempts at reinstalling Window's software for it, it came back. I've

decided that maybe Kubuntu issued something to the aircard and I don't know what. 

Since the aircard works in windows I'm thinking maybe I should give up trying to get it

to work in Kubuntu. Don't want to mess it up and end up with no internet. Anyway this is

all I have on it.
 


p.s p.s. 

if you think this posting should be under another forum, please let me know, and 

thank you to everyone for working on this OS. I don't understand alot about it but I like

being able to work with open source system. I think its the coolest idea around.

Later, All

---

