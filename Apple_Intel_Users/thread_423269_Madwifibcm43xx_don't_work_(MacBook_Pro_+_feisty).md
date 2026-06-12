---
title: "Madwifi/bcm43xx don't work (MacBook Pro + feisty)"
date: 2007-04-25
forum: Apple Intel Users
---

### Post by ExplodingPickle.org on 2007-04-25
For some reason with Ubuntu Feisty on my MacBook Pro neither bcm43xx or madwifi work. I've tried compiling madwifi myself, and generating the firmware from wl_apsta.o and then "modprobe bcm43xx." I still only see "eth0" and "lo" in "ifconfig" though. I've also tried disabling the wired connection and restarting. Does anyone here know why this is happening?

---

### Post by ronocdh on 2007-04-26
> **ExplodingPickle.org said:**
> For some reason with Ubuntu Feisty on my MacBook Pro neither bcm43xx or madwifi work. I've tried compiling madwifi myself, and generating the firmware from wl_apsta.o and then "modprobe bcm43xx." I still only see "eth0" and "lo" in "ifconfig" though. I've also tried disabling the wired connection and restarting. Does anyone here know why this is happening?
No, I don't, really. I have been focusing on wireless as the one thing that isn't working for me in Feisty! I know that encryption doesn't really work with Madwifi and the Atheros chipsets (at least the new ones, like 5416/8); the Madwifi guide says it's just WAP that doesn't work, and WEP does, but I disagree. I have gotten Madwifi to work briefly only when I completely shut off all encryption on my router, and sorry, but I'm not living like that!

Ndiswrapper has proved a huge pain for me in Feisty. I'm actually working on it right now, but my problem is just that after I add the driver and run **sudo ndiswrapper -l**, I get:
```
net5416: driver installed
```
when I should be getting:
```
net5416: driver installed
device (168C:0024) present
```
I've tried manually associating the two by using
```
sudo ndiswrapper -a 168C:0024 net5416
```
(syntax for which I found in **ndiswrapper man**) but then I just get a bunch of symlink errors. In short: argh!

Anyone with insights please post, I'm going mad. Also, I wiped my 64-bit installation of Feisty, thinking that was my problem. But nay. On 32-bit Edgy it was an extremely simple ndiswrapper process; not so in Feisty!

So, my friend, you are not alone. ;)

---

### Post by wigglydiggly on 2007-04-27
I get the same thing:

brad@MacBook:~$ ndiswrapper -l
net5416 : driver installed

but my wireless is working.  I guess it ok.  Been running fiesty like this for two months and no problems.

---

