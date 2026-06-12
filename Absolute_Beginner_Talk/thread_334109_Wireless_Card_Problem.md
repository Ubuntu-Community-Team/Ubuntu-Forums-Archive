---
title: "Wireless Card Problem"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-08
Ok, i have Kubuntu 6.10 installed on my new HP dv2120us laptop.  It seems as though it has a bcm4311 wireless card (internal).  I tried using ndiswrapper to install the driver. and the output from ndiswrapper -l is 

bcmwl5   driver present

upon looking at my lspci output, i get this
```
0000:01:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

```

and its obviously not working....any ideas?

---

### Post by MkfIbK7a on 2007-01-08
ndisswrapper -l
should say
bcmwl5 driver present hardware present
if it doesnt try plugging the card in a little bit harder
i have the same driver (bcmwl5) and it worked for me after i worked for it;)

---

### Post by RMorris78 on 2007-01-08
i tried pluggin it in harder, and upon doing that i noticed it doesnt seem to be a traditional minipci slot, it almost looks like a pci-e x1 slot..... could this be possible?

its a laptop by the way

---

### Post by MkfIbK7a on 2007-01-08
ok type
sudo modprobe ndiswrapper
see if that helps and then go to the network preferences and configure your connection

---

### Post by RMorris78 on 2007-01-09
tried it, no output

isnt the problem here its not detecting the hardware?

---

### Post by MkfIbK7a on 2007-01-09
not sure im sorry:(

---

### Post by RMorris78 on 2007-01-09
thanks for the help anyways

does anyone have an idea why it would be seen as an "unknown device 4311" in lspci??

---

### Post by deadgobby on 2007-01-09
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
 There is some reading to do at the link. Good luck
Gobby

---

### Post by RMorris78 on 2007-01-09
ok, by doing a "sudo depmod -a" and then redoing everything with ndiswrapper it shows both the hardware and driver are present now! score...

so heres what i did

sudo ndiswrapper -i bcmwl5.inf
   no output (good im assuming)
sudo ndiswrapper -m
   Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
sudo modprobe ndiswrapper
   no output
iwconfig
    but no wlan0 :( what am i doing wrong?

---

### Post by RMorris78 on 2007-01-09
anyone have any ideas?

---

### Post by RMorris78 on 2007-01-09
bump

---

### Post by kbsuperstar on 2007-01-09
Have no fear, I have the same broadcom wireless card integrated into my Compaq.

Read through this thread, and make sure you have WINE (you can get it from automatix2).

[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=4311)

---

### Post by RMorris78 on 2007-01-09
i found this in dmesg, it doesnt look good

[17179592.796000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179592.904000] ndiswrapper (check_nt_hdr:155): Windows driver is not 32-bit; bad magic: 020B
[17179592.904000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17179592.908000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

