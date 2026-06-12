---
title: "Problem setting up wireless connection"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by abreusamuel on 2007-03-08
Hi. I've been wanting to use linux for a long time and i was recommended ubunto. All the instalation went ok, until the wireless internet connection.

The wireless card was not detected by ubuntu so I used ndiswrapper, just as it is told in the desktop guide. 
I could do everything and got:
Installed ndis drivers:
mrv8ka51       driver present, hardware present

The next step was to load a module. I typed:
sudo depmod -a
and hit enter and it didn't complain, but when i typed:
sudo modprobe ndiswrapper
I got the message: FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko): Invalid argument

I've been searching on the internet for solutions, but couldn't find one. If anyone can help I would really apreciate.

I hope i can post my next message in the forum using ubuntu....

Thanks

---

### Post by benfindlay on 2007-03-08
Not sure about your specific problem, but its worth taking a look here I reckon: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")
I used this and didnt have to do anything with depmod

Hope this helps!

---

### Post by gigaferz on 2007-03-19
I had the exact same problem
I got my wireless working today!!

You have to unistall ndswrapper and download it, compile it and install it,

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

Let us know if it helped you

I am using Ubuntu Ultimate gamers Edition, and It has MOre packages than the regular release.

In order to compile you will need addiitonal packages..  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I dont know what exactly but linux headers is for sure and some "build essential"...ohh, well...at least it'll point you in the right direction

---

