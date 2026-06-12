---
title: "External Modem Woes - USRobotics"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by araro23 on 2006-08-26
Its been three weeks since I have installed Ubuntu. Almost everything works except I can not get my USR external modem to work thus I could not make any updates. I have tried reading though the threads and tried everything suggested. The modem dials the ISP, does a handshake (so it seems) but after a few seconds it disconnects. Have tried vdial and still could not get it to work. Anyone out there who can give me a step-by-step instructions on how to make it work. The modem works on Windows and is connected to a serial port of the pc ttyS0 its only the way I guess the modem communicates with the ISP is where I am having problems. Thanks for reading and hope someone out there can help.

---

### Post by deadgobby on 2006-08-26
YOu have what is called a hardware modem. According to Ubie wiki.
Hardware modems. I do not know if any one has given you Ubie's Wiki site. But this is what a gather up.... The below is taken from Ubuntu Wiki Site.

Hardware modems don't need a special driver. If your modem connects to the serial port and you know the COM port, the device name is /dev/ttySx, where x is one less than the COM port number. For example, if your modem is on COM2, the device is /dev/ttyS1, or if your modem is on COM1, the device is /dev/ttyS0. You can use this device name to configure your dialup connection.

Note by RaduCristianFotescu: I experienced the problem of a non-detected and not working external hardware serial modem (which made pppconfig, wvdial[conf] and gnome-ppp unuseable) even after issuing a 'sudo ln -s /dev/ttyS0 /dev/modem'. Of course, it previously worked in Slackware and Mepis! Eventually I got it working by making sure the modem was ON and connected to the RS-232 at the time when the kernel was booting! I guess it's smth with the boot scripts... 
 The link is 
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
 Once there, scroll down to hardware modems.

---

### Post by editrix on 2006-08-26
> **araro23 said:**
> Its been three weeks since I have installed Ubuntu. Almost everything works except I can not get my USR external modem to work thus I could not make any updates. I have tried reading though the threads and tried everything suggested. The modem dials the ISP, does a handshake (so it seems) but after a few seconds it disconnects. Have tried vdial and still could not get it to work. Anyone out there who can give me a step-by-step instructions on how to make it work. The modem works on Windows and is connected to a serial port of the pc ttyS0 its only the way I guess the modem communicates with the ISP is where I am having problems. Thanks for reading and hope someone out there can help.

It's not the modem, it's the setup. I know it's got something to do with authentication, as I've read posts about it, but darned if I can find any of them now. I copied the info to my hard drive, though:
> ... but while my modem responds and makes the call, the ppd deamon dies unexpectedly with a log message like the following: 
Oct 12 17:01:17 localhost pppd[8635]: The remote system is required to authenticate itself
Oct 12 17:01:17 localhost pppd[8635]: but I couldn't find any suitable secret (password) for it to use to do so.
Oct 12 17:01:17 localhost pppd[8635]: (None of the available passwords would let it use an IP address.)

Anyone knowing what i should do?

In /etc/ppp/options comment out the line 
auth
that requires remote host to authenticate itself.

Hope this helps.

---

### Post by deadgobby on 2006-08-26
[https://help.ubuntu.com/community/IptablesHowTo?highlight=%28ip%29](https://help.ubuntu.com/community/IptablesHowTo?highlight=%28ip%29)

---

### Post by JimDiabolo on 2006-09-05
I got my US Robotics Courier (external) modem running using [gnome-ppp]("http://packages.ubuntu.com/dapper/net/gnome-ppp").

But somehow it's slower than on windows. Maybe I need to tweak options.

---

