---
title: "inernet problem"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by vanishedsoul on 2006-10-26
hey there, i 'm absolutely a new beginner of UBUNTU though i installed it in the first try :) :KS ... Now the problem is i tried to connect to the internet but was not able to connect. I did heard my modem connecting tone but after 10-15 seconds it was not dialing anymore. 

I have a dial up connection with US robotics v92  (external) model 5631... Tell you one thing that i haven't installed the modem yet. So any one here hows ready to help a beginner???:-#  thanks

---

### Post by Jussi Kukkonen on 2006-10-26
If that is a winmodem you might have some work ahead of you... On the other hand the connect tone is a good sign.

Try here: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
You might try skipping the driver installation step since it's possible that you have the driver already. So start with *Configuring the dialup connection to your provider*.

---

### Post by vanishedsoul on 2006-10-26
after making a connection does it make any kind of icon in the UBUNTU like in windows it makes 2 monitors in the system task bar, how do we get know in the Ubuntu that we have been connected??

---

### Post by Mark_in_Hollywood on 2006-10-26
Please try this:

open a terminal (or console if you call it that)

type:

sudo wvdial

leave the terminal window open. WvDial will report it's connection log as it handshakes, sends passwords, etc.

If that works, and you can surf, you need to change the ownership of some files, the names of which I don't have at hand.

TO LOG OFF: CTRL-C

DON'T close the terminal window, until the modem has hung up and returned you to your prompt.

If it doesn't work, I need to know the maker and model of your modem. Whether it's internal or external and whether it's a Win/Lin Modem, that is there is no "host controller" on the modem board. It would look like a tiny power transformer.

If you have a Lin/Win you need extra sofware drivers. Of which, more from me, after we determine the problem a little further.

Bon Chance!

---

### Post by vanishedsoul on 2006-10-27
thanks for responding... 

Well let me first tell you what I'm using. Its a 

**"US Robotics 56k Faxmodem - V.92 ( EXTERNAL)" having a "MODEM MODEL 5631" and its connected to my "com1"**

here is the modem image [http://www.usr.com/images/products/product-emea.asp?prod=5631&loc=grmy](http://www.usr.com/images/products/product-emea.asp?prod=5631&loc=grmy)

others are:

**"intel 945GNT motherboard with Pentium D 2.66 (dual core) with kingston's 512 mb of Ram (DDR2)"**


well i tried your first part and here are the results

[B]gangsta@gangsta-desktop:~$ sudo wvdial

Password: 
WvDial: Internet dialer version 1.55
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory
Cannot open /dev/modem: No such file or directory[/B]

Also a strange thing happened (at least to me), before executing the above command (wvdial), i switched on the modem and booted the pc and then back to the UBUNTU and when in the beginning the UBUNTU was asking for the user =name ans the password, the started dialing and got connected and after almost 5-10 sec it got disconnected???? Any clues?

As far as i have read, It does not fall in the category of the Win/Lin modem. I also used the ScanModem Tool from [WWW].linmodems.org and scaned the system through it. In one of the files Modemdata.txt it was written that it didn't found any of the USB modem(btw its not a usb modem, its connected to the com1).

Then i have read about the hardware modems and they said they don't need the any special driver. So i started configuring the connection through "pppconfig & pon/poff" but i didn't know the "PAP Peer Authentication Protocol" so i have to end it here. 

Next, i tried to configure it through "wvdialconf & wvdial". The modem was detected through the wvdialconf but now I'm stuck at adding the phone number, username and password in the wvdial.conf file. i have tried several places but still when i dial the modem work fine up to the checking of the ph. number, pass, and username. 

LIKE:

[B]gangsta@gangsta-desktop:~$ 

sudo wvdial

 WvDial: Internet dialer version 1.55

 Initializing modem.
--> 
Sending: ATZ
ATZ
OK
--> 
Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK

--> Modem initialized.

--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
gangsta@gangsta-desktop:~$[/B]

and please do tell in which way i have to add the particulars. If you can write the whole line or please share your wvdialconfig file so that i can do it.

One more thing how can i get the **PAP Peer Authentication Protocol**??

And please don't tell me that i did this whole work for nothing, thanks

---

### Post by caravel on 2006-10-27
Your modem is not a winmodem, it's a good external serial modem.  

Try /dev/ttyS0 or /dev/ttyS1 (check which serial port you're connected to) instead of /dev/modem or create the symbolic link:

e.g. ```
ln -sf /dev/ttyS0 /dev/modem
``` links the 'modem' device to COM1.

There is some information specific to wvdial here: [http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm](http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm)

---

### Post by vanishedsoul on 2006-10-27
hey thanks for responding, the modem is connected to the COM1 but i think in UBUNTU will treat as one less than the comport to which is connected like actually is COM1 then it is "ttyS0".

---

### Post by vanishedsoul on 2006-10-28
i have been able to configure the wvdial and now it is dialing but the after the dialing and making the connecting tone, almost after 10 secs it gets disconected and then it again try try to redial the connection. Now what i do now?? also do tell me how i can stop it to redial?

---

### Post by razo559 on 2006-10-29
hello, i was reading the problem you had with the dial up cause i have the same problem, but for me i was only able to get up the step were i input 

"ln -sf /dev/ttyS0 /dev/modem" i get this error:

razo@razo-laptop:~$ ln -sf /dev/ttyS0 /dev/modem
ln: creating symbolic link `/dev/modem' to `/dev/ttyS0': Permission denied

i dont know why i get this error, can anyone help me, thanks

---

