---
title: "Catch 22"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ddover on 2007-03-30
I just did a fresh install from a ubuntu 6.06.1 LTS cd that was mailed to me from the ubuntu website. Everything is great except that it did not detect my Attansic L1 intergrated network card. Searching around the forums i found [http://ubuntuforums.org/showthread.php?t=292838](http://ubuntuforums.org/showthread.php?t=292838) which explains how to install the drivers from the my motherboards cd. Seems simple enough. Problem is I can't perform the "sudo make" command. It always returns "sudo: make: command not found". Past experince tells me that this is because I don't have the build essentials development tools installed. Unfortnetly I can't figure out how to install them without access to the internet. (Obviously I have another computer that I am accessing the internet with. a mac)

Ubuntu 6.06.1
ASUS mobo
Attansic L1 Gigaethernet

Any advice would be extremely appreciated.

Danny

---

### Post by vote_quimby on 2007-03-30
using the mac you could go to packages.ubuntu.com and download the build essentials .deb for 6.06 dapper (make sure you have all dependencies). Then you could transfer them using usb to your ubuntu machine and right click 'install'

---

### Post by zvacet on 2007-03-30
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Taype essential I you will be able to download the package.Save it to the disc burn and than put in your comp without net.

---

### Post by ddover on 2007-03-30
ok did what you said and it got a error 
"dependency is not satifiable, libc6-dev|libc-dev"

Thanks

---

### Post by zvacet on 2007-03-30
O.K. My mistake.I´m sure that you  sow red signed packages.That are dependencies wich you need too.Sorry for incomplete information.

---

