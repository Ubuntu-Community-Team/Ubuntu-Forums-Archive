---
title: "[SOLVED] Irtrans remote control stopped working"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-06-04
Gents,

I have made a mythbox with an origenae X10 case. This cases uses  irtrans to communicate with the remote. To install everything I followed the guide ; [url]http://ubuntuforums.org/showthread.php?t=304807&highlight=irtrans[/url and everything worked correctly for 2 months. Now it stopped working (I think after an update).

Can somebody help me troubleshooting because I have no clue where to start.

What did I already do:
- I downloaded the latest version of the driver and re-compiled it but no luck
- I downloaded the compiled version of the driver and no luck neither.

In both cases I tested it with the following command;```
irserver -codedump -debug_code -loglevel 4 /dev/ttyUSB0
```The result is:```
IRTRans Send Done: 1
Name   : 
Version: D5.03.08
FW SNo : 20897
Capab  : Power On; 
FW Cap : 3964953
USB SNo: 
Node   : /dev/ttyUSB0

IRServer Version 5.8.04
```But nothing appears on the screen when I press a button on my remote. Please help me as my mythbox is useless without a remote and I really like my box ;).

---

### Post by El_Matthews on 2007-06-05
This thread can be closed, it works again even if I have no clue on how I made it work again.

---

