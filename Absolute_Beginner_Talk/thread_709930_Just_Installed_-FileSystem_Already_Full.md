---
title: "Just Installed -FileSystem Already Full"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by yachuwey on 2008-02-27
I just installed ubuntu a couple of days ago and now it says that my 11.7gb filesystem is full and I can't install Wine. I installed it as a dual boot with XP. Why is it full already? I have only installed automatix, geany, swiftweasel, a few other things listed in automatix.

---

### Post by glennric on 2008-02-27
Try running 
```
sudo apt-get clean
```
and perhaps try the "Disk Usage Analyzer" in Applications->Accessories

---

### Post by 3rdalbum on 2008-02-27
Did you make it as just one partition, or did you split it up in two partitions (with one for /home/)?

If the latter, then your / partition is probably not big enough. The / partition holds everything except your user settings and documents. Even when it's full, it will not enroach on your /home/ partition.

If you don't have a separate partition for /home/, then you might just have some big temporary files (DVD rips, maybe?). These are located in /tmp/, so you can either delete them manually or just restart the computer.

---

### Post by asmoore82 on 2008-02-27
**[COLOR="Red"][SIZE="3"]Automatix is *actively _dangerous_* to your Linux system![/SIZE][/COLOR]**

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by yachuwey on 2008-02-27
Thanks for the replies. get clean freed up 900+mb. Disk Analyzer shows the following:

/10.5gb
    >var 7.7gb
         >log 7.5gb

When I installed ubuntu, I just used the default settings. I don't know how to check or resize the partitions.

---

### Post by asmoore82 on 2008-02-27
run this in a terminal and post the output:
```
find /var/log -type d -exec du -sh '{}' \;
```

just for fun, mine looks like this:
```
**[COLOR="Lime"]~$[/COLOR]** find /var/log -type d -exec du -sh '{}' \;
6.9M    /var/log
4.0K    /var/log/dist-upgrade
4.0K    /var/log/news
560K    /var/log/installer
12K     /var/log/fsck
68K     /var/log/apache2
4.0K    /var/log/bittorrent
68K     /var/log/apt
36K     /var/log/gdm
4.0K    /var/log/samba
48K     /var/log/exim4
8.0K    /var/log/partimage
84K     /var/log/cups
4.0K    /var/log/apparmor
4.0K    /var/log/unattended-upgrades
```

---

### Post by yachuwey on 2008-02-27
> **asmoore82 said:**
> run this in a terminal and post the output:
```
find /var/log -type d -exec du -sh '{}' \;
```

just for fun, mine looks like this:
```
**[COLOR="Lime"]~$[/COLOR]** find /var/log -type d -exec du -sh '{}' \;
6.9M    /var/log
4.0K    /var/log/dist-upgrade
4.0K    /var/log/news
560K    /var/log/installer
12K     /var/log/fsck
68K     /var/log/apache2
4.0K    /var/log/bittorrent
68K     /var/log/apt
36K     /var/log/gdm
4.0K    /var/log/samba
48K     /var/log/exim4
8.0K    /var/log/partimage
84K     /var/log/cups
4.0K    /var/log/apparmor
4.0K    /var/log/unattended-upgrades
```

Here it is:
7.5G    /var/log
1.1M    /var/log/installer
4.0K    /var/log/samba
4.0K    /var/log/unattended-upgrades
4.0K    /var/log/dist-upgrade
12K     /var/log/fsck
4.0K    /var/log/apparmor
4.0K    /var/log/bittorrent
132K    /var/log/apt
4.0K    /var/log/news
28K     /var/log/cups
32K     /var/log/gdm

---

### Post by asmoore82 on 2008-02-27
okay, this shows us that all of the directories under /var/log are of normal size,
but /var/log itself is HUGE(>7 Gigabytes)... so lets look at the files in /var/log, sorted by size:
```
ls -rSs /var/log
```
and, only the end of the list(the biggest files) are important, so post the output of this:
```
ls -rSs /var/log | tail
```

again, mine is
```
**[COLOR="Lime"]~$[/COLOR]** ls -rSs /var/log | tail
268 debug.0
 44 lastlog
304 messages.0
316 messages
320 syslog
336 udev
404 daemon.log.0
416 kern.log.0
444 kern.log
604 daemon.log
```

---

### Post by glennric on 2008-02-27
You should look closer at the /var/log directory.  Your log directory should not be anywhere close to 7.5G.

---

### Post by yachuwey on 2008-02-27
Here is  the list from the var/log:
 43792 messages.3.gz
  43792 kern.log.3.gz
  43812 syslog.3.gz
 691144 messages
 691152 kern.log
 691244 syslog
1124136 syslog.0
1124136 messages.0
1124136 kern.log.0
2099204 acpid

---

### Post by asmoore82 on 2008-02-27
Yikes!! your system is trying to tell you *something*; this is a subjective process, but ...
run these commands to view the logs and try to pick out what may be the major issue:
(while in `less`, use the UP and DOWN arrows to scroll and press Q to quit)
```
less /var/log/messages
less /var/log/acpid
less /var/log/kern.log
```

after that, I would say you are clear to *carefully* delete the logs like this:
run```
gksu nautilus
```
in this graphical file browser with elevated privilege,
navigate to /var/log and *carefully* delete some stuff,
leaning towards old "archived" logs(*.gz files);
make sure you "empty" the trash if necessary to actually clear up the space.

---

### Post by yachuwey on 2008-02-28
Here are the messages:

Feb 27 08:01:24 dad-desktop kernel: [123145.463362] ACPI: Unable to turn cooling device [de54b2a0] 'off'
Feb 27 08:01:24 dad-desktop kernel: [123145.467634] ACPI: Transitioning device [FAN1] to D3

[Sun Feb 24 07:36:23 2008] notifying client 4861[107:116]
[Sun Feb 24 07:36:23 2008] notifying client 5294[0:0]
[Sun Feb 24 07:36:23 2008] completed event "thermal_zone THRM 00000081 00000000"
[Sun Feb 24 07:36:23 2008] received event "thermal_zone THRM 00000081 00000000"

Feb 27 08:01:24 dad-desktop kernel: [123145.480523] ACPI: Transitioning device [FAN1] to D3
Feb 27 08:01:24 dad-desktop kernel: [123145.480527] ACPI: Transitioning device [FAN1] to D3
Feb 27 08:01:24 dad-desktop kernel: [123145.480530] ACPI: Unable to turn cooling device [de54b2a0] 'off'

They all appear to be the same.

Can I delete messages.log.0 and kern.log.o and kern.log..etc that are on the list?.

---

### Post by glennric on 2008-02-28
I had that problem on another computer.  I ended up having to blacklist the "fan" module to get it to stop.  There was something wrong with either the "fan" module or with the sensors on the motherboard itself.  Try adding the line "blacklist fan" to the end of the file /etc/modprobe.d/blacklist and see if this problem persists after that.  You will have to reboot for that to take effect.

---

### Post by yachuwey on 2008-02-28
I tried gedit, but when I save it, it says that i don't have permission.

---

### Post by yachuwey on 2008-02-28
Thanks for the help so far.

I still need help. ubuntu won't let me save the blacklist file. Also, can I delete the large .log and .log.0 files?

---

### Post by spamzilla on 2008-02-28
> **yachuwey said:**
> I tried gedit, but when I save it, it says that i don't have permission.

In terminal type:

sudo nautilus /var/log/ 

and delete any files you want.

**BE CAREFUL WITH WHAT YOU DO** as you are running as root and have full rights to destroy your system!

---

### Post by glennric on 2008-02-28
To edit the blacklist file type
```
gksu gedit /etc/modprobe.d/blacklist
```

---

