---
title: "Battery always at 0%"
date: 2010-05-17
forum: Apple Hardware Users
---

### Post by somethingkindawierd on 2010-05-17
I recently did a clean install of Ubuntu 10.04 on my Macbook 2,1 and it suddenly stopped detecting the batter state.

The first few days it worked great. But now the battery always registers 0%, when on AC or unplugged.

Here's the info I found about my battery:
```
~$ ls /proc/acpi/battery
BAT0
~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         0 mWh
last full capacity:      0 mWh
battery technology:      rechargeable
design voltage:          0 mV
design capacity warning: 250 mWh
design capacity low:     100 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            
OEM info:    
```   

Anyone have thoughts on how I can fix this?

---

### Post by linuxopjemac on 2010-05-18
[http://ubuntuforums.org/showthread.php?t=1469819&page=2](http://ubuntuforums.org/showthread.php?t=1469819&page=2)

---

### Post by somethingkindawierd on 2010-05-18
Hmmm...this is interesting. Thank you for the link. Based on [this note about upowerd crashing]("http://ubuntuforums.org/showpost.php?p=9312236&postcount=17") I simply typed 'upower' into my terminal and the battery is working now.

I added it to my starup items and it seems to have fixed the issue permanently.

---

### Post by linuxopjemac on 2010-05-19
good for you.

---

### Post by somethingkindawierd on 2010-05-22
The fix I posted earlier stopped working on my MacBook 2,1 running 32 bit Ubuntu. So I investigated further. Then I came across this article at Apple: [http://support.apple.com/kb/HT3964?viewlocale=en_US]("http://support.apple.com/kb/HT3964?viewlocale=en_US")

I reset the System Management Controller and now my battery is working fine without any fix or hack.

---

