---
title: "Bitpim with a dead Motorola V3c"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-22
Hey all, 

my roomate has a dead V3c.  It will not power on, but is recognized by my computer.  I am using Bitpim to attempt to open up the phone and grab his contacts... however I can not

I am running Bitpim as root, in order to have access to all the USB interfaces...

Is there anyway to access this phone?

Attached are screenshots of the phone setup and error messages

---

### Post by warrior24 on 2008-01-22
I use moto4lin

---

### Post by warrior24 on 2008-01-22
[http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin](http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin)

---

### Post by kernel tom on 2008-01-22
I get errors with that too... 

how are you supposed to detect ur phone with moto4lin?

---

### Post by kernel tom on 2008-01-22
> **warrior24 said:**
> [http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin](http://ubuntuforums.org/showthread.php?t=56253&highlight=moto4lin)

followed that step by step

[info] Phone is unpluged. Please connect it
[info] Phone pluged as P2K
Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Phone is busy. Please try later
[error] Unable to get file count
[error] Phone is busy. Please try later
[error] Unable to get drive name
Try to reboot
[error] Unable to reboot
Try to disconnect
[info] Phone disconnected
Try to connect
[info] Phone connected as P2K
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Unable to get drive name
Try to disconnect
[info] Phone disconnected
[info] Switching device /dev/ttyACM0 to P2K mode...
[info] AT E0 answer: OK 
[debug] nread=-1, errno=11
Searching for 
[error] Bad request or no files found
Searching for 
[error] Bad request or no files found
Try to connect
[info] Phone connected as P2K
[error] Phone is busy. Please try later
[error] Unable to get phone model
[error] Unable to get drive name
[error] Phone is busy. Please try later
[error] Unable to get file count
[error] Unable to get drive name

and thats my output

---

### Post by zabien1970 on 2008-01-22
It looks like you're using an older version of bitpim, try upgrading

---

### Post by warrior24 on 2008-01-22
type this in console 

sudo moto4lin

---

### Post by kernel tom on 2008-01-22
> **warrior24 said:**
> type this in console 

sudo moto4lin

thats what i ran when i received that output... could the phone just be incapable of communicating with the computer?

---

### Post by warrior24 on 2008-01-22
does a dialog box open at all when u run that command ?

Here is what mine looks like

---

### Post by kernel tom on 2008-01-22
yeah, i just when i search i get bad request, no files found

---

### Post by warrior24 on 2008-01-22
click on the preferences tab then click on update list.
Find where it says Motorola click on it and Set it as a p2k device

---

### Post by kernel tom on 2008-01-22
did that too.. i get the following

[info] Phone connected as P2K
[error] Phone is busy. Please try later
[error] Unable to get phone model
[error] Unable to get drive name
[error] Unable to get file count
[error] Phone is busy. Please try later
[error] Phone is busy. Please try later
[error] Phone is busy. Please try later
[error] Unable to get drive name
Searching for /
[error] Bad request or no files found

---

### Post by warrior24 on 2008-01-22
post a screen shot of the moto4lin application open on preferences tab

---

### Post by kernel tom on 2008-01-22
> **warrior24 said:**
> post a screen shot of the moto4lin application open on preferences tab

here it is

Yes i realize it says disconnected... when i connect it i get the errors stated before

---

### Post by warrior24 on 2008-01-22
[http://moto4lin.sourceforge.net/wiki/Razr_V3c](http://moto4lin.sourceforge.net/wiki/Razr_V3c)

Looks like it wont work with moto4lin
try bitpim never used it : )
[http://www.bitpim.org/](http://www.bitpim.org/)

---

### Post by kernel tom on 2008-01-22
bitpim can't find the device... 

i'm begining to loose hope

---

### Post by warrior24 on 2008-01-22
what phone company is it

---

### Post by kernel tom on 2008-01-22
its a Verizon Motorola V3c.... it's not a Verizon issue tho... I've been able to get into my Verizon phone no problem

---

### Post by warrior24 on 2008-01-22
type bitpim in console then when window opens click on the icon with the phone and magnifying glass then click yes  click on phone wizard and select your carrier.

---

### Post by kernel tom on 2008-01-22
Thank you for your responses, but I have done that time and time again.

Is it just not possible to get into a dead phone?

---

### Post by Paul86fxr on 2008-02-06
I cant get it to work with my Alltel v3c, it will not switch to p2k, keeps saying unable to connect please check preferences, it sees the phone, Vendor and product are correct, any ideas while you are at it?

---

