---
title: "Ubuntu Fresh Install - Crashing again"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-06-01
hey all,
last night i installed ubuntu again, due to the never ending crashes. So, i left my computer on last night to see if it crashes, when i woke up this morning, to my surprise it was working absolutely fine. Much to relief, happiness was short lived, that as soon as i got on gaim messenger soon after sending a couple of messages, ubuntu crashed once again! I Have no clue what on earth is going on..please if someone could help me out, it would be really nice. I have been looking forward to Ubuntu for a long time, and now that i have finally installed it, its working much to my disappointment. 
Thanks in advance
sibot

---

### Post by jonward0690 on 2007-06-01
Well what exactly does it do does it just lock up and have you tried booting into safe mode by going to sessions at the login screen and change it to safe mode.

---

### Post by sibot on 2007-06-01
Haven't tried booting to safe mode, but the whole computer just freezes, its like a total lock down. Could there be any possibility that Gaim might be causing this mess? I'm downloading the latest version of Gaim i.e. Pidgin, hope things work better with that. Are there any log files i can look into to see what went wrong and caused the crash?

---

### Post by jonward0690 on 2007-06-01
Yea there should be a system log you can look at I believe you should be able to go to system the go to administration.

---

### Post by daimaru on 2007-06-01
you should probably check your logs 

/var/log/messages 
/var/log/syslog 

and anything else you can find in there :D

---

### Post by sibot on 2007-06-01
Hmmmm okay, its a bunch of messed up lines with things i have no idea about, but in a few places i did manage to find error in syslog

Jun  2 13:46:41 sibot NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received:

and i guess this was from before/after the computer rebooted
Jun  2 13:46:27 sibot NetworkManager: <debug info>^I[1180772187.502671] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jun  2 13:46:27 sibot kernel: [   32.123139] Bluetooth: RFCOMM socket layer initialized
Jun  2 13:46:27 sibot kernel: [   32.123158] Bluetooth: RFCOMM TTY layer initialized
Jun  2 13:46:27 sibot kernel: [   32.123162] Bluetooth: RFCOMM ver 1.8
Jun  2 13:46:27 sibot anacron[5109]: Anacron 2.3 started on 2007-06-02
Jun  2 13:46:27 sibot anacron[5109]: Normal exit (0 jobs run)
Jun  2 13:46:27 sibot /usr/sbin/cron[5136]: (CRON) INFO (pidfile fd = 3)
Jun  2 13:46:27 sibot /usr/sbin/cron[5137]: (CRON) STARTUP (fork ok)
Jun  2 13:46:27 sibot /usr/sbin/cron[5137]: (CRON) INFO (Running @reboot jobs)

can anyone make any sense of it?

---

### Post by Lucifiel on 2007-06-01
Do you have any Bluetooth devices on your computer?

If not, you can try going to "services"(it's somewhere in the Menu) and then try to disable all Bluetooth-related services.

---

### Post by sibot on 2007-06-01
I don't have any bluetooth devices, and i disabled it from the services, i sure do hope it helps. Btw, downloading the official linux drivers from Nvidia site would be better than restricted drivers manager?

---

### Post by sibot on 2007-06-01
Hey,
This is where my system is crashing

Jun  2 14:30:30 sibot gconfd (digvijoy-5273): Resolved address "xml:readwrite:/home/digvijoy/.gconf" to a writable configuration source at position 0
Jun  2 14:30:31 sibot NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jun  2 14:30:31 sibot NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

I dont even have a wireless card??? where can i disable this??

---

### Post by sibot on 2007-06-01
Anyone? any idea?

---

### Post by Lucifiel on 2007-06-01
Well, crud... if I was running Ubuntu now, I'd be able to help you. (I don't have any o/ses installed now and am running off an iso).

---

### Post by sibot on 2007-06-02
hmm no worries, thanks for the help!

---

