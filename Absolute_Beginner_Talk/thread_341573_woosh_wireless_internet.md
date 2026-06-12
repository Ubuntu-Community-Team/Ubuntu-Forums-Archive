---
title: "woosh wireless internet"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by rustyxb on 2007-01-18
hey i just dual booted my computer with ubuntu and windows xp and i have a usb modem for connecting to wireless broaband in new zealand. the problem i am having is that i cant get woosh to work on ubuntu, i have read that its possible to do. i have found this infomation at [http://www.wlug.org.nz/WooshWireless](http://www.wlug.org.nz/WooshWireless) 

How to configure a Woosh modem using the USB cable under Linux

For this to work you almost certainly need a recent 2.6 kernel with ipw either available as a module or compiled into the kernel. This works out of the box with Ubuntu Hoary, just plug it in and you will see in dmesg the ipw driver loaded. It'll allocate you a usb tty:

Jun 16 10:34:49 localhost kernel: ohci_hcd 0000:00:02.1: wakeup
Jun 16 10:34:49 localhost kernel: usb 2-3: new full speed USB device using ohci_hcd and address 5
Jun 16 10:34:50 localhost kernel: usb 2-3: configuration #1 chosen from 2 choices
Jun 16 10:34:50 localhost kernel: ipwtty 2-3:1.0: IPWireless converter converter detected
Jun 16 10:34:50 localhost kernel: usb 2-3: IPWireless converter converter now attached to ttyUSB0

Create a ppp peer for woosh, by creating the file /etc/ppp/peers/woosh:

noipdefault
/dev/ttyUSB0
115200
defaultroute
usepeerdns
lcp-echo-interval 60
lcp-echo-failure 3
connect "/usr/sbin/chat -v -f /etc/chatscripts/woosh"
noauth
persist
mtu 1400
user "username@woosh.co.nz"
maxfail 0
deflate 15

Create the chat script /etc/chatscripts/woosh:

TIMEOUT 30
ABORT "NO CARRIER"
ABORT "BUSY"
ECHO ON
SAY "Dialling w00sh...\n"
""              \rAT
"OK-+++\c-OK"   ATH0
OK ATZ
OK AT+CGDCONT=1,"PPP","woosh.co.nz","username@woosh.co.nz,foobar",0,0
OK ATD*99#
SAY "Waiting up to 30 seconds for connection ... "
CONNECT ""
SAY "Connected..."

Note the double handling of the username/password, both in the chat script and in chap. This is almost certainly unnescessary but seems to simulate the Windows ipw software configuring the modem. You can probably get away with putting garbage in the chat script.

Make an entry to chap-secrets as above with your username and pass.

[email]username@woosh.co.nz[/email]   *       pass       *

Then use pon to initiate the connection

pon woosh

can anyone help me to understand this as i am new to linux and dont know much about it.
i managed to create those two files which it tell me to create but thats about as far as i have got.
any help would be much appreciated thanks

cheers
croy

---

### Post by james_hogan on 2007-07-11
Hey there,

Yeah, I tried following these instructions too and got now joy.  So I emailed Whoosh's help desk and they say:
"Dear James,
 
The connection does work on Linux, as long as you've got the PPPoE dialler, Roaring Penguin. However, we do not offer support for Linux."

Here's the link to the Roaring Penguin dialer:
 [http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe](http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe)

So yeah, I've yet to download it, but according to its website:

"PPPoE (Point-to-Point Protocol over Ethernet) is a protocol used by many ADSL Internet Service Providers. Roaring Penguin has a free PPPoE client for Linux and Solaris systems to connect to PPPoE service providers.

Dubbed RP-PPPoE, this open-source product is ideal for Linux users with a DSL "modem" whose Internet service provider uses PPPoE. Before you download this software, check whether or not you really need it. If your ISP uses PPPoE, but has given you a router, you may not need a PPPoE client on your Linux box. DHCP may work fine."

and sounds like it might do the trick.


Regards,
James

---

### Post by hcolyn on 2007-10-23
hi james, sorry for reviving such an old thread but i am experiencing the exact same problem... have you had any luck yet?  please let my know, as i am starting to get really desperate for some internet away from vista :(

---

### Post by james_hogan on 2007-12-08
Hi hcolyn,

Alas no.  No joy at all.  I eventually got Roaring Penguin to go, but it didn't automatically solve the problem and i'm not yet that savvy to be able to fix it either.  So unfortunately, I don't have any answers here.

I gave Whoosh a call about switching from a USB modem to an ethernet version, thinking that like ADSL routers it would be intelligent and solve my problem, but these are not devices which Whoosh regularly doles out.  They'll give you one, but its going to cost $30 something dollars for the privilege.  So yeah.  I'm running a dual boot system too, and I'm resigned to the fact that Whoosh is only going to run on my XP operating system not on my Ubuntu.

*sigh....*


Regards,
James

---

### Post by james_hogan on 2007-12-08
Hey Hcolyn,

Right starting to get somewhere.  I followed the WLUG instructions and got my system to a point where its not only recognising that I've attached something to the USB, but its also trying to use it to dial out according to the scripts.  Point for reference, where these guys have written "foobar" they really meant for you to enter your password in that space.  Also, there's an inconsistant between the scripts around what the contents of "chap-secrets" is supposed to look like.  One example looking at a config file called dsl-provider has "chap-secret" looking like:
"something@whoosh.co.nz" * "password"

and example looking at whoosh has: 

[email]something@whoosh.co.nz[/email] * password

i.e. missing the quotes.  I used the example of chap-secret with quotes.

So I "pon whoosh" and checked out the var/log/message area (in the terminal window, type "tail -f /var/log/messages" and it will show you all the system messages happening on your system as they happen).  My system tried connecting and everything (which is the most progress I've ever had), until it fell down with:

"couldn't get channel number: input/output error"

which seems to be an error nobody has mentioned before.  

Back to the drawing board, but the most progress I've had so far.  This time I'll try chap-secret without quotes


Regards,
James

Addendum(Nah, the removing of quotes didn't help)

---

