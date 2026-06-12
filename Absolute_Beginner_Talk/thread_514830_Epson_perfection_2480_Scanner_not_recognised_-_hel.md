---
title: "Epson perfection 2480 Scanner not recognised - help please"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-01
Hi guys, I've got xsane sane and the utils installed but no joy...

scanimage -L

philcb@philcb-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0121 [EPSON Scanner]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  scanimage -l
scanimage: no SANE devices found

What do I do now..
Thanks in advance

---

### Post by milosz.galazka on 2007-08-01
Hello,

Did you checked [http://ubuntuforums.org/showthread.php?t=143504]("http://ubuntuforums.org/showthread.php?t=143504")?

---

### Post by philinux on 2007-08-01
ok I got a bit farther,

i get the same no devices found when starting xsane. but when look in Gimp now and try to acuire image I get 
failed to open device snapscan:libusb:001:003 invalid argument. ???

 sudo lsusb produces this response
Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. 
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by milosz.galazka on 2007-08-01
Hello,

You probably already downloaded firmware, copied it and edited config file so maybe it's a permission problem? I can't help you more as don't use scanner at home...

---

### Post by philinux on 2007-08-01
Ah, what firmware ??

---

### Post by philinux on 2007-08-01
Found this helpful page after some digging.
[http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/](http://ubuntufs.wordpress.com/2006/05/26/epson-perfection-2480-scanner/)

now scanner works but only if I sudo xsane or sudo kooka. So I guess its a permission thing. Any ideas

---

### Post by milosz.galazka on 2007-08-01
Hmm, I think that this [http://luc.byhet.free.fr/epson2480/esfw41.bin]("http://luc.byhet.free.fr/epson2480/esfw41.bin")  (look at fifth post in submitted link) and then you should edit config file in /etc/sane.d/ directory adding

firmware /path/to/esfw41.bin

You will find answer by reading first post [here]("http://ubuntuforums.org/showthread.php?t=26911").

Hope this help.

---

### Post by milosz.galazka on 2007-08-01
At first submitted link there is something like this

sudo chmod 777 -R /proc/bus/usb

If you know device name you can change permissions for this device and add this change to devfs configuration so it will be presistent between reboots

---

### Post by philinux on 2007-08-01
Cheers, Yes I had followed all the instruction including editing the config file.

It didnt work straight away for some reason but works now LOL.

now when I type scanimage -L
device `snapscan:libusb:001:003' is a EPSON EPSON Scanner1 flatbed scanner

Scanner is found. Now out of the blue Xsane works ...mmm. not sure what went on but what a bit of a hole this is in ubuntu for a beginner. I'm not a beginner to pc's but this would put a lot of peeps off what do you think?

On closing xsane an error box pops up "Failed to create file: permissions denied".

Do I need to add root to the scanner group?

---

### Post by milosz.galazka on 2007-08-01
Hi,

You don't need to add root to scanner group but probably regular users.

Checking /var/log/messages is a good idea to find problem source also running sane with more verbose output could be helpful.

---

### Post by alienexplorers on 2007-08-01
Perfection 2480 	USB 	0x04b8/0x0121 	Good 	  	SnapScan
(1.4) 	sane-snapscan

---

### Post by milosz.galazka on 2007-08-02
It doesn't say a lot. 

You are the only one person now that could find the answer :)

---

