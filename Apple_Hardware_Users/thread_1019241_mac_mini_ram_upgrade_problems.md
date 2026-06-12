---
title: "mac mini ram upgrade problems"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by campee on 2008-12-22
I have a mac mini 2.0 GHz intel core duo mac mini. I used to have 2 512MB memory modules installed for a total of 1GB. I wanted to go up to 3GB (which I have read is the maximum) so I bought 2 x 2GB memory modules. I have installed both of them and booted the system and ran "free -m" from the command line to see how much RAM I have now. It still says I only have 1GB! I ran dmidecode to see what it thinks it has and got the following:

Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x0120, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x011F
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK 0
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Unknown
	Part Number: Not Specified

Handle 0x0121, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x011F
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK 1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: 0xCE00000000000000
	Serial Number: 0x9353074D
	Asset Tag: Unknown
	Part Number: 0x4D342037305432383634515A332D43463720

I tried removing one of the 2GB sticks and it still comes back with the same thing. Does anyone know what I can do to get these working? Thanks.

---

### Post by mkvnmtr on 2008-12-23
One time I put a stick of ram in and it didn't show. I put it a couple of mor times and sent itn back.  The guy tested it and said it was good. I put it in again and it still didn't show . The last time I put it in I finally got it seated correctly and it showed and has been working for two years. Maybe yoou should check it real good.

---

### Post by cyberdork33 on 2008-12-24
Looks like Dimm0 is not seated all the way, and the other card is only 1GB. You might want to make sure you got the right sticks of RAM.

Also, Macs can be particular about RAM. If you just bought some inexpensive RAM, it is likely that the Mac will not like it.

---

