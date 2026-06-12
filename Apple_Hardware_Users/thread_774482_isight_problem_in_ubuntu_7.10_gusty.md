---
title: "isight problem in ubuntu 7.10 gusty"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by cyrustajik on 2008-04-29
hello everyone
I just got a C2D intel macbook. Its one of those late 2006 edition. after putting ubuntu 7.10 on it I decided to get the isight working.
for the past 2 days I have tried EVERYTHING i could find n these forums. used the quick install mentioned here , compiled myself, used different extracting methods (which by the extracted the firmware successfully).
But still no luck. the isight doesnt work. Ive tried cheese, ekiga and all the rest.
I keep getting the " Device "/dev/video0" does not exist." error.
I think the problem is that my ubuntu doesnt know anything about my isight. I get the following when I use lsusb command.
Bus 005 Device 003: ID 05ac:8300 Apple Computer, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05ac:8240 Apple Computer, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 05ac:021b Apple Computer, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 003: ID 05ac:8205 Apple Computer, Inc.
Bus 004 Device 001: ID 0000:0000

and in my hardware information window I cant find anything about isight.
it seems so many people have managed to get this working here so I would really appreciate your help.
by the way my kernal is : 2.6.22-14-generic

this is what I get with lsusb:

cyrus@cyrus-Macbook:~$ dmesg | grep -E '(uvcvideo|5\-4)'
[ 5.544000] usb 5-4: new high speed USB device using ehci_hcd and address 3
[ 5.676000] usb 5-4: configuration #1 chosen from 1 choice
[ 21.336000] usbcore: registered new interface driver uvcvideo
as you can see there is no mention of isight what so ever!
I think my macbook doesnt even bothr looking for it!

any ideas ?

thanks in advance for your help
cheers
Cyrus

---

### Post by cyberdork33 on 2008-04-29
> **cyrustajik said:**
> Bus 005 Device 003: ID 05ac:8300 Apple Computer, Inc.
This is your iSight. Before Hardy, there were a lot of issues with getting things working...

In hardy, you do not have to "extract" firmware. just put the file in the /lib/firmware directory. You might be able to compile the latest uvcvideo module from source and use with isight-firmwmare-tools, but I don't know that it has been tried successfully on Gutsy.

Old gutsy guide:
[http://ubuntuforums.org/showthread.php?t=491381](http://ubuntuforums.org/showthread.php?t=491381)

New Hardy Guide:
[http://ubuntuforums.org/showthread.php?t=764616](http://ubuntuforums.org/showthread.php?t=764616)

---

