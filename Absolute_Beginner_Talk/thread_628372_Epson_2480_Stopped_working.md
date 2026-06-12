---
title: "Epson 2480 Stopped working"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by bclinton on 2007-12-01
The scanner worked shortly after I install Ubuntu 7.10 for some reason it does not now.When I start Xsane it sees it and after I hit ok when the scanner is selected I get

Failed to open device snapscan:libusb:005:006': invalid argument

Does anyone have a suggetion?

Followup

Anyone with any suggestions? This is really frustrating. It worked and now it doesn's and I didnt change anything. One other note. When I go into xsane scanner it shows the top option a my hauppage tv card and the second as my epson scanner. When i check the scanner and click ok I immediately get the error I noted above. It has to be a simple fix but I have tried everything and back to square 1.

TIA

---

### Post by cmnorton on 2007-12-01
You may not have changed anything, but have you accepted any updates?

---

### Post by bclinton on 2007-12-01
Yes, whenever the update icon let me know there were updates I installed them. I can see the light on my scanner go dim during the presplash boot up. It is bright green when I unpulg it from my usb port and when I replug it the light goes dim again...

---

### Post by olafant on 2007-12-02
I have also had problems with my 2480 similar to yours.

Try this -it worked first time for me in Gutsy/ Ubuntustudio

1. Download the iscan RPMs for latest gcc from here: 

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

2. Install alien 

3. Use alien/dpkg to convert/install both RPMs

$ sudo alien iscan ***.rpm
$ sudo alien iscan-plugin ***..rpm

4. Install resulting debs 

# dpkg -i iscan *****.deb
# dpkg -i iscan-plugin *****.deb

3. Change /etc/sane.d/dll.conf to contain:

net
epkowa


4. Copy the file into the sane.d/dll.d/ directory

5. Start up /usr/bin/iscan and go


There is an alternative methodology which is to load up the windows firmware file as noted elsewhere in the forum but this is not 100% reliable. 

A less PC method which has also worked for me is to reboot into Windows, kick the scanner into life and then reboot Ubuntu. No idea why.  


Best of

---

### Post by bclinton on 2007-12-06
Man! It worked! Unreal!

Thanks a million!:)

---

