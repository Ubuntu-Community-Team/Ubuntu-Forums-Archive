---
title: "Is 2 hour install normal?"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by thedon808 on 2005-05-24
I installed Ubuntu the other day and it took around 2 hours! My system is a PII 350Mhz 128ram so its not fast. I previously had fedora installed on it but it just took up too much space nearly 3gb, and that only took 45mins - 1hour to install. So you can see my concern. I haven’t really used it much yet as its only for a learning machine hopefully to become my fileserver, and host my website from it. But as i have to install apache, php, and, samba etc I don’t really want to sit through another long and drawn out install process. Cause fedora had them on the install so would it be quicker just to go back to fedora rather than wait around for ubuntu to install the other apps i need? or is there another distro that will install quicker that isn’t as big as fedora you could recommend

---

### Post by ssam on 2005-05-24
sounds a bit slow, but if you only have 128mb ram then there will be a lot more swaping stuff back and forwards than normal. maybe rpm handles low ram situations better, i am not sure.

more ram will make that computer prefectly fast enough

sam

---

### Post by Sam on 2005-05-24
[QUOTE=thedon808]I installed Ubuntu the other day and it took around 2 hours! My system is a PII 350Mhz 128ram so its not fast. I previously had fedora installed on it but it just took up too much space nearly 3gb, and that only took 45mins - 1hour to install. So you can see my concern. I haven’t really used it much yet as its only for a learning machine hopefully to become my fileserver, and host my website from it. But as i have to install apache, php, and, samba etc I don’t really want to sit through another long and drawn out install process. Cause fedora had them on the install so would it be quicker just to go back to fedora rather than wait around for ubuntu to install the other apps i need? or is there another distro that will install quicker that isn’t as big as fedora you could recommend[/QUOTE]
The installation retrieves the updated packages from the web. If you have a slow connection, this can take a long time.

---

### Post by thedon808 on 2005-05-24
As its only an old pc i dont really want to buy more ram for it. my internet connection is 300kbps i wasnt looking closely at the install but i dont think it downloaded much. if my understanding is correct apache, php and samba are all on the cd but not installed. so i can use 'apt get' (what ever its called) to install then from the cd rather than download them from the net?

---

### Post by davide_bruzzone on 2005-05-24
[QUOTE=thedon808]I installed Ubuntu the other day and it took around 2 hours! My system is a PII 350Mhz 128ram so its not fast. I previously had fedora installed on it but it just took up too much space nearly 3gb, and that only took 45mins - 1hour to install. So you can see my concern. I haven’t really used it much yet as its only for a learning machine hopefully to become my fileserver, and host my website from it. But as i have to install apache, php, and, samba etc I don’t really want to sit through another long and drawn out install process. Cause fedora had them on the install so would it be quicker just to go back to fedora rather than wait around for ubuntu to install the other apps i need? or is there another distro that will install quicker that isn’t as big as fedora you could recommend[/QUOTE]

Strange... A recent Fedora Core 3 installation that I performed (which included about 2.5 GB of packages that I needed to install) took a little bit longer than an Ubuntu installation on the same machine (A little over an hour compared to around 45 minutes to an hour for Ubuntu). The machine has a somewhat slow Transmeta Crusoe processor and 175 MB of RAM.

May I ask why you're concerned about how much time it takes to install the distribution rather than (or perhaps as well as) how well the distribution performs once it has been installed? Do you need to install it on many machines? Based on what you said in your post, it doesn't sound like it...

Regarding trying Ubuntu out/learning a little bit about it, you could try using the LiveCD before installing it... However, I don't have any experience with the Ubuntu LiveCD so I couldn't tell you how/where you could permanently save settings, content (such as Web pages) etc. I'm sure someone else on the forums would know though...

Cheers/HTH...

Dave

---

### Post by thedon808 on 2005-05-24
the main reason i was i concerned was if it would take other packages (apache, php and samba) a long time to install also. and really i was just supprised as it isnt a large distro. i did have a look at the live cd, i tried it at work on a celeron 500mhz 128ram it eventually booted but was so slow i couldnt load anything if i was lucky the menu list would scroll down but then grind to a halt.

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=thedon808] i did have a look at the live cd, i tried it at work on a celeron 500mhz 128ram it eventually booted but was so slow i couldnt load anything if i was lucky the menu list would scroll down but then grind to a halt.[/QUOTE]

Yeah. Live CDs hate 128mb of RAM. So does Gnome, thats why I use XFCE on my machine like that.

---

### Post by Sionide on 2005-05-24
One thing's for sure, if you tried installing Gentoo it'd take you a good couple of weeks. :P

---

### Post by Kyral on 2005-05-24
[QUOTE=Sionide]One thing's for sure, if you tried installing Gentoo it'd take you a good couple of weeks. :P[/QUOTE]

Amen to that. I thats the primary reason I switched to Ubuntu. Power of APT and 2 hour install beats Portage and a 2 **DAY** install. 

And yah, two hour install is normal for me (I mean from the time I boot the Ubuntu CD to the time I login to GNOME) and I'm running 512 MB RAM and a 2.17 GHz CPU

---

### Post by DutchLau on 2005-05-24
I timed my install, I got 55 minutes and a bit! Mind you, that was when there were no updates for Hoary yet!

---

### Post by Sionide on 2005-05-25
I didn't time it but I'm fairly sure it was around about an hour or two. I installed Windows before hand, had a brand new laptop to play around with, no OS pre-installed :D It's now running Ubuntu in a 38.5gig partition and Windows in a 2.5gig partition. Great!

---

### Post by davidgypsy on 2005-05-25
[QUOTE=thedon808]I installed Ubuntu the other day and it took around 2 hours! My system is a PII 350Mhz 128ram so its not fast. I previously had fedora installed on it but it just took up too much space nearly 3gb, and that only took 45mins - 1hour to install. So you can see my concern. I haven’t really used it much yet as its only for a learning machine hopefully to become my fileserver, and host my website from it. But as i have to install apache, php, and, samba etc I don’t really want to sit through another long and drawn out install process. Cause fedora had them on the install so would it be quicker just to go back to fedora rather than wait around for ubuntu to install the other apps i need? or is there another distro that will install quicker that isn’t as big as fedora you could recommend[/QUOTE]


I recently installed Ubuntu 5.04 onto an old AMD K2 with only 64 mb RAM, and it took about an hour. I am sure it could only be that it must have gotten the updated aplications off the web, which it does if you are live at time of install.

---

### Post by Mart on 2005-05-25
When I installed on my 433Cel 192m laptop it took almost 2 hours but FC3 took close to that as well.

---

### Post by davidmigl on 2005-05-25
It took 3 hrs on a 233 MHz machine with 128 MB RAM.  Loooong install times are normal.  Ubuntu seems to be focusing on things exactly opposite windows, some of whose goals were short installation time (at least for Longhorn) and fast boot-up time.

---

### Post by Sam on 2005-05-27
[QUOTE=davidmigl]It took 3 hrs on a 233 MHz machine with 128 MB RAM.  Loooong install times are normal.  Ubuntu seems to be focusing on things exactly opposite windows, some of whose goals were short installation time (at least for Longhorn) and fast boot-up time.[/QUOTE]
It's because all Windows installations are always the same, so the installer just copy an already configured block of bytes to the disk. With Ubuntu (and other distro), you have the choice of the package you install, and they must configure each other after that (which could take a long time).

---

### Post by clb137 on 2005-05-27
[QUOTE=Sionide]One thing's for sure, if you tried installing Gentoo it'd take you a good couple of weeks. :P[/QUOTE]


Have u tried to install Gentoo?   If so how did you find it??


clinton

---

