---
title: "Upgrades always eating up more space..."
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-24
I usually run synaptic once a week to get all the latest and greatest updates. I usually just go into synaptic, reload my repos, and select all updates and install. The problem is, every week i do an upgrade, that updates always say they will need XXXX amount of extra space.


Since ive installed my Xubuntu, using the server build, it took up like 1.2gb. Now after 4 weeks of upgrading on the weekend, once a week, my system is 1.8 gigs. And ive cleaned out all the apt cache too.

What gives? Are my programs getting updates requiring more dependencies? Or are the programs them selves just keep getting bigger and bigger as they are updated?

This is annoying to me because i backup weekly, and each backup is taking more and more space.

---

### Post by zxcv70 on 2006-05-17
I've got the same problem. I delete all apt cache regulary and do'n install useless soft. And I can't stop making Ubuntu bigger and BIGGER .. now it takes **5GB**!!! <OMG> . Even when I delete .. all .deb's there is no extra size left. ehh..](*,)

---

### Post by Mustard on 2006-05-17
Have you analysed where in the filesystem the new space is being taken up?  Could it be that some log files are expanding to cumbersome sizes?

---

### Post by mcduck on 2006-05-18
If you want easy GUI tool to check where the disk space is wasted, install Baobab :)

---

### Post by zxcv70 on 2006-05-18
I found this command :

 $ sudo du -sh /* 

 which is very usefull if you want to check how much space do folders take. I checked log files but they were just 14MB big ;) . I also uninstalled most of O-Office packages leaving only Writer. all this saved over 300 MB. but I think it's the end. 

Do you know and program working in GNOME similar to Clean Sweep for KDE?

Related topics:
[http://www.ubuntuforums.org/showthread.php?t=173713](http://www.ubuntuforums.org/showthread.php?t=173713)
[http://ubuntuforums.org/showthread.php?t=87342&highlight=delete+logs](http://ubuntuforums.org/showthread.php?t=87342&highlight=delete+logs)

---

### Post by bluevoodoo1 on 2006-05-18
I've deleted a lot (if not all) of the foreign language fonts that are included in the 'ubuntu-desktop.' There are almost 200 mb worth if I remember correctly.

---

### Post by Dr. Nick on 2006-05-18
also look into removing orphaned packages
here is a nice gui to do it
[http://www.marzocca.net/linux/gtkorphan.html]("http://www.marzocca.net/linux/gtkorphan.html")

As you update some programs  they change dependencies and you may have old packages installed that arent being used.

Good thread on clearing disk space
[http://ubuntuforums.org/showthread.php?t=172661&highlight=deborphan]("http://ubuntuforums.org/showthread.php?t=172661&highlight=deborphan")
Also a how to
[http://www.ubuntuforums.org/showthread.php?t=140920]("http://www.ubuntuforums.org/showthread.php?t=140920")

---

### Post by it.henrik on 2006-05-18
Im not sure if this is what you have been doing .. otherwise I would recommend 

sudo apt-get clean

---

### Post by zxcv70 on 2006-05-19
:KS Thanx for info .. it really helped me to save over 300 MB! :KS

It was a good idea to become an Ubuntnu citizen ;)

---

