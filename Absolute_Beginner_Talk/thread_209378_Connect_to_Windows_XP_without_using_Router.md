---
title: "Connect to Windows XP without using Router"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by jeffreyvergara.NET on 2006-07-05
I've trying to connect my Ubuntu Dapper to Windows XP and vice versa but no luck. I have tried several tutorials like installing & configuring samba but I still can't make it work.

I have two machines, Ubuntu Dapper, primary with ADSL (usb) Internet connection and the other is my Windows XP. It is easy to connect the two machines in Windows XP, without using a router and hub, I only used cat5 cable (lan cable) connected to both lan cards, then in "Network Places" >> "Set up a home or small office network" >> choose "Other" >> choose "This computer connects directly to the internet. I do not have a network yet." did the same thing on the 2nd PC with the same workgroup as the 1st PC. and thats it. I can share files and stuff including Internet connection. (the 1st pc must be on so the 2nd pc can have a internet connection)

How do you do this in Ubuntu Dapper to Windows XP?

---

### Post by calx on 2006-07-05
Have a look at these threads;
[http://ubuntuforums.org/showthread.php?t=91370&highlight=gateway+nat]("http://ubuntuforums.org/showthread.php?t=91370&highlight=gateway+nat")
[http://ubuntuforums.org/showthread.php?t=205750&highlight=gateway+nat]("http://ubuntuforums.org/showthread.php?t=205750&highlight=gateway+nat")
[http://ubuntuforums.org/showthread.php?t=72076]("http://ubuntuforums.org/showthread.php?t=72076")

[QUOTE=jeffreyvergara.NET]I've trying to connect my Ubuntu Dapper to Windows XP and vice versa but no luck. I have tried several tutorials like installing & configuring samba but I still can't make it work.

I have two machines, Ubuntu Dapper, primary with ADSL (usb) Internet connection and the other is my Windows XP. It is easy to connect the two machines in Windows XP, without using a router and hub, I only used cat5 cable (lan cable) connected to both lan cards, then in "Network Places" >> "Set up a home or small office network" >> choose "Other" >> choose "This computer connects directly to the internet. I do not have a network yet." did the same thing on the 2nd PC with the same workgroup as the 1st PC. and thats it. I can share files and stuff including Internet connection. (the 1st pc must be on so the 2nd pc can have a internet connection)

How do you do this in Ubuntu Dapper to Windows XP?[/QUOTE]

---

### Post by ProjectGod on 2006-07-05
why cant you use samba? when you say you cant connect do you mean share files or share internet? make sure you've got firewalls on both machines letting traffic in from both IPs. XP builtin firewall is a pretty lame firewall that aint very userfriendly and produces excess process that arent needed.

---

### Post by jeffreyvergara.NET on 2006-07-05
> hen you say you cant connect do you mean share files or share internet?
Yes.

i've got my firewall disable in Windows XP,  i just don'w know about my Ubuntu... I did not installed firestarter.

> [http://ubuntuforums.org/showthread.php?t=91370&highlight=gateway+nat](http://ubuntuforums.org/showthread.php?t=91370&highlight=gateway+nat)
it seems not working in Dapper

> [http://ubuntuforums.org/showthread.php?t=205750&highlight=gateway+nat](http://ubuntuforums.org/showthread.php?t=205750&highlight=gateway+nat)
It's opposite in my case. Ubuntu will be the host and Windows will be client

> [http://ubuntuforums.org/showthread.php?t=72076](http://ubuntuforums.org/showthread.php?t=72076)
same as above

---

### Post by ProjectGod on 2006-07-05
the only wy to go for file sharing between ubuntu and windows is samba... you've probably tried this but check it out anyway... try removing purging all the conf files for samba / smbfs... and try reinstalling **samba **and **smbfs **via aptitude.

wiki.ubuntu.com ... search for samba
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) ... filesharing / samba

for internet connection sharing... hm that's tricky what type of internet connection do you use. modem? router? dial up / adsl?

---

### Post by ProjectGod on 2006-07-05
if you have a usb router then try connecting the two machines via a crossover cable. straight nic to nic.

i'm outta here!

---

### Post by woedend on 2006-07-05
i'd run the internet shared via firestarter or bridging, then use samba to share files.  
Bridging tends to be easier but normally cannot be done without a router.  Firestarter uses NAT but without the messy setup.  One thing at a time lets see if we can get internet working?
Install firestarter
enable internet connection sharing in firestarter.  Make the local device(shared device) the card that goes out to the windows pc.  Internet device should be the modem(if its detecting correctly)
In sys->admin->networking, set the eth card that connects to the windows machine to have static ip address 192.168.0.1, netmask 255.255.255.0  don't put a gateway in.
On the windows machine, you will want to set it to have a static ip address of 192.168.0.2, netmask 255.255.255.0, gateway of 192.168.0.1 , and also must specify the dns servers.
The firewall must be on and activated with internet connection sharing box checked(no errors), the internet should then work...ive run this setup across both computers and xboxes so I promise it can be done :)
Let me know if this works for you...good luck :).

---

