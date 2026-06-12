---
title: "Linux fails to install, numerous methods tried"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by c0njur on 2006-06-05
I'm sorry if I'm listing too many problems in one thread, but I don't know where to go from here.

I've tried installing Dapper from the Live CD but it keeps freezing while copying files, usually between 60 and 70%, but not always. The CD-ROM drive just stops spinning and then the HDD light stops blinking. I've let it run for hours and nothing changes, I've always re-downloaded and burned the ISO file, but the same thing happens.

Then I tried to install Breezy, thinking I could upgrade to Dapper. However the installer refused to install the kernel (i386 file?), so I gave up on that.

Next I tried to install using the Dapper alernate CD. At first it appeared to be working as planned as it managed to copy files, install base, and begin to install programs. But when it reaches 58% (preparing to configure ubuntu-desktop) the screen goes blank and nothing happens, as had been described in [this thread]("http://ubuntuforums.org/showthread.php?t=189233").

So at this point I'm not sure what to do. I've spent 3 days trying to install some form of Ubuntu on my system and instead of gaining an operating system, I've lost one (the Gnome partition editor decided to erase my entire Windows partition).

Does anybody have any suggestions? 

_System Specs:_
Sony Vaio Laptop
Centrino CPU
Intel Graphics
Intel 2200b/g wifi

---

### Post by aysiu on 2006-06-05
It doesn't matter how many times you burn an ISO. If it's corrupt, it'll just be corrupt multiple times.

Did you do a checksum? Because these freezes during installation sound to me as if you have corrupt CD images.

For more details: [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

[http://ubuntuguide.org/#checkmd5](http://ubuntuguide.org/#checkmd5)

---

### Post by yteh on 2006-06-06
Not sure whether this is the same as my experience but here goes (it might help you).....

I installed Dapper using the Alternate install CD on my Acer Aspire laptop. The screen did go blank for me as well after seeming to be running just fine (it was ~70% when it happened). The first time this happened, I wasn't too sure what to do so I just shut down the computer and tried again. 

On my second attempt, the screen also went blank. This time I left it alone and about 5-10 minutes later...lo and behold, the cd auto-ejected! Screen was still blank but based on my experience with installs on my mac mini, it would have been at the 'Re-boot' screen. I hit enter, the system re-booted, and I was running Ubuntu!

...And I'm currently a very happy Ubuntu user (regardless of this 'quirk')

---

### Post by nalmeth on 2006-06-06
I had the same experience on a fresh install as yteh did, this was with the flight-7 install CD.

Anyway, follow asyiu's advice with the checksum, but if this still occur's (the dapper experience anyway), you should try to boot into dapper anyway, and run:

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop


In a terminal. In fact, that's likely all you'll boot into, having failed the ubuntu-desktop installation.

All in all I'd have to agree this sound's like a corrupted image.

---

### Post by c0njur on 2006-06-06
aysiu,

I can't perform those checksum operations as I have no working installed copy of Ubuntu. I'm typing this in the Live version right now and I can't create an ISO to match against the checksum, at least with the commands you gave me. I actually redownloaded the ISO, from a different source, but it still causes the same error.

yteh,

I've tried multiple times with all the CDs I've burned and no amount of time will let it install.


nalmeth,

I entered the commands you gave me that *ubuntu-desktop is already the newest version.* I can boot into the normal GNOME invironment, I just can't install.

---

### Post by ProjectGod on 2006-06-06
just skimming the posts in this thread... so if i appear to be reiterating something or stating the obvious... forgive :mrgreen: i guess you could try the installation on another machine with the same CD (iso image you burned) that'll verify if the image you downloaded is "corrupt"... secondly order one via shipit! its FREE!!!!!!!!!!! and depending which exotic location you reside in... the cd will arrive no later than 6 weeks! mine arrived in 3 weeks! niffty yeah? :D

---

### Post by carlosqueso on 2006-06-06
you could also try the alternate CD, but choose the server install.  That will install fewer packages, which you can then install with apt later.

---

### Post by c0njur on 2006-06-06
Success!

I took carlosqueso's advice and installed the server and used apt-get to install the desktop. The blank screen I encountered before only flashed for a second before continuing on. This methods seem to get around the xserver bug encountered in the normal desktop installation. 

Thanks to all that responded to this thread and gave input; it is greatly appreciated.

---

