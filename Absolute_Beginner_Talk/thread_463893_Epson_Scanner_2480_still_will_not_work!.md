---
title: "Epson Scanner 2480 still will not work!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by christopherberry11 on 2007-06-04
`snapscan:libusb:002:003' is a EPSON EPSON Scanner1 flatbed scanner' - here is the message I get when I 'scanimage -L'
But when I go to Gimp and try to acquire I get 'error during device I/O'
I am in 7.04 BUT I could not get the dashed thing to work in Edgy either!
Is there anyone out there who has been successful in 7.04 and can lay out the procedure for installation in SIMPLE NON-GEEK terms?
It seems such a shame that newbie's are forced to got through such rigmaroles - I am sure that many, at the moment. say a rude word and go back to Windows!!!!!
Thanks,
Grandad C.B.

---

### Post by dstew on 2007-06-04
Please post the output of```
cat /etc/sane.d/epson.conf
```

---

### Post by christopherberry11 on 2007-06-04
christopher@alfred:~$ sudo cat /etc/sane.d/epson.conf
Password:
# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
Here is the response I received!

#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
# usb 0x4b8 0x110
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0
christopher@alfred:~$ 

Any ideas,
Sincerely,
CB

---

### Post by dstew on 2007-06-05
It looks like your scanner may have the name scanner1. If your software is looking for scanner0, it might be failing. We need to make sure of the device name of your scanner. In a terminal, enter this command:```
    scanimage -f " scanner number %i device %d is a %t, model %m, produced by %v "
```This will give, hopefully, the complete device name. We need this to make sure that it is set up properly. Is the scanner connected to a USB port, a parallel port or a SCSI port?

---

### Post by mooscape on 2007-07-30
Same problem with EPSON PERFECTION 2480 PHOTO:   

> mooscape@mooscape-laptop:~$ scanimage -f " scanner number %i device %d is a %t, model %m, produced by %v "
 scanner number 0 device snapscan:libusb:005:021 is a flatbed scanner, model EPSON Scanner1, produced by EPSON mooscape@mooscape-laptop:~$ 

Any ideas?   

Further: I get the same printout to    > cat /etc/sane.d/epson.conf as the above.

AND:  The scanner works in xsane for exactly one scan, then the arm won't return more than half way. To get it back in position I have to plug and unplug the usb cable to get it to move about an inch each time.

---

### Post by mooscape on 2007-07-30
I  read in the results of cat /etc/sane.d that I should :  

>  # And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

BUT there is no such file.   On  the other hand, in /dev/bus/usb :

> T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 25 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=04b8 ProdID=0121 Rev= 1.10
S:  Manufacturer=EPSON
S:  Product=EPSON Scanner
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=4096ms


Is this of value?

---

### Post by yorkie on 2007-07-30
two previous threads that may shed some light on this subject

[http://www.bl0g.co.uk/070209/Ubuntu_on_the_Desktop_not_ready/](http://www.bl0g.co.uk/070209/Ubuntu_on_the_Desktop_not_ready/)

[http://ubuntuforums.org/showthread.php?t=143504](http://ubuntuforums.org/showthread.php?t=143504)

Hope this helps

---

### Post by mooscape on 2007-07-30
Thanks Yorkie,

 I tried that way, but no luck.  The odd thing is, I used it for a year on Dapper. It worked perfectly and was used daily. Then I decided to upgrade to Ubuntu Studio and the problems started.  I can scan but once only, then I get the error > Failed to scan, device busy  and the scan arm has not returned to the start position.  I can only move the arm back by plugging the usb in and out several times....!

---

### Post by noynac on 2007-07-30
> **mooscape said:**
> Thanks Yorkie,

 I tried that way, but no luck.  The odd thing is, I used it for a year on Dapper. It worked perfectly and was used daily. Then I decided to upgrade to Ubuntu Studio and the problems started.  I can scan but once only, then I get the error   and the scan arm has not returned to the start position.  I can only move the arm back by plugging the usb in and out several times....!

That sounds like the usb-suspend bug. I thought it had been fixed but perhaps not.

Do a search of the ubuntu forums on the words, usb suspend, and separately on the word, scanbutton, which is a workaround.

One thread on this topic is:

[http://tinyurl.com/2a5op4](http://tinyurl.com/2a5op4)

BTW, I have an Epson 3490 scanner that worked fine in Edgy but acted exactly like yours under Feisty. The scanbutton (scanbuttond actually) workaround cured the problem.

---

### Post by mooscape on 2007-07-30
Noynac

re: SCANBUTTOND     This works!!! 

You are hereby promoted to the Pantheon of Linux Gods!

---

