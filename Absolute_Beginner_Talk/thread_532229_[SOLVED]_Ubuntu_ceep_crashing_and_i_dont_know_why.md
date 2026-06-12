---
title: "[SOLVED] Ubuntu ceep crashing and i dont know why"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
MY computer keeps crashing for no reason i can see
every thing freezes no mouses or keybord input works exept for the 

"Razing skinny elefant is utterly boring" 
Ctrl+sys+(the fisrt letter of each word)  used to safely shutdown frozen system
that works

thought it was my ram so i ran a memcheck ther ram is fine
is there a log or something i should look at to see why it crashed 

i have been running Ubuntu for about a year and 1/2 same hardware, never had this problem before.
windows runs fine

Help pleases

---

### Post by splintercellguy on 2007-08-22
Check the System Log? Did you install anything recently?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
no for the install anything new

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
ok so i am looking at the system log, But what am i looking for

---

### Post by irish_flu on 2007-08-22
are there errors whose timestamps correspond to the crashing?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
lol Next time i will make shur to look at my clock
woops

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
I was up late last night and left it running after i went to bed, to see if it would freez. it did.
i dont know when but here is the stuff leading up to the last entry before i restarted it today
this is under the syslog
[PHP]
Aug 22 03:48:11 Ogerman NetworkManager: <information>^IClearing nscd hosts cache. 
Aug 22 03:48:11 Ogerman NetworkManager: <WARNING>^I nm_spawn_process (): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug 22 03:48:11 Ogerman NetworkManager: <information>^IActivation (eth0) successful, device activated. 
Aug 22 03:48:11 Ogerman NetworkManager: <information>^IActivation (eth0) Finish handler scheduled. 
Aug 22 03:48:11 Ogerman NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug 22 03:48:11 Ogerman ntpdate[5368]: step time server 82.211.81.145 offset -0.570990 sec
Aug 22 03:48:11 Ogerman kernel: [   36.168000] Time: acpi_pm clocksource has been installed.
Aug 22 03:48:11 Ogerman avahi-daemon[4885]: Registering new address record for fe80::216:e6ff:fe40:384 on eth0.*.
Aug 22 03:48:20 Ogerman kernel: [   45.816000] eth0: no IPv6 routers present
Aug 22 04:08:00 Ogerman -- MARK --
Aug 22 04:17:01 Ogerman /USR/SBIN/CRON[5373]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 22 04:28:00 Ogerman -- MARK --
Aug 22 04:48:01 Ogerman -- MARK --
Aug 22 05:08:01 Ogerman -- MARK --
Aug 22 05:17:01 Ogerman /USR/SBIN/CRON[5376]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)[/PHP]

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
pleases any ideas?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
welll it crashed agin

[PHP]Aug 22 15:55:38 Ogerman NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. [/PHP]

in the system log at time of crash

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
any who i think its my wire less card and i am going to try to blacklist the driver
i have an Ethernet so I don't need wireless in Linux
[PHP]RaLink RT2561/RT61 802.11g PCI
[/PHP]
i may try to get it working latter but if it stops the freezes

so ya how do i black list that driver

---

### Post by schorsch on 2007-08-22
If you know the module you should add it to "/etc/modprobe.d/blacklist" and reboot afterwards

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
> **schorsch said:**
> If you know the module you should add it to "/etc/modprobe.d/blacklist" and reboot afterwards

ya i dont know what the module is

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
i couldn't figure out how to black list the driver so i pulled the card out
and my computer has been running about 7 hours with out a problem before i couldn't even log in half the time so it was the wireless card or the driver for it.

anyway i dont need it but it would be nice if it worked who should i report the bug to and how

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-23
if anyone knows how to get this card working that would be great

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-25
hey the card work in 7.10

---

### Post by Bannor on 2007-10-25
> **<<joe>> said:**
> any who i think its my wire less card and i am going to try to blacklist the driver
i have an Ethernet so I don't need wireless in Linux
[PHP]RaLink RT2561/RT61 802.11g PCI
[/PHP]
i may try to get it working latter but if it stops the freezes

so ya how do i black list that driver

Joe 

I have been the victum of intermitent freezing.   What is blacklisting?  I don't have that driver so I must not have the same issue.  

When you freeze are you able to ctrl+alt+delete out of it?  cause I can only do a hard shut down

---

