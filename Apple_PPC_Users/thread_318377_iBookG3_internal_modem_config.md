---
title: "iBookG3 internal modem config"
date: 2006-12-13
forum: Apple PPC Users
---

### Post by oaklad on 2006-12-13
iBook G3 dual 500mhz

At Linux World in San Francisco this summer (2006) a Linux guru was able to configure my internal 56k modem.

I recently installed Xubuntu 6.1. My Airport card (not extreem) worked and I was able to connect and install the updates. I also installed KPPP to dial my modem.

After I configured my ISP and moidem at ttySO when I try to connect I see the following:
Looking for modem
Modem rewady
Initializing modem

I can proceed no further.

Here is what wvDial conf shows:
gerald@ubuntu:~$ wvdialconf /dev/null
Editing `/dev/null'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot set information for serial port.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Anyone have any suggestions. As I have a dual boot to OS X I am still able to use my modem.

---

