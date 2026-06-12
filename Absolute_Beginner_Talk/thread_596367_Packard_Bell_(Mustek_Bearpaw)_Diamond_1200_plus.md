---
title: "Packard Bell (Mustek Bearpaw?) Diamond 1200 plus"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by TimGS on 2007-10-29
I have Ubuntu 7.10 - clean install as its my first install of any Linux distro.

When starting Xsane I first got the following message popping up:

Failed to open device
gt68xx:libusb:005:002
Invalid Argument

After rebooting I got virtually the same message but with 004 instead of 005. I get the impression that this is just a USB port number that can and does change (?).

scanimage -L produces
device `gt68xx:libusb:004:002' is a Mustek Bearpaw 1200 CU Plus flatbed scanner

Help!:confused:

Thanks in advance
--Tim.

---

### Post by TimGS on 2007-11-05
Tried 'Scanner Utility' also, which popped up with a message saying that the scanner backend came up with the error 'Invalid Argument'

-- Tim.

---

### Post by afeasfaerw23231233 on 2008-01-12
i have this problem too [http://ubuntuforums.org/showthread.php?p=4119582#post4119582](http://ubuntuforums.org/showthread.php?p=4119582#post4119582)
i newly connect my bearpaw 1200 cu scanner and click applications - graphics - xsane and this appear "failed to open device 'gt68xx:libusb:001:005" invalid argument. and here is what scanimage -L shows: device `gt68xx:libusb:001:005' is a Mustek BearPaw 1200 CU flatbed scanner. 
it seems that those unsolved posts remain unsolved forever no matter how hard you bump it. but those posts which can be solved by one reply would keep getting a bunch of other similar replies. bump

---

### Post by afeasfaerw23231233 on 2008-01-12
i get my problem solved. i type scanimage in terminal and it said /usr/share/sane/gt68xx/ps1fw.usb file not found [not PS1Dfw.usb] so i go to this site [http://meier-geinitz.de/sane/gt68xx-backend/](http://meier-geinitz.de/sane/gt68xx-backend/) again and download ps1fw.usb, copy it to /usr/share/sane/gt68xx/ folder, then sudo chmod a+r /usr/share/sane/gt68xx/ps1fw.usb. and xsane work fine! but according to that site only 8 and 12-bit work in this driver ps1fw.usb, but all resolutions work in PS1Dfw.usb .[isn't my scanner capable for 48-bit?] but anyway 8-bit colour is enough for me now. anybody sees this help can download the driver from that site or here. [ps1fw.usb works in my case] see my post at this link [http://ubuntuforums.org/showthread.php?p=4120037#post4120037](http://ubuntuforums.org/showthread.php?p=4120037#post4120037)

---

### Post by TimGS on 2008-01-12
Thanks for the info. Its working now!

In my case it was PS1Gfw.usb that was required. Typing scanimage tells you which file is needed.

cheers,
-- Tim.

---

### Post by sdowney717 on 2008-01-16
scanimage -L
device `gt68xx:libusb:002:002' is a Mustek Bearpaw 1200 CU Plus flatbed scanner

when it scans I get a blank image with a single line running down the page

I did the chmod thing and get a better picture but it is illegible

---

