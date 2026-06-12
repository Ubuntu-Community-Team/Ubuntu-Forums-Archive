---
title: "cell phone as modem"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by linuxn00b73 on 2006-12-14
Greetings!
     The main thing I use on my laptop is the internet. Currently it has WinXP and is set up to use my cell phone as a modem to connect from anywhere. Can I do this with ubuntu?

It shows up in device manager under the usb section as :

SCP-4900 cellphone (it's really an SCP-5500 though) 
      ---USB Communications Interface
                ------Serial Port
      ---USB Data Interface
      ---USB Raw Device Access

Appreciate all the help I can get.

---

### Post by dbd on 2006-12-14
This how-to looks like it could be useful:
[http://ubuntuforums.org/showthread.php?t=166617](http://ubuntuforums.org/showthread.php?t=166617)

---

### Post by linuxn00b73 on 2006-12-14
Thanks, I'll check it out

---

### Post by linuxn00b73 on 2006-12-14
hmmm... doesn't seem to work. wvdial cannot find modem. I've read though a few more articles and tried everything. I can't believe it's so difficult to get the phone to work as a usb modem in linux. Mac and WinXP have easy connection software to get on the internet with a cell phone, but everything I've found so far on getting it to work on linux seems complicated.
**Anyone know a small fast linux I can use a phone as modem for a laptop?**
It's got  1.5Ghz Pentium M / 512 MB PC2700.  I wanted to switch from XP to a small super fast linux, but it must be able to use phone as modem for the internet.

---

### Post by dbd on 2006-12-15
I'm not aware of any software that makes it really easy in Linux I'm afriad. And I don't think that different distributions would make it particularly easier to get it to work with than with Ubuntu, although it may be worth trying out a few different live CDs if you are having lots of problems which may be Ubuntu, specific.

Have you looked on this site?:
[http://www.tuxmobil.org/phones_linux.html](http://www.tuxmobil.org/phones_linux.html)

Good luck

---

### Post by linuxn00b73 on 2006-12-15
Thank you. These scripts seem to work much better. I actually got a data connection this time but when I tested it with firefox things went funny. I think with a little tweaking I can get this to work.
 Someone really should make a program with a drop down box where you select your phone/mobile card and it sets up a connection in linux. With the popularity of mobile broadband these days, it's odd no one has come up with a linux version yet. Don't know if maybe one could get the info needed out of the M$ or Mac versions and translate it to linux.

---

### Post by dbd on 2006-12-16
> **linuxn00b73 said:**
> Thank you. These scripts seem to work much better. I actually got a data connection this time but when I tested it with firefox things went funny. I think with a little tweaking I can get this to work.
Glad to hear it.
> **linuxn00b73 said:**
> Someone really should make a program with a drop down box where you select your phone/mobile card and it sets up a connection in linux. With the popularity of mobile broadband these days, it's odd no one has come up with a linux version yet. Don't know if maybe one could get the info needed out of the M$ or Mac versions and translate it to linux.
Sounds like a good idea, well volunteered! ;)

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

### Post by niteshifter on 2007-12-13
Hi all,

I agree - it would be nice if someone was to write a GUI app to make this painless as possible. I thought about doing one myself but here's the problem: There are no standards for doing this. Every cell service provider out there has their own specific way they wish connections to be made, particularly modem initialization strings, also by which phone "number" to use. And they can change them whenever they want and answer to no one (at least in the USA. They answer to the FCC - which doesn't really "do" consumer concerns ;) )

This is how I use my Motorola RAZR V3 with USB or Bluetooth on Cingular / ATT via wvdial.

wvdial needs a configuration file ( /etc/wvdial.conf ), below is mine: (see notes at end about the various entries)
```
[Dialer V3USB]
Baud = 921600
Modem = /dev/ttyACM0
Dial Command = ATDT
Init2 = AT+CGDCONT=1,"IP","isp.cingular"
Phone = *99***1#
Username = ISP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
Stupid mode = 1

[Dialer V3BT]
Baud = 921600
Modem = /dev/rfcomm0
Dial Command = ATDT
Init2 = AT+CGDCONT=1,"IP","isp.cingular"
Phone = *99***1#
Username = ISP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
Stupid mode = 1

```

Invoke with the command line (for bluetooth):
```
sudo wvdial V3BT
```

For USB:
```
sudo wvdial V3USB
```

or use this bash script :
```
#!/bin/bash
# Dialup method chooser script for Mototola V3 phones
#  You must:
#   A) Have already configured bluetooth to work with the phone.
#   B) Have wvdial installed and edited wvdial.conf with your required settings
#  This script's purpose is to save a bit of remembering and typing ;)
#
echo Motorola V3 dialup connection by:
OPTIONS="Bluetooth USB Quit"
select opt in $OPTIONS; do
    if [ "$opt" = "Quit" ]; then
        echo Done
        exit
    elif [ "$opt" = "Bluetooth" ]; then
        echo Dialing out with Bluetooth...
        sudo wvdial V3BT
        exit
    elif [ "$opt" = "USB" ]; then
        echo Dialing out with USB...
        sudo wvdial V3USB
        exit
    else
        echo Bad choice!
    fi
done

```

If one is going to connect only one way (USB or BT) then you don't need the other section, nor do you need to include section names - the text within the brackets [ ]. You'd also invoke wvdial like this:
```
sudo wvdial
```


**Notes on wvdial.conf contents**

*Baud* - Is set high here - was testing compatibility with a V3xx (HSDPA). Still works with a common V3 (GPRS), so I never changed it back :) However, other phones may not be so tolerant, more "reasonable" rates for GPRS / EDGE / EV-1 phones are 115200 or 230400. 

*Modem* - You need to find this in your system. Generally USB phones show up as a tty device. Easy way to see what you phone's USB device name is:

Do this with phone disconnected. (That's the digit 1 after the dash)
```
ls -1 /dev > nophone.txt
```

Connect the phone. Now do this.
```
ls -1 /dev > withphone.txt
diff nophone.txt withphone.txt

```
Should show the phone's tty entry in /dev on the second line.

*Init2* - will vary with cell service provider. How did I work this out? Pretty much all cell providers will provide a Windows app that uses Windows DUN. Which is what I did: Use Cingular's Communication Manager set up and make a connection with it in Windows XP, then look in Win's XP Control Panel under Phones and Modems. Examine the properties of the newly created USB or Bluetooth modem. Hopefully this will work for you as well. If you don't have Win XP, borrow a friend's system or find someone who also uses a cell phone as modem on your service. Last resort: Call your service's customer support - and be prepared to spend some time doing this, making muliple calls. Not to bash call center help, but what you want is NOT in their main experience. You might be better off spending some time with Google.

*Phone* - also varies with cell provider. Same trick as Init2 setting.

*Username and Password* - also varies with cell provider. And - before anyone freaks: yes I published my username and password. Doesn't matter - all users of a cell service provider's data plan will have the exact same name and pass. The cell network identifies and authenticates via IMEI / SIM card data.


**Notes on Bluetooth connecting**

Bluetooth connection requires that bluetooth be configured. That varys depending upon bluetooth support installed. For Edgy with bluez I had to do two things:

1) Pair the computer and phone. This is easist by sending something from the phone to the computer (like an image file). I needed to install gnome-bluetooth to get OBEX functionality in Gnome so as to be able to pair the two. Fiesty and Gutsy users I think already have this or the equivalent.

2) Edit this file: /etc/bluetooth/rfcomm.conf

I think Feisty and Gutsy users will also need to do the steps below, but I've not tried it with those two versions. Would be lovely if someone were to clarify this.

You'll need the bluetooth MAC address of your phone. Use hcitool to find it, make your phone disoverable first:
```
hcitool scan
```

That will return a list of BT devices found. Look for your phone's name (at the end of the line(s)). Your phone's MAC is the text at the first of the line, will be in the form of XX:XX:XX:XX:XX:XX

Write the MAC address down.

Now use sdptool to find your phone's BT capabilities:
```
sdptool browse XX:XX:XX:XX:XX:XX
```

Where XX:XX:XX:XX:XX:XX is your phone's MAC. A lot of information is returned here. What we want to find is the section called "Dial-up networking Gateway" or similar text. Look for this line:

Channel: Y

Write down that number. Now edit /etc/bluetooth/rfcomm.conf and plug the MAC and channel numbers in, below is mine for reference with the MAC as X's and the channel is Y:

```
#
# RFCOMM configuration file.
#

rfcomm0 {
	# auto bind at start
	bind yes;
	# my V3's MAC
	device XX:XX:XX:XX:XX:XX;
	# RFCOMM channel is 1 as reported by sdptool browse
	channel Y;
	# Description
	comment "V3 Bluetooth"
}

```

**Notes about Cingular (now ATT): **

You must - repeat MUST - have the Laptop Data Connect Plan. No other, and certainly not MediaNet. "Tethering" - the act of using your phone as a modem - is only allowed on that plan. Now, you'll be able to connect with other plans, like MediaNet or PDA Data Connect with apparently no problems (although FTP and SSH and some other protocols don't work with MediaNet) but you will be in violation of ATT's Terms of Service. You could wind up being changed "out of bucket" rates which can translate to a multi-kilo-dollar phone bill. No kidding. I spent over six weeks last year getting my accounts set up properly and narrowly avoided a sky-high bill.

---

### Post by bharadwaj on 2008-01-28
thanx this helped

---

### Post by JoshuaRL on 2008-01-28
Nice.  I haven't tried this, but it sounds good.  I have this to offer:

For Verizon, the number is #777, the username is [email]0000000000@vzw3g.com[/email] (where the 10 digits are your phone number), and the password is "vzw".

Sweet.

---

### Post by mlissner on 2008-01-29
This may be a silly question, but is it possible to use a phone to dial up to an Internet ISP, and leave the GPRS part out of it? That would be my goal, since I only need my phone occasionally, and it seems like it ought to work.

---

### Post by doi65535 on 2008-01-31
i managed to connect to the internet through my cellphone via gprs dialup by usb cable and bluetooth. i used bluez-utils with wvdial on xubuntu on asus eeepc and a motorola v1075 phone on vodafone in romania

my actual problem was pairing the phone to the computer because otherwise wvdial did a good job connecting via a usb cable with little or no work at all from my side. i just followed

[http://ubuntuforums.org/showthread.php?t=166617&highlight=bluetooth+dialup](http://ubuntuforums.org/showthread.php?t=166617&highlight=bluetooth+dialup)

and usb dialup worked

how i did it:

- configure wvdial with the usual stuff for gprs dialup (you have my config file below for usb and bt). the first part is for usb dialup through the mobile phone, the other one for bluetooth dialup, anyway the only difference is the modem device, other settings are identical

[Dialer cb]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT E0
Init4 = AT+CGATT=0
Init5 = AT+cgdcont=3,"ip","internet.vodafone.ro",,0,0
Init6 = AT+CGQREQ=3,0,0,0,0,0
Init7 = AT+CGQMIN=3,0,0,0,0,0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99***3#
Password = vodafone
Username = internet.vodafone.ro
Stupid Mode = 1

[Dialer bt]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT E0
Init4 = AT+CGATT=0
Init5 = AT+cgdcont=3,"ip","internet.vodafone.ro",,0,0
Init6 = AT+CGQREQ=3,0,0,0,0,0
Init7 = AT+CGQMIN=3,0,0,0,0,0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/rfcomm0
ISDN = 0
Phone = *99***3#
Password = vodafone
Username = internet.vodafone.ro
Stupid Mode = 1

- get bluetooth working and run

hcitool scan

to find your phone, write down its mac, use 

sdptool browse XX:XX:XX:XX:XX:XX

to find the channel dialup works on, then setup /etc/bluetooth/rfcomm.conf with the device you want to use. you can easily find this somewhere on the forum or on ubuntuhelp

- create a file (/etc/bluetooth/bluepin in my case) containing:

#!/bin/bash
echo "PIN:123456"

- chmod 777 the file created above (don't ask me why)

- start in a terminal

sudo passkey-agent --default /etc/bluetooth/bluepin XX:XX:XX:XX:XX:XX

- you might have to (don't know if these two are needed)

sudo hcitool cc XX:XX:XX:XX:XX:XX

and

sudo hcitool auth XX:XX:XX:XX:XX:XX

- in another terminal run (corresponds to my wvdial config file)

sudo wvdial bt

- the phone will ask for pin and wait for you to input it, then ask if yo want to allow the dialup gateway service to be used and so on

- wvdial starts connecting and so on

---

### Post by SB-RAD on 2008-01-31
I found out a while back the GPRS or packet switched connections do not respond to PPP lcp-echo requests when I used SUSE a few years back.

When I commented out:

# lcp-echo-interval 30
# lcp-echo-failure 4

From /etc/ppp/options

the connection would no longer time out after 2 Min.

This is because you use AT commands for initiating a packet switched session but the PPP session is only between your PC and the modem in the device you are using.

Hope this helps!

---

### Post by mlissner on 2008-02-01
I'm trying to set up my phone as a modem (dial-up, not GPRS). Does anybody have any thoughts on that? 

I am forever caught in the "no carrier" problem listed here:
[http://ubuntuforums.org/showpost.php?p=4233209&postcount=4](http://ubuntuforums.org/showpost.php?p=4233209&postcount=4)

---

### Post by SB-RAD on 2008-02-04
Do you mean GSM Phone?

If you are trying to make a CSD (Circuit Switched Data) call you need to initialise the GSM modem to prepare the bearer to use for the call!

In this case it depends on what bearer you phone chipset has and is supported by the operator? And terminating modem!!!!

What speed and modulation are you trying to use, 9.6kbps at V.110?

---

### Post by mlissner on 2008-02-05
Wow. You kind of lost me there, but I think you're right that I want to use my phone to make CSD calls. Basically, I want to use my cell phone to connect to the internet as if it were an onboard modem on my computer that was connected to a phone jack. It seems like a logical thing to do.

I did a little more reading with your CSD term in mind, and I found one link that says Cingular has this feature turned off, so that might explain why it wasn't working.

I will try some more things, and see what I can learn.

---

### Post by SB-RAD on 2008-02-05
The AT command that may put you on the right track is:

AT+CBST=?

For example my data card has (It supportsGSM, 3G, HSDPA and HSUPA):

at+cbst=?
+CBST: (0,7,12,14,16,17,39,43,48,51,71,75,80,81,83,84,116,134),(0,1,4),(0,1)

+cbst:(Speed),(Name),(CE)

Must be in the above order!!!!!

Name and CE are normaly 0 or 1 though others may be supported by the network and card.

Name 0 = data circuit asynchronous
ame 1= data circuit synchronouse
Both are UDI or 3.1kHz modem connection

CE 0 = transparent
CE 1 = non transparent

The Speed parameter may have lots of options which again may or may not be supported, in the UK I tend to use the V.110 or V.120 ISDN speeds but here a a list of a few I have gathered

Speeds

0 Autobaud  makes for a slower connection time
1 300 bps (V.21)
2 1200 bps (V.22)
3 1200/75 bps (V.23)
4 2400 bps (V.22bis)
5 2400 bps (V.26ter)
6 4800 bps (V.32)
7 9600 bps (V.32)
12 9600 bps (V.34)
14 14400 bps (V.34) HSCSD over GSM
15 19200 bps (V.34) HSCSD over GSM
16 28800 bps (V.34) HSCSD over GSM
17 33600 bps (V.34) HSCSD over GSM
34 1200 bps (V.120)
36 2400 bps (V.120)
38 4800 bps (V.120)
39 9600 bps (V.120)
43 14400 bps (V.120) HSCSD over GSM
47 19200 bps (V.120) HSCSD over GSM
48 28800 bps (V.120) HSCSD over GSM
49 38400 bps (V.120) HSCSD over GSM
50 48000 bps (V.120)
51 56000 bps (V.120)
65 300 bps (V.110)
66 1200 bps (V.110)
68 2400 bps (V.110 or X.31 flag stuffing)
70 4800 bps (V.110 or X.31 flag stuffing)
71 9600 bps (V.110 or X.31 flag stuffing)
75 14400 bps (V.110 or X.31 flag stuffing)
79 19200 bps (V.110 or X.31 flag stuffing)
80 28800 bps (V.110 or X.31 flag stuffing)
81 38400 bps (V.110 or X.31 flag stuffing)
82 48000 bps (V.110 or X.31 flag stuffing)

Others exist but they are more for multimedia bearers such a video calling or I have not found them. Most will work over UMTS if the network supports it.

So if you set the initialization string:

at+cbst=0,0,1

it sets the Modem to operate with autobaud over an asynchronous
connection.

However if you know what your operator and destination modem supports you can force the GSM modem to use that.

I may at times use:

at+cbst=51,0,1  which is 56000 bps V.120, Asynchronous, Non-transparent.

---

### Post by davidpodhola on 2008-03-23
[QUOTE=niteshifter;3943631]

Thanks a lot, saved old S55 :)

---

