---
title: "Gutsy and cell as modem (again)"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2007-12-13
The following is output from [this]("http://ubuntuforums.org/showthread.php?t=166617") thread when wvdial is run and I am just using to try and illustrate a problem I am having trying to use a Samsung F300i as a modem in Gutsy…

```
t0p@lapt0p:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Wed Apr 26 23:11:44 2006
--> pid of pppd: 11096
--> Using interface ppp0
[B]--> local IP address 10.33.228.142
--> remote IP address 10.6.6.6
--> primary DNS address 193.35.133.10
--> secondary DNS address 193.35.134.10[/B]
```

Not all of the above is a 100% accurate reflection of what I see when I connect… but I don't have the exact info at the moment (at work and not at home)...

When I use wvdial everything seems to be going smoothly up to the bold part… I never see IP address etc. being displayed.  It goes up to “Using interface ppp0” and then after about 15 seconds it gives an error (16) which says remote modem hung up and it tries to redial…

I have configured wvdial with many… many tutorials from this forum and I always get the same result… can this be an ISP problem… or is their some network configurations wrong on my side?  (I connect successfully in windows XP)

---

### Post by thenailedone on 2007-12-14
*bump and plead*

I know how annoying it is when threads get bumped and someone makes double posts... and I have just done both :(

Linux without net access is a crippled penguin... I am using Gutsy with a Samsung F300i and the carrier is Virgin Mobile (South Africa)...

Thanks again...

---

### Post by niteshifter on 2007-12-14
I feel your pain :)

Look at your original post - I posted how I connect via wvdial using a RAZR V3, including the wvdial conf script. 

If you've already read that then post your /etc/wvdial.conf file here and I'll see what I can figure out.

---

### Post by thenailedone on 2007-12-14
> **niteshifter said:**
> I feel your pain :)

Look at your original post - I posted how I connect via wvdial using a RAZR V3, including the wvdial conf script. 

If you've already read that then post your /etc/wvdial.conf file here and I'll see what I can figure out.

Thanks niteshifter... I had read your post and it gave me the same info as most of the other tutorials (which makes sense I guess) but I did see something I hadn't seen/tried before...

From your reply:

> Init2 - will vary with cell service provider. How did I work this out? Pretty much all cell providers will provide a Windows app that uses Windows DUN. Which is what I did: Use Cingular's Communication Manager set up and make a connection with it in Windows XP, then look in Win's XP Control Panel under Phones and Modems. Examine the properties of the newly created USB or Bluetooth modem. Hopefully this will work for you as well. If you don't have Win XP, borrow a friend's system or find someone who also uses a cell phone as modem on your service. Last resort: Call your service's customer support - and be prepared to spend some time doing this, making muliple calls. Not to bash call center help, but what you want is NOT in their main experience. You might be better off spending some time with Google.

I suspect that this might be a source of my problems... wvdial finds the modem ok, initializes it OK and then when it is negotiating with the service provider the other modem hangs up... as if it isn't hearing what it wants to hear... I will try your suggestion when connecting via XP thx :)

*edit 16/12/07:*

I cannot get my PC to connect to the internet.  This is as much info as I can give now&#8230; more than I have ever given&#8230; help&#8230; please&#8230;

I am using Ubuntu 7.10 Gutsy Gibbon 64-bit.  I am using a Samsung F300i via a USB cable with Virgin Mobile&#8230; I am doing all this from South Africa.

My wvdial.conf file:

```
[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Init3 = at+cgdcont=1,"ip","vdata" 
Modem Type = USB Modem 
Modem = /dev/ttyACM0 
Baud = 460800 
ISDN = 0 
Phone = *99# 
Username = A  
Password = B  
Stupid Mode = 1 
```

I got most of the lines of the wvdial file by running: sudo wvdialconf /etc/wvdial.conf

Init3 I got from [www.mybroadband.co.za](www.mybroadband.co.za) forum...

*Apparently* I do not need a username and password (but wvdial needs entries there so I just added the A and B&#8230;)

This is the output I get when I run wvdial:

```
thenailedone@eclipse:~$ sudo wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvModem<*1>: Cannot get information for serial port. 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: at+cgdcont=1,"ip","vdata" 
WvDial Modem<*1>: at+cgdcont=1,"ip","vdata" 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATDT*99# 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATDT*99# 
WvDial Modem<*1>: CONNECT 
WvDial<*1>: Carrier detected.  Starting PPP immediately. 
WvDial<Notice>: Starting pppd at Sat Dec 15 21:58:42 2007 
WvDial<Notice>: Pid of pppd: 6822 
WvDial<*1>: Using interface ppp0 
WvDial<*1>: Disconnecting at Sat Dec 15 21:59:13 2007 
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16) 
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages 
and the wvdial and pppd man pages for more information. 
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds 
```

Between *WvDial<*1>: Using interface ppp0* and *WvDial<*1>: Disconnecting at Sat Dec 15 21:59:13 2007* there is a 30 second delay&#8230; 


Issues I think my be causing my problems connecting

1. I noticed this error message straight after running wvdial: *WvModem<*1>: Cannot get information for serial port.*

2. I also don&#8217;t know if my chosen user name and password could be an issue&#8230;

3. 64-bit OS issue?

4. I struggled in the beginning to connect in XP too&#8230; and then one day it worked&#8230; could there be a delay in connecting and how do I increase the time Ubuntu will wait before it disconnects (if it is my PC disconnecting and not Virgin Mobile)?

:-/

---

### Post by thenailedone on 2007-12-31
I think two weeks is a reasonable time to wait... *BUMP*

---

### Post by scorp123 on 2008-01-02
Hmmm ... I dunno if this will be of much help ...

Samsung SGH-G800 as modem under Linux (via BlueTooth):
[http://ubuntuforums.org/showpost.php?p=3943475&postcount=1](http://ubuntuforums.org/showpost.php?p=3943475&postcount=1)

... not sure how much this would help you? Maybe your Samsung is similar enough to mine so that the config I suggest there might work?


Sharp 770 SH as UMTS modem under Linux (via USB):
[http://ubuntuforums.org/showpost.php?p=3751898&postcount=2](http://ubuntuforums.org/showpost.php?p=3751898&postcount=2)

... again, not sure if this will help you. But take a look at the parameters I use, e.g. with my stupid Sharp I have to put "Stupid Mode = yes" into my config because otherwise my phone tries being 'smart' (too smart!) and messes up. Maybe it's something similar in your case? Try some of the parameters such as "stupid mode" and post back if it helped.

Also, what I'd suggest is to "get to know your phone" by "having a chat" with it via "minicom". See here:
[http://ubuntuforums.org/showpost.php?p=3808468&postcount=13](http://ubuntuforums.org/showpost.php?p=3808468&postcount=13)
[http://ubuntuforums.org/showpost.php?p=3814290&postcount=17](http://ubuntuforums.org/showpost.php?p=3814290&postcount=17)

Plug-in your phone via USB (I assume that's how you connect to it, right?) and check for any messages you get via "dmesg". And then follow my suggestions in that second posting up there: have a chat with your "modem" via "minicom" and ask some stuff, e.g. "ati1", "at+cgdcont?" and stuff like that (again, please see the second link a few lines up from here), and see what your phone says, if it says anything at all.

If you can get it to talk to you via "minicom" then your problems are already 99% solved.

I hope all this helped at least a little ....  :)

---

### Post by shafin on 2008-01-02
set your username and password both to xyz in the wvdial.conf file.See if it does the work.
also add ```
New PPPD = yes
``` under the baud line

---

### Post by scorp123 on 2008-01-02
> **shafin said:**
> set your username and password both to xyz in the wvdial.conf If no username and no password are needed it's better to leave those parameters empty, e.g. ```
Username = ''
Password = ''
```

---

### Post by thenailedone on 2008-01-18
:(

Tried all the remedies and nada... nothing... zip... zero... zilch...

---

