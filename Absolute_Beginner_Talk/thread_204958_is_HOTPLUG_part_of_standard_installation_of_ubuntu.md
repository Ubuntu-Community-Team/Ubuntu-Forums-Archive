---
title: "is HOTPLUG part of standard installation of ubuntu 6.06 ?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by aleskm on 2006-06-27
hi, I've got some minor problems with my USB ADSL modem, I have read some forums and it seems that I should have something called HOTPLUG installed in Ubuntu. Ubuntu should then be able to detect my USB modem when I connect it. But it seems I don't have HOTPLUG in my Ubuntu, there is no /sbin/hotplug and no /etc/hotplug.

How I can add HOTPLUG to my Ubuntu ?

thx for help

---

### Post by harishg on 2006-06-28
During the startup do you see the hotplug being loaded.You can also check the log file and see if it is loaded.(/var/log/kern.log)Check if you have pcmia-cs installed.If not install it through synaptic.Are you sure if your adsl modem is supported ?

---

### Post by dmizer on 2006-06-28
i don't believe it's possible to load ubuntu without hotplug.  it is however possible to disable hotplug via a hack that can be found in the how to section about making your ubuntu boot faster.

boot your computer without the modem connected.  then connect the modem.  in terminal type "dmesg" and post the output here.

---

### Post by aleskm on 2006-06-28
[QUOTE=harishg]Are you sure if your adsl modem is supported ?[/QUOTE]

Yes, I'm sure. I can connect to Internet with it, but if I want to do it, I must first start my Windows XP and then reboot to Linux. Linux then recognizes the modem, but if I start Linux first, modem doesn't work. I looked into syslog a there is a message "... hotplug misconfiguration ?"

---

### Post by FuturePast on 2006-06-28
[QUOTE=aleskm]Yes, I'm sure. I can connect to Internet with it, but if I want to do it, I must first start my Windows XP and then reboot to Linux. Linux then recognizes the modem, but if I start Linux first, modem doesn't work. I looked into syslog a there is a message "... hotplug misconfiguration ?"[/QUOTE]

I think hotplug has been superseded by udev and hal (hardware abstraction layer).

From what you have said, it sounds like a firmware issue i.e. the modem needs the OS to upload its firmware. Windows obviously does this.
Ubuntu keeps firmware in /lib/firmware/...
I would see if I can download the firmware from somewhere (the manufacturer's site or the driver site) and copy it to the correct directory.

---

### Post by Apple 101 on 2006-06-28
What about the hotplug package in Synaptic?

---

