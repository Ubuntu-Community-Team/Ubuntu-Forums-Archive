---
title: "Usb problem"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Wolfiebad on 2007-03-17
I have just installed Ubuntu on my system and it seems that it didn't detect my usb. I tried pluging in my usb wireless network adapter and mp3 player. Absolutely nothing happens. I have one of Via motherboards (can't remember witch it's 4-5 years old) with intel pentium 1.7 GHz and Radeon 9100. Any ideas what might be the problem? (I had similar problems in windows and a usb driver installation helped but i can't get one for linux :( )

---

### Post by astoltz on 2007-03-17
Plug in the MP3 player.  Then open a terminal and put in the following command:```
tail -n 20 /var/log/syslog
```That will print out the last few lines of your system log file.  There should be something about the recent USB plugin.  Post the output of that command back here and we can help decipher.

---

### Post by Wolfiebad on 2007-03-17
Ok here's what i got:
```
Mar 17 18:21:19 miha-desktop kernel: [17179645.832000] Bluetooth: RFCOMM socket layer initialized
Mar 17 18:21:19 miha-desktop kernel: [17179645.832000] Bluetooth: RFCOMM TTY layer initialized
Mar 17 18:21:19 miha-desktop kernel: [17179645.832000] Bluetooth: RFCOMM ver 1.7
Mar 17 18:21:19 miha-desktop anacron[3999]: Anacron 2.3 started on 2007-03-17
Mar 17 18:21:20 miha-desktop anacron[3999]: Normal exit (0 jobs run)
Mar 17 18:21:20 miha-desktop /usr/sbin/cron[4025]: (CRON) INFO (pidfile fd = 3)
Mar 17 18:21:20 miha-desktop /usr/sbin/cron[4026]: (CRON) STARTUP (fork ok)
Mar 17 18:21:20 miha-desktop /usr/sbin/cron[4026]: (CRON) INFO (Running @reboot jobs)
Mar 17 18:22:53 miha-desktop gconfd (miha-4165): starting (version 2.16.0), pid 4165 user 'miha'
Mar 17 18:22:54 miha-desktop gconfd (miha-4165): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 17 18:22:54 miha-desktop gconfd (miha-4165): Resolved address "xml:readwrite:/home/miha/.gconf" to a writable configuration source at position 1
Mar 17 18:22:54 miha-desktop gconfd (miha-4165): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 17 18:22:54 miha-desktop gconfd (miha-4165): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 17 18:22:54 miha-desktop gconfd (miha-4165): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 17 18:22:58 miha-desktop kernel: [17179745.580000] NET: Registered protocol family 10
Mar 17 18:22:58 miha-desktop kernel: [17179745.580000] lo: Disabled Privacy Extensions
Mar 17 18:22:58 miha-desktop kernel: [17179745.580000] IPv6 over IPv4 tunneling driver
Mar 17 18:23:11 miha-desktop kernel: [17179757.760000] ISO 9660 Extensions: Microsoft Joliet Level 3
Mar 17 18:23:11 miha-desktop kernel: [17179757.840000] ISOFS: changing to secondary root
Mar 17 18:23:14 miha-desktop gconfd (miha-4165): Resolved address "xml:readwrite:/home/miha/.gconf" to a writable configuration source at position 0
```

---

### Post by astoltz on 2007-03-17
There's nothing there about a USB device.  When you plug it in under Windows, what happens?  It is recognized as a removable drive?  Or do you have to start some other application to communicate with the player?  Also, I should have had you try this before:  Post the output of ```
lsusb
``` with the player plugged in.

---

### Post by Wolfiebad on 2007-03-18
In windows i had to install the usb (not the the device that is plugged in). After that it worked fine.

P.S.: if i type lsusb nothing happens.

---

### Post by francesco44 on 2007-03-18
Look at my post which follows yours and analyse your "fstab" file in "etc" to check if you have a line corresponding to usb mount...just create also a directory with sudo mkdir in /media.

With USB PROBLEMS ALWAYS LOOK FIRST AT FSTAB!

I lost a week with silly outputs of such or such command line!

Best regards

---

### Post by francesco44 on 2007-03-18
I forgot to say that you must create /media/usb

---

### Post by muiredachau on 2007-03-20
I just installed ubuntu recently and when I boot up the system comes across a hotplug subsystem failure so I can't use my usb's

---

### Post by Wolfiebad on 2007-03-20
Thanks Francesco I'll try it during weekend.

---

