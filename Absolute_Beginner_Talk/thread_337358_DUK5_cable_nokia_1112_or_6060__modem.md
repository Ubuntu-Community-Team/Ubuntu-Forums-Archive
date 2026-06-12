---
title: "DUK5 cable nokia 1112 or 6060  modem"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by ThirdGear on 2007-01-12
Hi :)
I am trying to use my Nokia 1112 or 6060 phone via a DUK5 cable as a modem to connect to the internet.

lsusb

Bus 001 Device 006: ID 0e55:110b Speed Dragon Multimedia, Ltd
Bus 001 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

The Speed Dragon Multimedia is the DUK5 cable 

sudo wvdialconf /etc/wvdial.conf

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Modem Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Modem Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Modem Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Modem Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Modem Port Scan<*1>: S42  S43  S44  S45  S46  S47
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?

has anyone one got a setup like this working?

Dapper 6.06

Thanks in advance

---

