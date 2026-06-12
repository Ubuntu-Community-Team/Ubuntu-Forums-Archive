---
title: "[SOLVED] Edgy Eft and Packet writing"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-10-07
Hi,
I wonder if "packet writing" can be enabled in the new Ubuntu 6.10 'Edgy EFT' release 
as it was described [here]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+writing+without+tears") for Ubuntu 6.06 (Dapper Drake)?

---

### Post by Cariboo1938 on 2006-11-04
> **Cariboo1938 said:**
> Hi,
I wonder if "packet writing" can be enabled in the new Ubuntu 6.10 'Edgy EFT' release 
as it was described [here]("http://www.ubuntuforums.org/showthread.php?t=129093&highlight=Packet+writing+without+tears") for Ubuntu 6.06 (Dapper Drake)?Talking to myself...yes it can. 
I installed it and it works well, except I can't mount the drive permanently. 
If I try to open I get the Error message;(see Attachment *1)
If I mount it with:```
sudo mount -t udf -o utf8,noatime /dev/pktcdvd/0 /media/cdwriter
```it works; (see Attachment *2)
[COLOR="Blue"]What do I have to do to be able to open it without first mounting the drive manually?[/COLOR]

---

### Post by Cariboo1938 on 2006-11-18
!!!!!!!!Still working on Packet writing: Now I try to use a DVD!!!!!!!!> **dradul said:**
> **Packet Writing Without Tears: How to use Rewritable Optical Media in Ubuntu**
*Pedro A. López-Valencia*
*[SIZE="1"]python -c 'print "cGFsb3BlenZAZ21haWwuY29t".decode("base64")'[/SIZE]*

**Formatting your CD-RW**
Before you start formatting your CD, make sure that you have DMA active in your burner...
 
Take a CD-RW [COLOR="Magenta"]or DVD-/+RW [/COLOR]and format it:
```
sudo cdrwtool -t 4 -d /dev/hdd -q
```
Go brew a carafe of cofee  and grab some muffins. Drink slowly...  
Error message when I try to format the DVD:
> root@BitByter:~# sudo cdrwtool -t 4 -d /dev/hdb -q
setting speed to 4
using device /dev/hdb
1088KB internal buffer
setting write speed to 4x
Settings for /dev/hdb:
        Fixed packets, size 32
        Mode-2 disc

I'm going to do a quick setup of /dev/hdb. The disc is going to be blanked and formatted with one big track. All data on the device will be lost!! Press CTRL-C to cancel now.
ENTER to continue.

Initiating quick disc blank
Disc capacity is 3524075584 blocks (2753183872KB/6882960MB)
Formatting track
[COLOR="Red"]wait_cmd: Input/output error
Command failed: 04 17 00 00 00 00 00 00 00 00 00 00 - sense 00.24.00
format disc: Illegal seek[/COLOR]
root@BitByter:~# My DVD drive is a LG GSA-4160B which, the Device Manager tells me, is found as HL-DT-ST DVDRAM GSA-4160B.
[COLOR="Blue"]Is this a hardware problem or do I have to use a different command to format the DVD?[/COLOR]

---

### Post by Cariboo1938 on 2008-01-05
I never got it working properly, and I gave up to try....
There is rumor out that K3B will sometime have it integrated....
I better wait for [**_[SIZE="3"]S.Trueg's[/SIZE]_**]("http://behindkde.org/people/trueg/") solution

---

