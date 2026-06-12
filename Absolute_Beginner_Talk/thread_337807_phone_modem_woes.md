---
title: "phone modem woes"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by David J Bush on 2007-01-13
[FONT=Georgia][SIZE=3][COLOR=Indigo]I have a USB Best Data "Smart One" 56K external phone modem.
The largest chip  on the board  says:

CONEXANT
SMARTV.90+
CX81801-34
E945703.1
0312       MEXICO

A smaller chip says:

CX11253-11P
K19714.2
0310        KOREA

On the PC board it says:

BEST DATA PRODUCTS  INC.
WK294VO
0308
56USB92
P/N 10194
COPYRIGHT  2003
               0303

The USB ID of this device is [/COLOR][/SIZE][/FONT][FONT=Georgia][SIZE=3][COLOR=Indigo]0572:1280

On the "HSF Linux" mailing list I eventually got this reply:

[/COLOR][/SIZE][/FONT]> [COLOR=DarkRed]Hi,

according to the Windows XP driver you have provided, it seems that  your 
modem is based on a ACF Conexant chipset. We do not provide a driver  for 
such modems yet.

It is quite possible that it will work under  Linux without a 3rd party 
driver with the 'usbserial' or 'cdcacm' modules.  You should contact the 
vendor of your modem for more information on Linux  support.[/COLOR][FONT=Georgia][SIZE=3][COLOR=Indigo]I could continue to try to find a driver that works, OR I could buy a new modem. It could be RS-232; I hear those are more likely to run hassle-free. But here's the catch: It also has to run under Windows 98SE. I am using two computers with a KVM switch.

Any recommendations or advice would be appreciated.

David
[/COLOR][/SIZE][/FONT]

---

### Post by oilchangeguy on 2007-01-13
is highspeed available in your area? most phone companies basic dsl packages start around 25-30.00 which is probably near what you're paying for dial-up. there are modems that will work with linux (most won't). and most nic cards work right out of the box with linux.

---

### Post by David J Bush on 2007-01-13
[FONT=Georgia][SIZE=3][COLOR=Indigo]High speed is not an option. I pay $9.95 for dialup.[/COLOR][/SIZE][/FONT]

---

### Post by oilchangeguy on 2007-01-13
ooooh, netzero, or people pc???????? anyway google your modem's model number to see if it works in linux. or replace the modem. if you're using a soft modem (software, requires a cd to load drivers) you need a hard modem (hardware no driver cd needed). locate a serial modem, this hooks up to your computers serial port, and from what i've read should work out of the box.

---

