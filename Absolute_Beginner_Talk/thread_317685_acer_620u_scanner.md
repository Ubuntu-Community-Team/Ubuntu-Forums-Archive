---
title: "acer 620u scanner"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by matchstich on 2006-12-12
not sure if this is the right place for this. but i searched for drivers for a acer 620u flatbed scanner. all i could find are windows drivers.

any one have any idea where i might search for a linux driver?
thanks

---

### Post by matchstich on 2006-12-12
[http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/x692.html](http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/x692.html)

dang it, i found the drivers
thanks

---

### Post by matchstich on 2006-12-17
> **matchstich said:**
> [http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/x692.html](http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/x692.html)

dang it, i found the drivers
thanks

can someone go to  [http://snapscan.sourceforge.net](http://snapscan.sourceforge.net)

and explain that to me in english

or at least point me to a step by step guide for newbies to do this
thanks

---

### Post by matchstich on 2006-12-29
ok, i have been problems with this
[http://www.ubuntuforums.org/showthread.php?t=20453&page=3&highlight=scanners](http://www.ubuntuforums.org/showthread.php?t=20453&page=3&highlight=scanners)

i went to that thread and tried to do that and messed up. 

can someone explain the 5th line exactly?  i reinstalled the os again , because i couldn't finger out how to correct my mistook.

is there a step by step guide for this?
thanks

---

### Post by matchstich on 2007-01-07
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/U96V057.bin

# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
 #/dev/usb/scanner0 bus=usb
usb 0x04a5 0x2060

# For SCSI scanners specify the generic device, e.g. /dev/sg0 on Linux.
# /dev/sg0

ok, i got this far. did i do this right?

cept when i go to  applications>graphics>xsane image scanner--i get 
failed to open device  snapscan:libusb:004:002  invalid argument

i don't understand. thanks
here are the results from sane-find scanner
# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04a5 [Color], product=0x2060 [ FlatbedScanner 13]) at libusb:004:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as

---

### Post by dbmk on 2007-01-22
I have an Acer 620U and ubuntu 6.06LTS
And I have got it to working.

cat /proc/bus/usb/devices
has this line in it (with many others)
P:  Vendor=04a5 ProdID=2060 Rev= 1.00


General description of what is needed.
1- using info in table from [http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)
    - (firmware file u96v121.bin is needed)
2- get firmware file. u96v121.bin
    - (extracted from driver downloaded from benq site)
3- install firmware file in ubuntu standard place
    - /usr/share/sane/snapscan/u96v121.bin
4 - edit just one line in snapscan config file to u96v121.bin firmware
    - /etc/sane.d/snapscan.conf

And now "Applications->Graphics->XSane Image Scanner" WORKS :-)



Detailed Version of above General description
Note Linux file names are case sensitive.

download the windows driver zip file mirascanv403u10_bqa.zip

and in a terminal

expand the zip file
"unzip mirascanv403u10_bqa.zip"

change directory to the firmware directory
"cd MiraScan\ v4.03u10_BQA/BIN/"

as root user (sudo) make directory to put firmware in
"sudo mkdir /usr/share/sane/snapscan"

as root user (sudo) copy firmware file to that directory
"sudo cp u96v121.bin /usr/share/sane/snapscan/"

as root user (sudo) use gedit program to edit snapscan.conf file
"sudo gedit /etc/sane.d/snapscan.conf"
and change firmware line to location of file
firmware /usr/share/sane/snapscan/u96v121.bin



BenQ link for Acer 620U driver download
[http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D](http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D)

Note for matchstich
It looks like you have edited more than just the firmware line in /etc/sane.d/snapscan.conf
(remove the line "usb 0x04a5 0x2060" )
and in my case a different firmware file worked.
to delete (remove) your current firmware file
as root (sudo) remove the file
sudo rm /usr/share/sane/snapscan/U96V057.bin

NOTE Linux file names are case sensitive

---

### Post by seenu on 2007-10-19
HI dbmk,

i am a ubuntu beginner from germany and was close to a nervous breakdown because I couldt find a way how to run my prisa 620u. Most of the informations I found was not understandable for beginners until I found your entry. It works!!! Thanks a lot!!!

---

