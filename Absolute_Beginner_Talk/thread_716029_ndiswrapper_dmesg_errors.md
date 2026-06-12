---
title: "ndiswrapper dmesg errors"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Timdejager on 2008-03-05
Hello,

I Finally got my wireless linksys card working in combination with my router (linux noob). From my perspective it works flawlessly but ndiswrapper keeps giving dmesg errors. Does anybody know if there is any way at all to make ndiswrapper stop doing this, because they keep showing up repeatedly and clutter up dmesg, so i can't see any other errors i am having.

Also I have another problem, I have no idea if its related. But every once in a while say 3 mins. I get this weird noise from my speakers something like: 'ding ding dong' and after an interval of 5 secs 'ding dang dong' it sounds like a little bell (hard to describe a sound :P). Does anybody have any ideas what this annoying noise could mean?

Thanks,

Tim

---

### Post by jimv on 2008-03-05
What's the error?

---

### Post by Timdejager on 2008-03-05
These are the errors I am having:

```
[ 2151.404228] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x49737973
[ 2151.404229] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x203a7273
[ 2151.404233] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x6b636f4c
[ 2151.404235] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x736f4c5f
[ 2151.404237] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x6e695f73
[ 2151.404239] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x72726574
[ 2151.404241] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x20747075
[ 2151.404244] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0xf8000a30
[ 2151.506465] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138A, count: 8, return_address: f8e4960a

```

and the they just keep coming

---

### Post by happyhamster on 2008-03-05
Do you have some kind of chat program running perhaps? In that case the sounds could be notifications that someone has logged on/off.

---

### Post by dca on 2008-03-05
I've seen this when two drivers are installed for the same wireless card...  Like restricted drivers added for MadWifi (Atheros) but user installed ndiswrapper & Windows driver w/o blacklisting the ath_pci kernel modules...
 
...what kind of wireless card is it?

---

### Post by Timdejager on 2008-03-05
Doh, that must be it! I'm also running pidgin but ithought i turned off all the sounds lol :P, thanks for clearing that up :)

> **dca said:**
> I've seen this when two drivers are installed for the same wireless card...  Like restricted drivers added for MadWifi (Atheros) but user installed ndiswrapper & Windows driver w/o blacklisting the ath_pci kernel modules...
 
...what kind of wireless card is it?

As for the wireless card It's a Linksys wmp54gx card with an airgo chipset. And you are right i didn't blacklist anything, i only saw instructions on blacklisting the broadcom chipset or something so i figured i didn't need to do it. Could you perhaps point me in the right direction?

---

### Post by dca on 2008-03-05
Well, the odd thing is you're indicating that it's working fine just filling up the message log.  If you put 'NdisWriteErrorLogEntry' into Google search you'll find a ton of issues relative to the card across quite a few Linux distro(s) but all pointing to it wasn't working in Linux.  A friend w/ the same issue (error log filled w/ same message and WiFi wouldn't work *period*), I added 'ath_pci' to the /etc/modules/blacklist.d file...  I can't remember, don't quote me...  If you're issue is similar you'll have to re-read those instructions you have and add something like 'bcxx' or something similar to the blacklist file...  Hopefully someone seeing this can confirm...

---

### Post by Timdejager on 2008-03-05
> **dca said:**
> Well, the odd thing is you're indicating that it's working fine just filling up the message log.  If you put 'NdisWriteErrorLogEntry' into Google search you'll find a ton of issues relative to the card across quite a few Linux distro(s) but all pointing to it wasn't working in Linux.

True, except when it defaulted to connect to my router whichat the time had a wpa encryption, suddenly I could not connect to any network any longer. And it even crashed ubuntu while starting up i eventually had to reinstall because I could no longer log in. So i removed the wpa encryption and with a 128 bit wep key it works just fine.

---

### Post by jimv on 2008-03-05
I would try uninstalling, and then building/install the latest Ndiswrapper (1.52)

sudo apt-get install build-essential
sudo apt-get remove --purge ndiswrapper
sudo rm -r /etc/ndiswrapper

Download the latest ndiswrapper source
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.52.tar.gz)

cd (whatever directory you put the file in)
tar -zxvf ndiswrapper-1.52.tar.gz
cd ndiswrapper-1.52.tar.gz
sudo make install

sudo ndiswrapper -i [your driver file]
sudo ndiswrapper -m
sudo modprobe ndiswrapper

---

### Post by Timdejager on 2008-03-05
I Tried what you suggested, that but it has no effect

---

