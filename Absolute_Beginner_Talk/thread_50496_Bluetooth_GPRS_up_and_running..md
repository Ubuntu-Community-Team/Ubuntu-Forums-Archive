---
title: "Bluetooth GPRS up and running."
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-20
Just a quick report. After finally working through a whole lot of issues and complaints, I finally got my Bluetooth GPRS up and running. I finally recalled a post that the USB bluetooth dongle should not be in a hub, well, I don'd have a hub, but an extra PCI card add some four extra ports. Although its up and running and files etc work from PC to phone, I was unable to connect to GPRS.

On a whim, I decided, stuff it, and plugged the dongle in one of the system board USB port. And it started up without ANY mods to any file. I use wvdail, but was only connecting for two minutes, and off it goes. So I switch to my GPRS scripts, and I am still going strong!!! (The slapping sound you hear??? Me slapping myself with satisfaction.) \\:D/  \\:D/  \\:D/  \\:D/ 

Now my next hurdle. To set up things in such way so that I can just click on internet or mail, and it connects using my script. Dunno that part yet. Same goes for mail. Anyone that can help me, please congratulate me first and then tell me how! O:)

The command I currently use to run my GPRS scripts is:
pon MTN_GPRS
The last bit is what I decide on my network usage.

BTW. O yes, I am bragging big time. I write this mail while in UBUNTU, my first time ever online with Linux and my PC. :grin:

---

### Post by mabuti on 2005-09-14
HI!
Its good to hear that u got your GPRS up and running on linux. Can you explain bit by bit how did the setup, because I have been trying to do the same but have failed. I have a bluetooth adaptor and nokia 6260.
MTN_GPRS, sounds like youare somewhere in Joburg.

---

### Post by 3david on 2005-10-28
could you post your gprs scripts?

---

### Post by GrootBrak on 2005-11-03
[QUOTE=3david]could you post your gprs scripts?[/QUOTE]


Sorry, missed your post. I am at work running winduhs. As soon as I get some "home time" I will post to you. Meanwhile, check that you have the latest bluetooth-utils installed. 

This will only work if you have bluetooth sucessfully set up on your PC and paired the phone to PC on rfcomm0 channel 1. Else change as you may need.


In folder etc/ppp/peers. Use gedit to save and name it "T630" or whatever you like.

> /dev/rfcomm0 1	#Device bound to T630 Phone
115200		#Speed
defaultroute	#Use the network for the default root
usepeerdns	#use the DNS servers from the remote network
nodetach	#keep PPD in foreground
crtscts		#hardware flow control
lock		#lock the serial port
noauth		#don't expect modem to authenticate itself
local		#don'r use carrier detect or DTR
crtscts
debug


# Use the next two lines if you recieve the following messages:
#	No response to echo-requests
#	Serill link appears to be disconnected
#	Connection terminated
#
#lcp-echo-failure 4
#lcp-echo-interval 65535

#Prevent dial line checking as it does'nt work with SE T630
#causes it to disconnect
lcp-echo-interval 0
lcp-echo-failure 0


connect 	"/usr/sbin/chat -v -f /etc/chatscripts/MTN_GPRS-connect"
disconnect 	"/usr/sbin/chat -v -f /etc/chatscripts/MTN_GPRS-disconnect"

As you can see most is edited out. You could need those extra lines for other phones.

Here is what I have in folder etc/chatscripts. First is to connect. Second is to disconnect. Save it with the name you prefer, but remember to same name as the last two lines above. In my case it would be saved as "MTN_GPRS-connect" and "MTN_GPRS-disconnect" respectively.

> # File: /etc/chatscripts/MTN_GPRS
#
#Chat script for GPRS connection
#with MTN GPRS

TIMEOUT	10
ABORT	'BUSY'
ABORT	'NO ANSWER'
ABORT	'ERROR'
SAY	'Starting GPRS connection\n'

#Get the modem's attention and reset it.
""	'ATZ'

#Selection of the PDP contect. Choose which of the data connections to use. (CID)
#'' 'AT+CGDCONT=1,"IP","",,0,0'

#Qos requirements: requested and minimum acceptable
#'' 'AT+CGQREQ=1,0,0,0,0,0'
#'' 'AT+CGQMIN=1,0,0,0,0,0'

#EO=No echo, V1=English result codes
#OK	'ATEOV1' #Can cause problems

#Set APN
SAY	'Setting APN\n'
#OK	'AT+CGDCONT=1,"IP","myMTN"'

#Dial the number
ABORT	'NO CARRIER'
SAY	'Dialing CID 1 ... \n'
OK	'ATD*99***1#'
CONNECT	''



> #File: /etc/chatscripts/MTN_GPRS-disconnect
#
#Chatscript for disconnecting GPRS from MTN
""		"\K"
""		"+++ATHO"
SAY	"GPRS disconnected."

If you are an MTN subscriber, get the phone setting over the air by sending the following network code. *123# Then follow the instructions. The service is free.

Once set up, from command line, type "sudo pon T630" and away you go. I made a shortcut with the command, so I simply click it. However for the life of me a cannot get "poff" to work via shortcut!!!

---

### Post by debernardis on 2006-02-22
Hi, I was able to connect to GPRS (from Wind, an Italian mobile phone company) using info from your howto and from [http://ubuntuforums.org/showthread.php?t=111455](http://ubuntuforums.org/showthread.php?t=111455) , but...

since I am quite a noob I am unable to switch from wifi (WLAN0) to ppp0 to test the new connection.

I tried
```
$ sudo ifdown wlan0
$ sudo ifup ppp0
Ignoring unknown interface ppp0=ppp0
```

So ppp0 has something bad even if 
```
$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol
          inet addr:212.141.96.172  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:1 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:160 (160.0 b)  TX bytes:97 (97.0 b)
```

Could you help me? Thanks

_EDIT_
I did it. Started over, using KPPP for connection parameters. Added the proper GPRS initialization string **AT+CGDCONT=1,"IP","internet.wind.biz"** (cut .biz for home users) in modem config.
Also, since no authentication is needed for GPRS Wind connection, I edited /etc/ppp/peers/kppp-options , removing the comment sign from #noauth.
Deactivated wi-fi interface with **sudo ifdown wlan0**.
Then started KPPP, which connected flawlessly to GPRS.
After using GPRS I reactivated wlan with **sudo ifup wlan0**.

Wind users in need of help are welcome asking my config.

---

