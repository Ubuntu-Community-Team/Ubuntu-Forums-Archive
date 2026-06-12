---
title: "installer that works is there such a thing  ????????"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by mnzt42yd on 2006-05-21
is there such a thing ?????????? iv downloaded 3-4 times first was 2,83 gb  5.1 full.iso i asumed was told must have been corruped  as was giving wrong letters during install 

then advised to get beta downloaded flight5 installer failed kept crashing about 50% soon afterwards flight 6 came out  was told to use this as can do install form the live cd .. same keeps crashing finally flight7 states installer crash fixed  ..... sorry naw and the real sore bit is its  such a nice o.s when its running on the live cd

---

### Post by aysiu on 2006-05-21
Have you checked that the ISO wasn't corrupted?

[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by jazzmuzik on 2006-05-21
I think your downloads have been corrupted. It is best to use a bittorrent client to download the Ubuntu iso files. Bittorrent checks each packet for accuracy and can resume downloads if it gets interrupted. wget is another good choice for downloading. It is a command line util. Once you get the download it is pretty essential that you run the md5sum check on the iso to make sure it is bit for bit an exact copy. Only then should you burn the iso in "image" or "iso" mode, NOT data mode.

---

### Post by mnzt42yd on 2006-05-22
first this is a clean install no other o/s on the system

ok followed your instructions  ... from the web link downloaded with bearshare

checked the cd .. ok  no errors ... went into bios of pc reset everything to default ... loaded the live cd  clicked the install  used defaults  all way through except the location  (chose one closest to me  (uk)) bla bla bla .... started to install now its hanging at about 70% lmao .... ok all joking aside 

whats my other options to TRY notice i say TRY, lol and get it to install ????  or is it give up time iv seen theres a text based install is it much harder or is there a web link for how to do that anyone can give me to get this up and running

---

### Post by aysiu on 2006-05-22
The text-based installer isn't difficult. You just can't use your mouse with it.

To see what it's like, go here:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by _simon_ on 2006-05-22
Do I gather you're in the UK? I can send you an official Ubuntu breezy CD if you want? At least you'll know you've got an OK copy. 

Just drop me a pm with your address and which version you want. I've got 64bit, 32bit and Mac ones.

The offer is there :)

---

### Post by Klaidas on 2006-05-22
maybe you just burn CDs at hight speed? That's how they might corrupt.
Use low speed, like 4x :)

---

### Post by dmizer on 2006-05-22
you keep saying that the downloads are corrupted.

are you downloading the iso in windows?  if so, try going to [http://housecall.trendmicro.com](http://housecall.trendmicro.com) ... it could be that you have a virus or malware infection that's compormising your download.

also slower burn rates help significantly.

---

### Post by dmizer on 2006-05-22
[QUOTE=mnzt42yd]checked the cd .. ok  no errors ... went into bios of pc reset everything to default ... loaded the live cd  clicked the install  used defaults  all way through except the location  (chose one closest to me  (uk)) bla bla bla .... started to install now its hanging at about 70% lmao .... ok all joking aside[/QUOTE]
actually ... that sounds like you have a good cd now.

try reinstalling and before you hit enter to install (when it says "boot"), type the following:
```
linux noapic
```
then i suspect you won't hang at 70%

---

### Post by mnzt42yd on 2006-05-22
all advice has been taken on board but  iv already done all this checked for virus other visitors :-#  on system  everyhting on the main pc is clean which surprised me  lol as far as burning the cds all cds were burned at x4 speed no faster  i might be new to this o/s but iv a little bit of experience with windows  :-\"   so its really frustrating when something so simple dosent work ](*,) but i will try the command at boot time

---

