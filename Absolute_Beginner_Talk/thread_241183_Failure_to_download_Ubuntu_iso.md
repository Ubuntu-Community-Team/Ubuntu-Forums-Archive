---
title: "Failure to download Ubuntu iso"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-22
I am building my own machine which I plan to run a AMD64 bit chipset. I went here-> [http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/) and tried downloading the appropriate desktop iso for the AMD64 but the download always fails to continue after about 120MB of file transfer (or near). I have tried using both FF and Dillo with the same ending results. I have a high-speed internet connection directly to my modem (for an attempt to troubleshoot the problem) but still no luck. Any ideas as to why this cuts off?

Here is the log I got from Dillo

--20:17:11--  [http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-amd64.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-amd64.iso)
           => `-'
Resolving ubuntu-releases.cs.umn.edu... 128.101.240.211
Connecting to ubuntu-releases.cs.umn.edu|128.101.240.211|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 733,751,296 (700M) [application/x-iso9660-image]


23% [=======>                             ] 172,048,304   --.--K/s  ETA 2:18:57

Right about there it will lock up and the file transfer rate will go blank.

---

### Post by GeekSpeek'r on 2006-08-22
try a different mirror:

[http://ubuntu.cs.utah.edu/releases/6.06/](http://ubuntu.cs.utah.edu/releases/6.06/)
[http://mirrors.cat.pdx.edu/ubuntu-iso/6.06/](http://mirrors.cat.pdx.edu/ubuntu-iso/6.06/)
[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/)
[http://se.releases.ubuntu.com/6.06/](http://se.releases.ubuntu.com/6.06/)

etc

---

