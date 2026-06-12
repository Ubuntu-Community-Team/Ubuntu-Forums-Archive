---
title: "System reboots on its own"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by wildkarde on 2007-07-29
No idea why it's happening.  I have a UPS connected to this computer so it can't be a power outage (brown-out) unless it's something defective with the UPS.

This is all I could find on var log messages.

```
Jul 29 09:22:37 contarc-desktop -- MARK --
Jul 29 11:13:14 contarc-desktop syslogd 1.4.1#20ubuntu4: restart.
Jul 29 11:13:14 contarc-desktop kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 29 11:13:14 contarc-desktop kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 29 11:13:14 contarc-desktop kernel: Symbols match kernel version 2.6.20.

```

Anywhere else where i can find anything?

Any ideas anyone?

Thanks in advance

---

### Post by 505 on 2007-07-29
Check the wakeup on lan option. It in your BIOS settings.

---

### Post by DBStevens on 2007-07-29
New or old system?

Running what at the time of the reboot?

Most recent additions if the system has been rock solid until now.

What is in 

/var/log/daemon.log

/var/log/apport.log  and /var/log/apport.log.1

/var/log/debug

---

### Post by wildkarde on 2007-07-29
System is new.  

Ubuntu Feisty x86.

debug.log
```
Jul 29 11:13:15 contarc-desktop NetworkManager: <information>^Istarting... 
Jul 29 11:13:18 contarc-desktop hcid[5510]: Bluetooth HCI daemon
Jul 29 11:13:18 contarc-desktop NetworkManager: <debug info>^I[1185721998.828951] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jul 29 11:13:18 contarc-desktop hcid[5510]: Starting SDP server
Jul 29 11:13:20 contarc-desktop apcupsd[5561]: apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Jul 29 11:13:20 contarc-desktop apcupsd[5561]: NIS server startup succeeded

```

/var/log/apport.log is empty and /var/log/apport.log.1 

```
apport (pid 10249) Sat Jul 28 13:23:40 2007: script: /usr/bin/deluge, interpreted by /usr/bin/python2.5 (command line "/usr/bin/python /usr/bin/deluge")
apport (pid 10249) Sat Jul 28 13:23:40 2007: apport: report /var/crash/_usr_bin_deluge.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
apport (pid 11882) Sat Jul 28 13:48:39 2007: called for pid 10389, signal 11
apport (pid 11882) Sat Jul 28 13:48:39 2007: script: /usr/bin/deluge, interpreted by /usr/bin/python2.5 (command line "/usr/bin/python /usr/bin/deluge")
apport (pid 11882) Sat Jul 28 13:48:39 2007: apport: report /var/crash/_usr_bin_deluge.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

```

I should probably take a look at that because for some reason, deluge has been crashing a lot as of late.  

I will reboot now and take a look at the wakeup on lan option on the BIOS.

Thanks

---

### Post by DBStevens on 2007-07-29
Also running memtest for a couple of hours wouldn't hurt.

It could be just about anything from a loose card to bad memory and that's even before you get to various Bios and other software settings.

---

### Post by wildkarde on 2007-07-29
Hmm, i might have been mistaken.

It did it again.  The logs says that it reboots but it doesn't actually reboot.  It shuts down.

This makes no sense.   Any other ideas?

---

### Post by DBStevens on 2007-07-29
Running what at the time of the reboot/shutdown whatever?

Most recent additions if the system has been rock solid until now.

What is in

/var/log/daemon.log

Does your system have over temperature protection and if so can that shut the system off or just throttle down the clock rate?

---

### Post by Raptor45 on 2007-07-29
Just to throw out the idea, are you sure you have a good enough PSU to handle your computer?

---

### Post by bigfox on 2007-07-30
The last time my computer was having this problem it was the Power Supply.

Power Supplies die in one of 3 ways.

1:  They have the decency to just stop functioning.

2:  They stop functioning and take something else expensive with them.

3:  They wig out and send dirty power to your computer and make other parts act up.  They mess with your head and drive you nuts trying to figure out what is wrong with your computer.

---

### Post by DBStevens on 2007-07-30
Which is one of the reasons I was asking such question as what was running, requested that memtest be run etc.

It is also a new system and he has a device between his computer and power.

Is the system home brew if so did you check the  power consumption requirements and size the power supply accordingly (including extra for future additions) , are all of the power connectors securely connected.   I had one that wasn't so good going to a hard drive at one point, it caused me a bit of trouble. 

As for bigfox's list I can vouch for number 2,  I lost a motherboard and processor to one that went poof.

---

