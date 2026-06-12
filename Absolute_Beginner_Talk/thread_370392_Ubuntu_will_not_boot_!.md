---
title: "Ubuntu will not boot !"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-25
This is not a new installation. I installed Ubuntu a month ago. It is the only OS. I restarted and when it got to the Ubuntu screen with the progress bar it hangs and has some weird blue and green garbled marks across the screen. I booted into recovery mode, but have not learned the commands to start to diagnose the problem. Please help.


screenshot:
[ATTACH]26146[/ATTACH]

---

### Post by Maestro23 on 2007-02-25
What were you doing before you restarted?

---

### Post by 67GTA on 2007-02-25
I was installing VLC and uninstalling mplayer via Synaptic and it froze. I canceled Synaptic and decided to restart and start over. That is when it happened.

---

### Post by urk_nono on 2007-02-25
Can you boot into Ubuntu, and not the recovery mode? Are there any errors appearing when you're booting up, or is it just your screen that's having problems?

---

### Post by 67GTA on 2007-02-25
I just remembered I was having trouble with my ati drivers earlier. I uninstalled the proprietary driver from ati website and did not reinstall the driver from Ubuntu repository. Will Ubuntu reload the default driver or did that screw it up?

---

### Post by urk_nono on 2007-02-25
Not to my experience, no. Ubuntu will still boot even though the ATI driver is not installed, that's what you have to do when you first install a new OS. Have you tried booting Ubuntu yet?

---

### Post by 67GTA on 2007-02-25
It won't boot into Ubuntu, it hangs at the screen I posted. I got to a prompt by selecting the recovery mode at the grub menu.

I am on my daughters computer now.

---

### Post by urk_nono on 2007-02-25
I see. I'm not entirely sure, but it might be trouble with your xorg.conf. Doing **dpkg-reconfigure xserver-xorg** might do the trick.

---

### Post by 67GTA on 2007-02-25
Okay, I am at the start of the configuration. I am afraid this might get messy. Is there some documentation for this process?

---

### Post by Maestro23 on 2007-02-25
> **67GTA said:**
> Okay, I am at the start of the configuration. I am afraid this might get messy. Is there some documentation for this process?

Just read what it says, if you are not sure, go with default values so you can get back into the system.  Then install the correct driver for your card.

---

### Post by 67GTA on 2007-02-25
I went through the configuration and it still hangs at the same screen. The system is running in the recovery mode. When I reboot it says it is shutting down firewall, etc.

---

### Post by 67GTA on 2007-02-25
I went through the configuration and it still hangs at the same screen. The system is running in the recovery mode. When I reboot it says it is shutting down firewall, etc. How can I veiw the text as it is loading in recovery mode. I can't catch everything to see if it is posting an error.

---

### Post by 67GTA on 2007-02-25
Okay, here goes:
Finally booted in recovery mode (text). Got error message:
Failed to start the x server. It is likely not set up correctly. Result of file output: 
X window version 7.1.1
x protocol version 11
build os linux 2.6.15.7
current os linux shawnr-desktop 2.6.17-11-generic #2 smp
module loader present
(==) log file /var/log/xorg.0.log
(==) using config file /etc/x11/xorg.conf
(EE) no devices detected
Fatal server error


I am going to try reconfigure again...

---

### Post by 67GTA on 2007-02-25
Nada. It will not boot past the progress screen in graphical mode. Tried lspci command: ATI Technologies Inc Unknown device 4d52. Anyone have any more ideas?

---

### Post by 67GTA on 2007-02-25
Update:

Well it finally loaded. I changed the x server driver from ati to vesa and was able to boot up in failsafe Gnome. When I tried to boot into Gnome I got this message: /etc/gdm/presession/default: registering your session with wtmp and utmp.

/etc/gdm/presession/default: running: /usr/x11r6/bin/sessreg-a-w /var/log/wtmp   106 can't open /etc/profile

When I booted into failsafe Gnome I got the message: error starting the gnome settings daemon. unable to determine the adress of the message bus.

---

### Post by 67GTA on 2007-02-25
The last error message in failsafe gnome was to try man dbus-launch and man dbus-daemon for help. I tired them, but do not completely understand. Anyone have any expertise with that area?

---

