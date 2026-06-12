---
title: "HOW TO: Connecting HUAWEI E220 through TMN Portugal"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by eagleman on 2007-03-23
Hi all.
I only start with linux a month ago.
I would like, if possible, if someone could tell me how I put my modem working in ubuntu.
Thanks.

---

### Post by placidoaps on 2007-06-28
Hi,

Here how I did it (I had to install Caixa Mágica to find out how they did it ***THANKS CaixaMágica***)

You will find the programs you need in the file **programs.tar.gz** attached to this post (bellow)

connect your huawei e220 usb device and wait a few seconds (let's say 10)
run the program (don't forget to make it executable; I assume you are in the same directory as the program huaweiAktBbo-i386.out):
**sudo ./huaweiAktBbo-i386.out**

if you run this command:
**ls /dev/ttyUSB***

you should get:
**/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2**

Then you have to send the PIN to your modem with the program comgt (replace 1234 with your pin) don't use sudo here!
 (don't forget to make it executable ; I assume you are in the same directory as the program comgt)
**echo 1234|./comgt -x -d /dev/ttyUSB0**

open the file /etc/wvdial.conf and put this and only this inside (make a backup of the old one if you want):
#----------------------------------------------------------------
[Dialer Defaults]
Phone = *99#
Username = tmn
Password = tmn
Stupid Mode = 1
Dial Command = ATDT

[Dialer pin]
Init1 = AT+CPIN=0731

[Dialer conta]
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = AT+CMEE=1
ISDN = 0
Modem Type = Analog Modem

[Dialer 2gonly]
Init4 = AT+COPS=0,0,"tmn",0

[Dialer 3gonly]
Init4 = AT+COPS=0,0,"tmn",2

[Dialer ligacao]
Init5 = AT+CGDCONT=1,"IP","internet";

[Dialer 384k]
Init6 = AT+CGEQMIN=1,4,64,384,64,384
Init7 = AT+CGEQREQ=1,4,64,384,64,384

[Dialer 144k]
Init6 = AT+CGEQMIN=1,4,64,144,64,144
Init7 = AT+CGEQREQ=1,4,64,144,64,144

[Dialer 64k]
Init6 = AT+CGEQMIN=1,4,64,64,64,64
Init7 = AT+CGEQREQ=1,4,64,64,64,64
#-------------------------------------------------------

finally run this command;
**sudo /usr/bin/wvdial conta ligacao**

that's it enjoy
I'll try to do something better soon...
like a script that will do the installation directly
and wil turn on the modem as soon as you connect it to the computer (with udev)

---

### Post by placidoaps on 2007-06-29
some more information:

I usually disconnect other networks (right mouse button on the network icon -networkmanager - on the up right corner of the screen- deactivate networks or desactivar redes in portuguese)

when your modem is connecting to the network it will blink until a blue or blue/green light appears without blinking (blue/green light is better as your connection is faster!)

if you cannot access internet

after that check if you have an appropriate DNS server:
run the command:
**cat /etc/resolv.conf**

you should get someting like this (the first IP is your DNS server  (tmn portugal), the second one does not exist)
[B]nameserver 194.65.100.117
nameserver 10.11.12.14[/B]

if not put this line
**nameserver 194.65.100.117**
 in the file
**/etc/resolv.conf**

extra info:
if you want to see your signal quality run (i assume you are in the same directory as the comgt program): 
**./comgt -d /dev/ttyUSB1**

run for help on comgt
./comgt help

---

### Post by brunolabs on 2007-11-04
Thanks! It works!

Do you know if this works with Gutsy (7.10) also?

---

