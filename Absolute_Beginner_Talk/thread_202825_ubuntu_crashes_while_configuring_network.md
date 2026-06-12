---
title: "ubuntu crashes while configuring network"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Architeuthis on 2006-06-24
hello, i am new on this forum :) 

I recently reinstalled ubuntu dapper drake (because i wase using the ext2 file format), before my internet with usb wirelles adapter worked well (asus wl-167g, on dapper drake). When i try to configure my connection ( i have a adsl router) i give the same settings as before. (essid: philips wifi, normal ascii and dhcp). Then i click activate and ubuntu crashes. It just stops doing anything, my mouse wont work etc, it simply doesnt do a thing.

Can someone help me?

---

### Post by Apple 101 on 2006-06-24
This happened to me.  Are you using ndiswrapper?  If you are, you need an original .inf and .sys driver.

---

### Post by Architeuthis on 2006-06-24
I havent installed anything i just use the standard network thing in ubuntu.
Or uses ubuntu ndiswrapper as standard?

---

### Post by Apple 101 on 2006-06-24
No ndiswrapper is an optional package.  You're lucky if your card is detected natively.

---

### Post by Architeuthis on 2006-06-24
My card is detected natively and it worked before i reinstalled ubuntu. I had the same problem also before i reinstalled, but i didnt gave a name to my computer in the network so i thougt that made ubuntu crash. Now i gave it a name in the network and it still crashes. I discovered the "ifup" command this makes the network work, but it still crashes 1 on 4 times. 

Should i download ndiswrapper and install those original .inf and .sys drivers, and were can i find those?

---

### Post by sailor2001 on 2006-06-24
[QUOTE=Architeuthis]My card is detected natively and it worked before i reinstalled ubuntu. I had the same problem also before i reinstalled, but i didnt gave a name to my computer in the network so i thougt that made ubuntu crash. Now i gave it a name in the network and it still crashes. I discovered the "ifup" command this makes the network work, but it still crashes 1 on 4 times. 

Should i download ndiswrapper and install those original .inf and .sys drivers, and were can i find those?[/QUOTE]
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by Architeuthis on 2006-06-24
ok it works! :D 

i used the ifup command and went to the network menu it said rausb0 was active,  i pressed ok and ubuntu crashes again. After the restart it still worked! I checked the settings in the network menu (yep again it crashed). Then i checked them using iwconfig and there i saw the correct settings.

Is this a bug in ubuntu or something like that?

thanks for the help anyway!

---

### Post by Apple 101 on 2006-06-24
How can you get the wireless network to start up from boot?  Mine has to be manually started because it is never in the network manager area.

---

### Post by raptros-v76 on 2006-06-24
add auto <interface name> to the end of /etc/network/interfaces

---

### Post by Apple 101 on 2006-06-24
Great!!! Thanks.

---

