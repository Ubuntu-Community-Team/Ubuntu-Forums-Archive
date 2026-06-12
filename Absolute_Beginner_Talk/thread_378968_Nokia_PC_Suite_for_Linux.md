---
title: "Nokia PC Suite for Linux?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by Bideshi on 2007-03-07
We live in Bangladesh and the only way for us to access the internet is via GPRS using our Nokia phone as a modem.  Up to now, we have used Nokia PC Suite.  We have just bought a desktop and installed Ubuntu 6.06 on it.  Checking on the Nokia website, it would appear that they only have PC Suite and cable drivers that are Windows compatible.

Does anyone have any experience of using a GPRS modem on Ubuntu?
If so, where did you access the software?

Any tips and help would be gratefully received.

---

### Post by Sidster on 2007-03-08
What phone do you have? Do you have bluetooth on your PC?

I've managed to get most things working with my N91 on 6.10 (Edgy Eft)

---

### Post by Bideshi on 2007-03-08
We have a 6610i with a DKU-5 cable.  We have been using it succesfully on Windows but then PC suite was designed for that.  Are you using PC suite?  If not, how did you get the cable/modem driver set up etc?

---

### Post by Bideshi on 2007-03-08
I have just read the nokia forums.  Most unhelpful.  A few people seem to have the same issue but there is no official response from nokia and they appear not to want to release a linux version.  However, I was directed to the following site, [http://www.kmobiletools.org/](http://www.kmobiletools.org/),  which is has open source software for mobiles.  I am a programming novice so will have to spend some time seeing how easy it is to use but I will get back with more news later.

---

### Post by Marsolin on 2007-03-08
I'd try [KMobileTools]("http://linuxappfinder.com/package/kmobiletools") first, but if it doesn't work for you, [Wammu]("http://linuxappfinder.com/package/wammu") is another option.  It lists the 6610 as supported, but I'm not sure how different that is from your 6610i.

KMobileTools is capable of using the Gammu backend that Wammu uses, but it isn't the default.

---

### Post by Bideshi on 2007-03-10
Thanks, we have followed these two links but are unclear as to whether they enable connection to the internet or just mobile phone synchronisation.  Do you know?  When we installed PC suite on Windows, we had to load drivers and software, get phone recognised as a modem and connect phone to computer via serial cable.  We assume something similar needs to be done here but we are flummoxed by step 1.

We have followed up links from other threads to GPRSEC but this doesn't seem to support our Bangladeshi provider.  Ultimately, even if we are competent enough to get it all loaded, this might prevent us using ubuntu for web access.

Unfortunately, if we cannot resolve this issue we will have to go back to using Windows.

---

### Post by Marsolin on 2007-03-10
It may just be syncronization. Another alternative you be installing the Windows version using Wine. All you have to do in install wine from the repos, and then select the exe file for Nokia's program just like you would in Windows. The winehq website isn't responding for my this morning so I'm not able to check and see if anyone has reported an experience with the Nokia PC suite yet.

---

### Post by loneowais on 2007-07-31
I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT="Fixedsys"][COLOR="Red"]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT="Fixedsys"][COLOR="Red"]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected

---

### Post by babysteps on 2007-07-31
[QUOTE=loneowais;3108693]I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$                            

I'm excited to have found this post. I have a Nokia 9290 that connects to the laptop with a serial cable.   What command would I issue instead of 'lsusb' to get the vendor and product ID? Also, how would I continue with the next part of the command, if at all possible?

Thanks for your help!

Babysteps

---

### Post by loneowais on 2007-07-31
> **babysteps said:**
> [QUOTE=loneowais;3108693]I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$                            

I'm excited to have found this post. I have a Nokia 9290 that connects to the laptop with a serial cable.   What command would I issue instead of 'lsusb' to get the vendor and product ID? Also, how would I continue with the next part of the command, if at all possible?

Thanks for your help!

Babysteps
LSUSB is a command which shows you usb devices connected at a perticular time...so  the command is same for all....

And the tutorial applies to any Nokia Phone in the universe...havnt tried it on any other phone than nokia...may work with others like moto, samsung, SE, etc but not sure....Nokia works for sure...

Good Luck

---

### Post by Lord Grover on 2007-07-31
> **loneowais said:**
> 
<USEFUL STUFF>

Very useful - thanks.

---

### Post by chrismine on 2007-10-10
> **loneowais said:**
> I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT=Fixedsys][COLOR=Red] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT=Fixedsys][COLOR=Red]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT=Fixedsys][COLOR=Red]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT=Fixedsys][COLOR=Red]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected

CAn this be done with a bluetooth connection? Phone is Nokia 6234.

Thanks.

---

### Post by omiazad on 2007-10-20
You don't need Nokia PC Suite to access Internet with your phone. Here is a little how to I wrote long ago in Bangla. So it would be helpful to you. It works even in Ubunto 7.10. Have a look at [here]("http://omi.net.bd/?p=104") and [here.]("http://omi.net.bd/?p=114") I assume you use GrameenPhone.

Let me know if you fail. [Some Linux stuff is also available in Bangla.]("http://omi.net.bd/?cat=8")

---

### Post by MrKlean on 2007-10-20
I use wvdial and it works great ....I connect a bit faster than dialup since I don't have 3g where I use it...but better than nothing LOL!!

---

### Post by samkaleke on 2007-10-24
i have gone up to the end of the whole process but i still cant connect to the net. i keep getting the nessage "subscribe to packet data",but i can easily connect with windows. am based in malawi and am on Celtel network.my question is,

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = username
Password = password
Stupid Mode = 1

on dialer defaults, is anything supposed to be the same regardless of where one is based? the phone=*99#? my phone is nokia 5300.

please help

---

### Post by jpastore on 2007-10-30
I want to sync my Nokia 9500 with Evolution. 

I can see my phone with lsusb:
```

Bus 004 Device 004: ID 0421:0405 Nokia Mobile Phones 9500 GSM Communicator

```

and when I do dmesg I get:
```

[26328.708174] usb 4-2: new full speed USB device using uhci_hcd and address 5
[26328.809597] usb 4-2: configuration #1 chosen from 1 choice
[26328.822504] cdc_acm 4-2:1.12: ttyACM0: USB ACM device

```

I can't seem to get wammu to recognize the phone, SyncML didn't quite work out but I could find explicit instructions for someone whose enver sued it before. Any thoughts or maybe a link to some documentation would be appreciated.

---

### Post by _cc on 2007-11-26
Hi, im planning to buy Asus Eee PC which default OS is Linux but compatible with Windows..

This is also one of my problem if Pc Suite will work in Linux..

thread will help me.. thanks

---

### Post by boob11 on 2007-11-29
thnx    :)

---

### Post by gbolahr on 2007-11-29
Hi Guys/ladies,
i get the output below when i try the sudo/sbin/modprobe command.i am using a nokia N95.


gbolahr@gbolahr-desktop:~$ sudo lsusb
[sudo] password for gbolahr:
Bus 007 Device 002: ID 046d:08ce Logitech, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:04ed Nokia Mobile Phones 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
gbolahr@gbolahr-desktop:~$ sudo/sbin/modprobe usbserial vendor vendor=0x421 product=0x4ed
bash: sudo/sbin/modprobe: No such file or directory
gbolahr@gbolahr-desktop:~$ 

since it says the directory cannot be found,do i try to create it? or is the output above based on the line of data for my phone....ID:0421:04ed??
pls advise...
thanks

---

### Post by REDISISTone.nl on 2007-12-03
Hello,

I want to connect to the internet with my Nokia N95 and Ubuntu 7.10.

I did wat the Howto said but I get this an error output. First my config:

```

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Stupid Mode = 1
```

(I found on the t-mobile site I should make Username and Password tmobile)

Next the output of the wvdial (as sudo)

```
reinier@reinier-laptop:~$ sudo gedit /etc/wvdial.conf
reinier@reinier-laptop:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Mon Dec  3 12:31:18 2007
WvDial<Notice>: Pid of pppd: 32537
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: Disconnecting at Mon Dec  3 12:31:24 2007
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
```

And the hole thing will try to reconnect without any result. I even got my phone connected but that doesn't work...

Got any suggestions?

---

### Post by subs on 2007-12-03
> **Marsolin said:**
> I'd try [KMobileTools]("http://linuxappfinder.com/package/kmobiletools") first, but if it doesn't work for you, [Wammu]("http://linuxappfinder.com/package/wammu") is another option.  It lists the 6610 as supported, but I'm not sure how different that is from your 6610i.

KMobileTools is capable of using the Gammu backend that Wammu uses, but it isn't the default.

thnx.... finally my nokia phone works on my ubuntu installation!!

---

### Post by karthikophobia on 2007-12-03
Im using NOKIA 6670
Can u tell me how to access my phone's memory using the data cable

Thanq

---

### Post by REDISISTone.nl on 2007-12-04
> **REDISISTone.nl said:**
> Hello,

I want to connect to the internet with my Nokia N95 and Ubuntu 7.10.

I did wat the Howto said but I get this an error output. First my config:

```

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Stupid Mode = 1
```

(I found on the t-mobile site I should make Username and Password tmobile)

Next the output of the wvdial (as sudo)

```
reinier@reinier-laptop:~$ sudo gedit /etc/wvdial.conf
reinier@reinier-laptop:~$ sudo wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Mon Dec  3 12:31:18 2007
WvDial<Notice>: Pid of pppd: 32537
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: pppd: X&#65533;[06][08][18]&#65533;[06][08]
WvDial<*1>: Disconnecting at Mon Dec  3 12:31:24 2007
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
```

And the hole thing will try to reconnect without any result. I even got my phone connected but that doesn't work...

Got any suggestions?

Anybody?

---

### Post by atomkarinca on 2007-12-04
> **karthikophobia said:**
> Im using NOKIA 6670
Can u tell me how to access my phone's memory using the data cable

Thanq

Just plug in your data cable through USB and  your phone should be mounted automatically. When you want to unplug it, just right-click the folder select unmount.

---

### Post by Megabite on 2007-12-09
> **loneowais said:**
> I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT="Fixedsys"][COLOR="Red"]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT="Fixedsys"][COLOR="Red"]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0?

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: ?[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: ?[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: ?[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected

Thank God I found this post! This is so great! I was so afraid that my Nokia phone will not work with Ubuntu, becouse I acess the internet like Bideshi - using my phone as a modem. So thank you so much for sharing this technique.

---

### Post by ashzoomerintrack on 2007-12-12
> **atomkarinca said:**
> Just plug in your data cable through USB and  your phone should be mounted automatically. When you want to unplug it, just right-click the folder select unmount.

Such a thing is not happnening in my case. I have Nokia 6630 it shows the device on lsusb but i am not able to access its memory card. Plz guide me.....................

---

### Post by atomkarinca on 2007-12-12
When you plug your USB cable to your phone, it should bring up 3 options:

- Nokia mode,
- Printing & media,
- Data storage

select "Data storage" and your phone should be mounted and a shell should open, displaying  your phone's memory.

---

### Post by azn804 on 2007-12-14
> **loneowais said:**
> I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT="Fixedsys"][COLOR="Red"]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT="Fixedsys"][COLOR="Red"]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected


This part help me alot in trying to connect the n95 but the second section is missing a piece of line which cause the N95 to not connect. Follow all the steps that "loneowais" discribe until you get to to this part:

[COLOR="RoyalBlue"][FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1[/COLOR]

What you are going to put in place of that is this: just copy the entire thing to the "/etc/wvdial.conf"

[COLOR="DarkOrchid"][Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Init3 = AT+CGDCONT=1,"IP","internet2.voicestream.com";
Stupid Mode = 1[/COLOR]

What is different is that I added the last Init3 to the commend to tell to to connect to t-mobile server. This is for unlimited no VPN internet. If you want t-zone, use wap.voicestream.com. with VPN, use internet 3.voicestream.com.

this will help anyone who have Ubuntu Gusty and a N95 (which has been tested to work by me) or any other Nokia (not tested). good luck and let me know if this works for u.

If it does work with the setting above, I also made some changes using this link,
[http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php](http://www.linux.ie/articles/tutorials/threeirelandUSBmodem.php)
just follow the guide but input your own variables.

---

### Post by msn2104 on 2007-12-26
> **loneowais said:**
> I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT="Fixedsys"][COLOR="Red"]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT="Fixedsys"][COLOR="Red"]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected


Many thanks to loneowais...
Works perfect for me..Am using nokia 6630 and Malaysia's Celcom 3G.

[Dialer Defaults]
Modem = /dev/ttyUSB0
0Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = celcom3g
Password = celcom3g
Stupid Mode = 1

---

### Post by Biggy on 2007-12-26
try Bluetooth Manager called Blueman. [http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)

---

### Post by gein on 2007-12-28
Im using 2 apps:
gnome-phone-manager
gnokii
with all libs thiese apps can do everything that nokia pc suite does and even more. I have N91 and I connect it through BlueTooth, but USB cable works fine to.

---

### Post by chrismine on 2007-12-28
> **gein said:**
> Im using 2 apps:
gnome-phone-manager
gnokii
with all libs thiese apps can do everything that nokia pc suite does and even more. I have N91 and I connect it through BlueTooth, but USB cable works fine to.

Please post how did you do the gnokii configuration. Have Xgnokii installed and it just freeze. I have read a lot of posts and still cannot get it to work.

I use Nokia 6234 with bluetooth - blueman, Phone Manager and  Multisync-quad all works for me - sometimes even gMobileMedia works.

Thank you.

---

### Post by pinta_vodki on 2008-01-22
Can anyone help me please? I have followed the instructions and my phone connects to the internet, but I can't open any page in web-browser... What can be wrong??

---

### Post by trileru on 2008-02-24
Hello. I wanna install *,sis software on my E51 but dunno how withouth Nokia suite. Is there an alternate software that can install sis files on my nokia?

---

### Post by gorg_karlo on 2008-04-12
The instructions posted on this thread has absolutely pushed me to go Ubuntu all the way!

Just a quick note - the instructions work on Nokia 6500s

---

### Post by changlinn on 2008-04-17
> **azn804 said:**
> 

What you are going to put in place of that is this: just copy the entire thing to the "/etc/wvdial.conf"

[COLOR="DarkOrchid"][Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = tmobile
Password = tmobile
Init3 = AT+CGDCONT=1,"IP","internet2.voicestream.com";
Stupid Mode = 1[/COLOR]



Thanks azn804 I had the order of it wrong. Mines below for Vodafone in australia with the Nokia n95 via USB.

[COLOR="blue"][Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = vf
Password = vf
Init3 = AT+CGDCONT=1,"IP","vfinternet.au";
Stupid Mode = 1[/COLOR]

---

### Post by qwert13 on 2008-04-22
does any one have a recommendation for a nokia 3500 classic?
Some kind of nokia-pc-suite-like app that works without greater trouble?

---

### Post by rphil2008 on 2008-04-22
Thanks a lot for sharing this technique guys. Kudos especially to:

lonewais and azn804.

I followed lonewais instgructions to the letter. Although I encountered errors, I was able to deal with them. In the tip given by azn804, its right on target with my own mobile. It will not connect to the internet without that line beginning with Init3...

For the benefit of fellow users in particular those with Smart 3G phones from the Philippines, here's how I did it.

1. Followed lonewais instructions.
2. Encountered error " cannot write to .../pap-secrets"
3. Encountered error "cannot write to .../chap-secrets"
4. Resolved 2 and 3 by changing ownership of those files to user, myself.
5. Encountered error "failed to connect (113 no route to host)"
6. Resolved error 5 by creating a file /etc/apt/apt.conf which contains these lines of code:

Acquire {
Retries "0";
HTTP {
Proxy "http://smart.com.ph:8080";
};
};

7. Encountered error "cant connect/ modem hung up" or something like that
8. Resolved error 7 by adding Init3 as mentioned by azn804,, specifically for Smart Communications. Here's the wvdial.conf code:

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = smart
Password = smart
Init3 = AT+CGDCONT=1,"IP","internet";
Stupid Mode = 1

Finally, close all terminals and windows and all running applications. Open a terminal again and type wvdial. It will list some IP addresses and appear to hang up on the last line (see picture.) This is your cue. You're in business!

I was able to connect to the internet and also download updates from available servers. The connection is very slow but then it was a big thing for me to be ale to surf using my Nokia6233 at P10/half hour. Not too bad.
 
Here is a screenshot of the wvdial and downloading updates window:

[IMG]http://img257.imageshack.us/img257/6109/screenshotgm5.png[/IMG]

And here is the Ubuntu Website as it appeared yesterday on my browser, also  using my Nokia6233 as my new modem:

[IMG]http://img504.imageshack.us/img504/4461/screenshot2ml8.png[/IMG]

Did I mention I am posting this right on my laptop with the Nokia6233 as modem with wvdial? Heheh=) I hope I also contributed something back. Thanks guys!

---

### Post by hemajith on 2008-07-01
> **loneowais said:**
> I did it on a nokia n80, n73, 6230(somethinsimilar..is a folder java phone), 7610, 6630 & 6680....

This is how to do it...

Connect your phone via datacable
open terminal & type    

[FONT="Fixedsys"][COLOR="Red"] lsusb[/COLOR][/FONT]

now u will get the following output
 
owais@owais-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0421:0445 Nokia Mobile Phones 
Bus 001 Device 002: ID 046d:092f Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
owais@owais-desktop:~$ 


it is on my compter,ur will  not be exactly the same...

Now note the line in which NOkia Mobile Phones is written...it has two number one is 0421 & other is 0445...we'll take these numbers as 0x421 & 0x445

0421 is the Vendor ID & 0445 is the Product ID

Now enter this comand.

[FONT="Fixedsys"][COLOR="Red"]sudo /sbin/modprobe usbserial vendor=0x(vid) product=0x(pid)

eg, in my case::: sudo /sbin/modprobe usbserial vendor=0×421 product=0×445[/COLOR][/FONT]

Now enter this command

[FONT="Fixedsys"][COLOR="Red"]wvdialconf create[/COLOR][/FONT]
 u'll get a long output which will be like 

Scanning your serial ports for a modem.
Port Scan: S0 S1 S2 S3
WvModem: Cannot get information for serial port.
ttyACM0: ATQ0 V1 E1 — OK
ttyACM0: ATQ0 V1 E1 Z — OK
ttyACM0: ATQ0 V1 E1 S0=0 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 — OK
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
ttyACM0: Modem Identifier: ATI — Nokia
ttyACM0: Speed 4800: AT — OK
ttyACM0: Speed 9600: AT — OK
ttyACM0: Speed 19200: AT — OK
ttyACM0: Speed 38400: AT — OK
ttyACM0: Speed 57600: AT — OK
ttyACM0: Speed 115200: AT — OK
ttyACM0: Speed 230400: AT — OK
ttyACM0: Speed 460800: AT — OK
ttyACM0: Max speed is 460800; that should be safe.
ttyACM0: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 — OK
Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0: Speed 460800; init “ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0&#8243;

NOw.. notice the output says that there is a modem at /dev/ttyACM0 & max speed is 460800

now enter this command

[FONT="Fixedsys"][COLOR="Red"]sudo gedit /etc/wvdial.conf[/COLOR][/FONT]

A file will open in text editor...now delete everything in that file & paste the following there

[Dialer Defaults]
 Modem = Your Modem Name(eg, /dev/ttyACM0 in my case)
 Baud = ur max speed(460800 in my case)
 Init1 = ATZ
 Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem
 Phone = *99#
 Username = username
 Password = password
 Stupid Mode = 1

save the file & you are done


NOw whenevr u need to connect...open terminal & type wvdial,,wait till some sort of IP adress is displayed like

pppd: &#65533;[06][06][08]` [06][08]
primary   DNS address 218.248.240.135
pppd: &#65533;[06][06][08]` [06][08]
secondary DNS address 218.248.240.79
pppd: &#65533;[06][06][08]` [06][08]

Now you are connected....hit cntrl+c to dissconnect...



U can also create a laucher on desktop(application in terminal) & keep the command as wvdial..now double click it & u r connected

WOW.. this is something I have been seeking for a very long time. Great work! I did all that and and when I hit wvdial, it dials but it dies out after dialing. It goes like this,

--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Jul  1 11:16:07 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 5969
--> Disconnecting at Tue Jul  1 11:16:07 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

My carrier's dial number is *99***1#. When this happened in windows, they gave me a script to insert to the advanced properties of the dial up. It's

AT+CGDCONT=1,"IP","www.dialogsl.com",,0,0

and it worked after that. Is there anywhere here that I have to insert this?

---

### Post by hemajith on 2008-07-01
oh I got it! it works. I did some syntax errors. I'm using a Nokia E65 and now it works. Thank you. This is great!

---

### Post by femolala on 2008-07-24
hi am in Nigeria i use nokia 7610 am having problem connecting to my laptop via the bluetooth   my os ubuntu

---

### Post by loneowais on 2008-07-24
Check this
[http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html]("http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html")

---

