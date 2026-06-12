---
title: "Wireless not found on Dell 630m"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by ejricha on 2007-03-09
I have a Dell 630m laptop, I had Fedora on it for a few months, but could never quite get my wireless card working.  It was recognized and could see wireless networks, but never connect to them.  I switched to Ubuntu a week ago after encountering some problems with Yum that pissed me off.

Anyway, I am no closer now to having a working wireless card; I am actually much further.  It does not even appear when I do an "lspci -v".  Does this mean that I am completely hosed with wireless on Ubuntu?  Or are there some kernel configurations that I can apply?  And if so, how do I do this? (I vaguely remember doing it with Fedora, but I am completely new to Ubuntu).

I would just switch back to Fedora, but like how quickly/cleanly Ubuntu boots.  Other than that and aptitude, I really don't see many differences.  Maybe I just don't have enough experience with either.

Eric

---

### Post by benfindlay on 2007-03-09
Its worth while trying ndiswrapper with your card

Best place for instructions is here: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

Its also worth launching terminal and typing ```
sudo apt-get install ndiswrapper-utils ndiswrapper-source ndisgtk
```
This will install all the ndiswrapper packages for you. The reason I say this is because the guide above only tells you to install 1 of the packages. The others are useful too!

It only takes about 5 minutes to get your wireless up and runnin that way. Plus if you install wifi-radar using ```
sudo apt-get install wifi-radar
``` you can use it to scan for available wireless networks!

The ndisgtk package puts a GUI config into your System>>Administration menu called "Windows Wireless Drivers" which makes it even easier to configure!

Hope this helps!

---

