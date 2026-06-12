---
title: "broadcom problems with feisty"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-05-06
I have the infamous broadcom 4306, and I finally had it working on dapper, by blindly following howto's in this forum.  I just upgraded to feisty and it doesn't work.  I tried the how-to located at:

[http://ubuntuforums.org/showthread.php?t=434946&highlight=broadcom+feisty](http://ubuntuforums.org/showthread.php?t=434946&highlight=broadcom+feisty)


I get hung up on step 4 and get the following error:

jeff@jeff-laptop:~/bcm43xx-softmac-sa$ make
make -C /lib/modules/2.6.20-15-386/build M=/home/jeff/bcm43xx-softmac-sa modules
make: *** /lib/modules/2.6.20-15-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2


I don't know what I'm supposed to do.  Any ideas?  I'm a total newbie, too so please reply in "linux for dummies" language.

thanks

---

### Post by iamtherealwoody on 2007-05-06
I have the broadcom 4306 too with a gateway computer.  This is the best and easiest way ive found to date. give it a try,
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+ndiswrapper]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306+ndiswrapper")
It doesnt constantly loose connection like the cutter.

---

### Post by divague on 2007-05-06
I have the same broadcom 4306, mine is working fine. I installed bcm43XX-fwcutter and it automatically installed the drivers, the first times the network manager showed a message saying that it connected to a network, but the internnet wasn't working, so i opened a terminal and put:

$iwlist eth1 scan

this showed me the signals that the card was getting then

$sudo iwconfig eth1 essid "*the-name-of-the-cell*" channel *the-number-of-the-channel*

then:

$sudo dhclient eth1

and it connected and the internet was working.

hope this helps

---

### Post by jctaft on 2007-05-06
I hesitate to completely scrap the cutter and go with ndiswrapper just because every time I try too many how-to's (most of which I don't get through because I get an error halfway through that I don't know how to get past) My computer won't work at all, and I try and post on here for help, but then I can never remember all the different things I've tried, and I always just had to re-install Ubuntu after awhile.  I'd prefer not to go down that road if possible.  Any ideas on how to finish installing the cutter?


j

---

### Post by jctaft on 2007-05-10
On woody's advice I installed ndiswrapper (actually I friend who is very competent with ubuntu did it for me and roughly described what he was doing.)  He did it, however, in a place where I could not connect to a wireless network, but all indications seemed like it worked.  Once I was home, I tried to get on and it found my wireless network, but would not connect, it couldn't get an IP address.  I looked in the network tools and network manager and whatnot, but could not find any thing wrong (althought I don't really know what I'd be looking for) but I didn't think I'd changed anything.  WHen I restarted, however, not only did it not work, but it couldn't even find a wireless device.  In  network tools my wireless card is not listed anymore.  Does anyone know how to fix this?

---

