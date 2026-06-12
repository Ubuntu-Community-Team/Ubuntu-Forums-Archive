---
title: "Freeze after resume from suspend on MacPro"
date: 2012-08-24
forum: Apple Hardware Users
---

### Post by produnis on 2012-08-24
Hi folks, I am running Ubuntu 12.04 64bit on my old 2007-MacPro1,1

I dont use any proprietary drivers (e.g. NVIDIA)

My problem is, that my machine will randomly freeze after I resume from suspend. The machine is running for some time (1-8 minutes) and then just freezes.

I grepped dmesg and the X-logs for terms like "error", but found nothing...


any help welcome
;)

---

### Post by 2F4U on 2012-08-24
Did you look into /var/log/pm-suspend.log and /var/log/syslog?

---

### Post by produnis on 2012-08-24
Thank you vary much for your reply...

/var/log/pm-suspend.log looks fine:
```

Wed Aug 22 21:55:45 CEST 2012: Awake.
Wed Aug 22 21:55:45 CEST 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed Aug 23 21:55:46 CEST 2012: Finished.
produnis@Bilbo:~$ 

```


I cannot find any interesiting in /var/log/syslog - I grepped for ERROR and FAIL, but found nothing... what else could I look for?


Again, it doesn't freeze immediately; I can usually use it for a few minutes/seconds.  But individual applications start being unresponsive the moment I try to perform some activity in them, and shortly thereafter the system as a whole becomes unresponsive.

---

### Post by produnis on 2012-08-26
I just installed the Kubuntu-Desktop, and while using KDE, there are no freezes after resume from suspend anymore..

so, I guess this is a UNITY-2D related issue...
Is there any Unity-Logfile I should investigate?

---

