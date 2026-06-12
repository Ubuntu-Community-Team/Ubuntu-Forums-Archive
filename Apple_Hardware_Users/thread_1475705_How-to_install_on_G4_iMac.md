---
title: "How-to install on G4 iMac"
date: 2010-05-07
forum: Apple Hardware Users
---

### Post by Azyx on 2010-05-07
I run lucid lynx 10.04 beta (live) on an iMac G4 800MHz flat screen.
How do I partionate an 80GB HDD?

In gparted I see 8 very smal partition exept the hfs+ partition. I have thrinked the hfs+ partition and made a 1GB swap, approx 50GB /home and 5GB /. 
When I try to install Ubuntu say I need a new world partion for the boatloader. How fix it? first it say I need 8MB, then 1.8GB!!!!

Is it 'newworld' or 'New world start partition' and what should bee the mount-point?

/Cheers

---

### Post by linuxopjemac on 2010-05-07
You have to create a small partition for the bootloader. 1 Mb is enough for that. 
Here you see an example of that, you should notice that there are no small partitions here as MacOS is not installed:
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

The newworld boot block does not have a mount point.

---

### Post by Azyx on 2010-05-07
> **linuxopjemac said:**
> You have to create a small partition for the bootloader. 1 Mb is enough for that. 
Here you see an example of that, you should notice that there are no small partitions here as MacOS is not installed:
[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

The newworld boot block does not have a mount point.

ahh. yaboot is the name. It seems complicated...to make all this partitions. is it possible to do this from GParted? I could not recall any possibility to make a bootstap-partition, just newworld and New world start partition. I will check more when i coming home to my iMac. /Cheers

---

### Post by Azyx on 2010-05-07
> **Alston.Alfred said:**
> Just a partial answer on opening the cd tray,(maybe). Is there a door that swings down, and allows the cd tray to slide out? If there is it may be 'hiding' the area where the paper clip goes into. Probably on the left side, right under the cd tray, about an inch over from the left.
 
I'm not really understand your answer but...Yes. I had problems to find how to open cd-tray in OS-X (Open an empty cd/dvd-tray) in this kind of iMac. but I never look after the little hole for paper-clips ;) It is a little door that opend and then the tray going out. I don't have an eject-bottom on my keyboard and the 'command-E' seems not to work every time in OS-X, but If I go into some application, I think it was, iTunes or a burner program, I mananage to open an empty tray' with the 'command+E' :) I don't know how it work on Ubuntu, so maybe in need to find the little hole ;)
 
/Cheers

---

### Post by linuxopjemac on 2010-05-07
Don't pay attention to the bullshit Mr Alston.Alfred spams throughout this forum. He just wants to have his links published.

---

