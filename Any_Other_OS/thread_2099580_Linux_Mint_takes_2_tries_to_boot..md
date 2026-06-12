---
title: "Linux Mint takes 2 tries to boot."
date: 2012-12-29
forum: Any Other OS
---

### Post by Buruk on 2012-12-29
When I start the computer the grub screen shows, I choose linux mint cinnamon 14 and then the screen goes blank. Nothing else happens after that, I have to hold the power button down. Then when I start it again it works fine, and this cycle repeats every time I start the computer. What is wrong?

---

### Post by 2F4U on 2012-12-30
What is in the log files when the start fails?

---

### Post by Buruk on 2012-12-30
This is the log from /var/log/boot.log. It's not code but I thought it would be best to put it in a code box to help with reading and save page space.

```
fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
fsck from util-linux 2.20.1 
udevd[674]: failed to execute '/usr/sbin/alsactl' '/usr/sbin/alsactl restore 0': No such file or directory 
  
/dev/sda5: recovering journal 
/dev/sda6: clean, 9151/655360 files, 152606/2621440 blocks 
/dev/sda8: recovering journal 
/dev/sda7: recovering journal 
/dev/sda9: recovering journal 
/dev/sda5: clean, 262/32768 files, 38096/131072 blocks 
/dev/sda12: recovering journal 
/dev/sda7: clean, 219645/458752 files, 1516256/1835008 blocks 
/dev/sda12: clean, 11608/1302528 files, 793803/5207808 blocks 
/dev/sda8: clean, 11/196608 files, 29884/786432 blocks 
/dev/sda9: clean, 11023/262144 files, 283207/1048576 blocks 
 * Starting bluetooth daemon[164G[ OK ] 
 * Starting CUPS printing spooler/server[164G[ OK ] 
 * Starting Samba Auto-reload Integration[164G[ OK ] 
 * Stopping Samba Auto-reload Integration[164G[ OK ] 
 * Stopping Failsafe Boot Delay[164G[ OK ] 
 * Starting System V initialisation compatibility[164G[ OK ] 
kernel.shmmax = 128000000 
 * Setting sensors limits       [170G  [164G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
 * Stopping System V initialisation compatibility[164G[ OK ] 
 * Starting System V runlevel compatibility[164G[ OK ] 
 * Starting [164G[ OK ] 
 * Starting [164G[ OK ] 
 * Starting restore sound card(s') mixer state(s)[164G[ OK ] 
 * Starting ACPI daemon[164G[ OK ] 
 * Starting anac(h)ronistic cron[164G[ OK ] 
 * Starting [164G[ OK ] 
 * Starting [164G[ OK ] 
 * Starting save kernel messages[164G[ OK ] 
 * Starting [164G[ OK ] 
 [33m*[39;49m VirtualBox Additions disabled, not in a Virtual Machine 
 * Starting regular background program processing daemon[164G[ OK ] 
 * Starting deferred execution scheduler[164G[ OK ] 
 * Starting CPU interrupts balancing daemon[164G[ OK ] 
 * Stopping save kernel messages[164G[ OK ] 
 * Starting MDM Display Manager mdm       [170G  [164G[ OK ] 
```

---

### Post by xenopeek on 2012-12-31
It may help to know some bits about your hardware. Can you share the output of:
```
inxi -Fxz
```
That it always fails to boot on the first go sounds like some device is not fully powered on yet. You may try to go into your BIOS and disable "fast boot" or somthing similar. You want to achieve the computer doing a full POST (power on self check) before loading the operating system. Most computers come configured with "fast boot", where there won't be done a full POST. Hence it may be that the first time the operating system is loaded faster than that all devices are ready, while if you then reset everything is read as it has had more time.

---

### Post by dsv47 on 2012-12-31
Install Gnome Display Manager (gdm) and replace MDM with gdm as the default login display manager.

---

