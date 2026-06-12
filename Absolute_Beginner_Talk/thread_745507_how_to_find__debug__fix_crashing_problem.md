---
title: "how to find / debug / fix crashing problem?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2008-04-04
Hi.
I recently experiencing random freezes and crashes. They became way more frequent than before I installed new compiz plugins and a patched nautilus and eel (don't know what's that).

I followed two guides:
**[Install additional plug-ins for compiz in Gutsy]("http://forum.compiz-fusion.org/showthread.php?t=5303")**
and
**[4 Different Wallpapers - Gnome]("http://forum.compiz-fusion.org/showthread.php?t=6199")**

After that, I've uninstalled the patched nautilus (make uninstall) and reinstalled the original one. I seem to get even more crashes after that. The crashes are quite random. A new window pops up, dragging the view of a pdf file, 

How can I find out what's causing the crashes? Does compiz leave a crash log file? I would very much like to fix this problem rather than reinstall the whole system.

Thank you in advance.

Oh, I almost forgot. I am on an Acer laptop with NVidia card (Geforce Go 7300) with NVidia Driver Version 100.14.23

---

### Post by northern lights on 2008-04-04
Do you realize the tutorial for the 4 desktops was written for Feisty?

I've tried this during my spring break for fun. Did not get it to run under Gutsy. This is since Gutsy's current repo's have compiz 0.6.1 and the patches and all are for 0.5.0 (I think, don't quote me on the latter version). Bottom line: forget it in Gutsy.

Most likely a solution to the freezing would be a clean reinstall of nautilus. Maybe also compiz, if you're patches got something to do with it. If you'd want to do that, run ```
sudo apt-get remove nautilus
sudo apt-get autoremove
```
Manually check in "/usr/bin/" for "nautilus". If existent, delete. You could do all that from the commandline, but it's probably easier to use an alternative file manager (as your nautilus will be uninstalled for a bit). So before doing all the above, run ```
sudo apt-get install thunar
```Thunar is xfce's file manager (I think, again don't quote me, anyways, it does the job). You can start it from the panel/menu or with "thunar" from commandline or "Alt+F2" dialog. To delete "nautilus" in "/usr/bin/" you'll have to open the file manager as root, using ```
gksu thunar
```

Reinstall.```
sudo apt-get nautilus
```
Repeat with compiz, if problem persists.



P.S. On a side note:

4 different wallpapers is relatively easy. With the downside of not having a desktop. I'll explain:

In your tutorial, a "wallpaper plugin" is required. compiz 0.6.1 comes with such a thing. I assume you're using the cube. If so, in the cube plugin's settings you can put several wallpapers under some tab. If you put four, compiz will draw 4 different wallpapers on each side of the cube to the root of the screen. The problem lies in the fact, that nautilus is not only the gnome file manager, but also the app that draws the desktop and it's icons (not exactly according to the *nix philosophy of having one discrete program for one discrete task...). And it does so ontop of compiz' wallpapers.

So naturally uninstalling nautilus will allow you're 4 wallpapers to show. Unfortunately you now got 4 desktops without icons. If the panel, the menu, the home folder and an optional dock suffice, it's a solution. If you care for icons. No more but one wallpaper in Gutsy.

---

### Post by lian1238 on 2008-04-04
> **northern lights said:**
> Do you realize the tutorial for the 4 desktops was written for Feisty?

I've tried this during my spring break for fun. Did not get it to run under Gutsy. This is since Gutsy's current repo's have compiz 0.6.1 and the patches and all are for 0.5.0 (I think, don't quote me on the latter version). Bottom line: forget it in Gutsy.
I did get the wallpaper plugin to work in gutsy, but not sure if it was after I reinstalled compiz and related stuff. I don't know the version of compiz but CCSM is 0.5.2 now.

Thanks for the info, **northern lights**. I tried the Wallpaper plugin after I uninstalled nautilus but doesn't work. The option in Desktop Cube works though. I use cairo-dock so, icons are not really necessary. But I also use conky and a conky with a solid background isn't that pretty. I'll just stick with the same wallpaper on all 4. (I just switched to the Cube today. I used Desktop Wall for a very long time :))

I'll try using this for a day, without reinstall compiz. No freezes in a day = problem gone. If it persists, I'll try uninstalling compiz.

Thanks for your help!

---

### Post by northern lights on 2008-04-04
Good thing its working. Should be fine - since it's nautilus you had tried to patch.

> **lian1238 said:**
> I don't know the version of compiz but CCSM is 0.5.2 now!

On that one: So is my ccsm. If you were interested in compiz, run ```
compiz --version
```

---

### Post by lian1238 on 2008-04-05
I experienced a freeze earlier, so uninstalled compiz as well. I manualled deleted ~/.compiz/ and ~/.gconf/apps/compiz/ and reinstalled compiz. Now all unsupported plugins are gone and the settings are default. But it didn't fix the freezing problem.

I am experiencing freeze ups which are about 15 seconds long. On the CPU monitor applet on the panel shows a big chunk of the CPU usage (50% - because it's a dual-core??). Is there a way to find out which app caused the high CPU usage, AFTER it has passed?

I think it has something to do with the video driver or card. Something to do with the display, because only after the 15-or-so-seconds freeze, do I sometimes see the bottom half (or sometimes just a quarter) of the screen as black for just a blink (1 frame?). Does that make sense at all?

How do I reinstall a (safe?) NVidia driver? I used envy to automatically install the current one.

Thanks so much for a solution.

---

### Post by northern lights on 2008-04-06
Crap. Sorry to hear problem persists.

What driver's are you using for your nvidia card?

> **lian1238 said:**
> Is there a way to find out which app caused the high CPU usage, AFTER it has passed?

Run ```
dmesg
``` right after unfreezing...

---

### Post by lian1238 on 2008-04-07
Running dmesg after defreeze showed several lines with NVRM. Forum was closed for maintenance so I didn't get to post the exact message. I googled it and found someone else who had a similar freeze. Their problem was overheating. A new cooler fan solved it. My laptop is over one year old, maybe it IS overheating. I'll report back after the next freeze.

---

### Post by northern lights on 2008-04-08
Are you getting something like ```
NVRM: Xid: YY, YYYYYYYYYY....
```where the Ys are integers?

This is an issue related to your nvidia card. Unfortunately, that's about the only thing that's for certain. Your only hope of decoding the error message and having it tell you what it is [nvnews]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=13").

Fair enough, it could be the graphics card overheating, it as well could not be the case. Newer or older drivers might solve the problem. Check your card's temperature and google whether it's normal or not.

Run ```
lspci | grep VGA
``` to find out your card model and install "conky" if you don't have a system monitor.

---

### Post by lian1238 on 2008-04-09
> **northern lights said:**
> Are you getting something like ```
NVRM: Xid: YY, YYYYYYYYYY....
```where the Ys are integers?
Yes, it's like this:
```
[234751.372000] NVRM: Xid (0001:00): 6, PE0000 0a68 00000000 0000fdbc 00f7f7f7 00000000
[234751.392000] NVRM: Xid (0001:00): 30,  L1 -> L0

```
I just had a 10-second-freeze-up while "scale"-ing, the compiz plugin.

> **northern lights said:**
> 
This is an issue related to your nvidia card. Unfortunately, that's about the only thing that's for certain. Your only hope of decoding the error message and having it tell you what it is [nvnews]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=13").

Thanks.

> **northern lights said:**
> 
Fair enough, it could be the graphics card overheating, it as well could not be the case. Newer or older drivers might solve the problem. Check your card's temperature and google whether it's normal or not.

Run ```
lspci | grep VGA
``` to find out your card model and install "conky" if you don't have a system monitor.
I have conky but not configured with the temp. I have nvidia-settings and the core temp is 57C. It also has "Slowdown Threshold" and "Degrees: 105 C" under it. I'm guessing 57C is normal. Usually, it's around 60C without a freeze.

I am guessing it has something to do with the nvidia card trying to use system ram for its cache. On my laptop, it says "Up to 256MB NVIDIA GeForce Go 7300 w/TurboCache technology".

---

### Post by lian1238 on 2008-04-09
I had a crash. I can't seem to find anything in syslog at the time of the crash, only after it.
It crashed and restart at 15:05:02. There was nothing before in the log before that.. or is there?

/var/log/syslog
```

Apr  9 07:40:30 lian-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr  9 07:40:30 lian-laptop anacron[14002]: Job `cron.daily' terminated
Apr  9 07:40:30 lian-laptop anacron[14002]: Normal exit (1 job run)
Apr  9 07:53:52 lian-laptop -- MARK --
Apr  9 08:09:01 lian-laptop /USR/SBIN/CRON[16819]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 08:15:19 lian-laptop kernel: [226019.152000] sky2 eth0: Link is down.
Apr  9 08:17:01 lian-laptop /USR/SBIN/CRON[17330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 08:33:52 lian-laptop -- MARK --
Apr  9 08:39:01 lian-laptop /USR/SBIN/CRON[18726]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 08:53:52 lian-laptop -- MARK --
Apr  9 09:09:01 lian-laptop /USR/SBIN/CRON[20643]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 09:17:01 lian-laptop /USR/SBIN/CRON[21161]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 09:33:52 lian-laptop -- MARK --
Apr  9 09:39:01 lian-laptop /USR/SBIN/CRON[22554]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 09:53:52 lian-laptop -- MARK --
Apr  9 10:09:01 lian-laptop /USR/SBIN/CRON[24528]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 10:17:01 lian-laptop /USR/SBIN/CRON[25042]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 10:33:52 lian-laptop -- MARK --
Apr  9 10:35:42 lian-laptop kernel: [234442.468000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Apr  9 10:39:01 lian-laptop /USR/SBIN/CRON[26504]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 10:40:51 lian-laptop kernel: [234751.372000] NVRM: Xid (0001:00): 6, PE0000 0a68 00000000 0000fdbc 00f7f7f7 00000000
Apr  9 10:40:51 lian-laptop kernel: [234751.392000] NVRM: Xid (0001:00): 30,  L1 -> L0
Apr  9 10:53:52 lian-laptop -- MARK --
Apr  9 11:09:01 lian-laptop /USR/SBIN/CRON[29179]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 11:17:01 lian-laptop /USR/SBIN/CRON[29691]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 11:24:49 lian-laptop gdm[23419]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  9 11:25:16 lian-laptop hcid[5664]: Default passkey agent (:1.153, /org/bluez/passkey) registered
Apr  9 11:25:16 lian-laptop hcid[5664]: Default authorization agent (:1.153, /org/bluez/auth) registered
Apr  9 11:25:18 lian-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr  9 11:25:19 lian-laptop kernel: [237418.984000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
Apr  9 11:25:19 lian-laptop kernel: [237419.104000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
Apr  9 11:39:01 lian-laptop /USR/SBIN/CRON[31892]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 11:49:59 lian-laptop kernel: [238898.876000] UDP: short packet: From 24.104.98.2:60945 25649/109 to 192.168.0.2:6881
Apr  9 12:09:01 lian-laptop /USR/SBIN/CRON[1809]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 12:17:01 lian-laptop /USR/SBIN/CRON[2328]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 12:33:52 lian-laptop -- MARK --
Apr  9 12:39:01 lian-laptop /USR/SBIN/CRON[3724]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 12:53:52 lian-laptop -- MARK --
Apr  9 13:09:01 lian-laptop /USR/SBIN/CRON[5752]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 13:17:01 lian-laptop /USR/SBIN/CRON[6278]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 13:33:52 lian-laptop -- MARK --
Apr  9 13:37:18 lian-laptop kernel: [245338.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:18 lian-laptop kernel: [245338.648000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245338.744000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245338.744000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245338.804000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245338.804000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245338.896000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245338.896000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245338.968000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245338.968000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.056000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.056000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.140000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.140000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.208000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.208000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.308000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.308000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.384000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.384000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.468000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.468000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.552000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.552000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:19 lian-laptop kernel: [245339.648000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:19 lian-laptop kernel: [245339.648000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:20 lian-laptop kernel: [245339.720000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:20 lian-laptop kernel: [245339.720000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:20 lian-laptop kernel: [245339.824000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:20 lian-laptop kernel: [245339.824000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:20 lian-laptop kernel: [245339.896000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:20 lian-laptop kernel: [245339.896000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:20 lian-laptop kernel: [245340.012000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:20 lian-laptop kernel: [245340.012000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:20 lian-laptop kernel: [245340.056000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:20 lian-laptop kernel: [245340.056000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:21 lian-laptop kernel: [245340.868000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:21 lian-laptop kernel: [245340.868000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:21 lian-laptop kernel: [245340.952000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:21 lian-laptop kernel: [245340.952000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:21 lian-laptop kernel: [245341.048000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:21 lian-laptop kernel: [245341.048000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:37:21 lian-laptop kernel: [245341.104000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Apr  9 13:37:21 lian-laptop kernel: [245341.104000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Apr  9 13:39:01 lian-laptop /USR/SBIN/CRON[7983]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 13:53:52 lian-laptop -- MARK --
Apr  9 14:09:01 lian-laptop /USR/SBIN/CRON[11064]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 14:17:01 lian-laptop /USR/SBIN/CRON[12710]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  9 14:33:52 lian-laptop -- MARK --
Apr  9 14:39:01 lian-laptop /USR/SBIN/CRON[15631]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr  9 14:53:53 lian-laptop -- MARK --
Apr  9 15:05:02 lian-laptop syslogd 1.4.1#21ubuntu3: restart.
Apr  9 15:05:02 lian-laptop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Apr  9 15:05:02 lian-laptop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Apr  9 15:05:02 lian-laptop kernel: Symbols match kernel version 2.6.22.
Apr  9 15:05:02 lian-laptop kernel: No module symbols loaded - kernel modules not enabled. 
Apr  9 15:05:02 lian-laptop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe90000 (usable)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 000000003fe90000 - 000000003ff00000 (ACPI NVS)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr  9 15:05:02 lian-laptop kernel: [    0.000000] 126MB HIGHMEM available.
Apr  9 15:05:02 lian-laptop kernel: [    0.000000] 896MB LOWMEM available.
Apr  9 15:05:02 lian-laptop kernel: [    0.000000] found SMP MP-table at 000f6690
<other start up messages> 
```

/var/log/Xorg.0.log
```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.2)
Current Operating System: Linux lian-laptop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr  9 15:05:10 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1025,0110 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1025,0110 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1025,0110 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1025,0110 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1025,0110 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1025,0110 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1025,0110 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d7 card 1025,0110 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4352 card 1025,0110 rev 14 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4222 card 8086,1005 rev 02 class 02,80,00 hdr 00
(II) PCI: 0a:09:0: chip 104c,8039 card 3000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 0a:09:2: chip 104c,803b card 1025,0110 rev 00 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,11), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x54000000 - 0x540fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x54100000 - 0x541fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:30:0), (0,10,14), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 10 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 10 non-prefetchable memory range:
	[0] -1	0	0xd2200000 - 0xd22fffff (0x100000) MX[B]
(II) Bus 10 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 11: bridge is at (10:9:0), (10,11,14), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 11 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation Quadro NVS 110M / GeForce Go 7300 rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[1] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[2] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[3] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[4] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[10] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[16] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[17] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[1] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[2] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[3] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[4] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[10] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[16] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[17] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.23  Thu Oct  4 10:52:20 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.23  Thu Oct  4 10:18:31 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[19] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1280x800 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7300 (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.46.43
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7300 at PCI:1:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1280x800+0+0"
(II) NVIDIA(0):     "DFP:1024x768+0+0"
(II) NVIDIA(0):     "DFP:800x600+0+0"
(II) NVIDIA(0):     "DFP:640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (108, 106); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT: nvidia-auto-select +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce Go 7300 (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.72.22.46.43
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce Go 7300 at PCI:1:0:0:
(--) NVIDIA(1):     LPL (DFP-0)
(--) NVIDIA(1): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): LPL (DFP-0): Internal Dual Link LVDS
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[8] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[9] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[10] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[11] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[19] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) NVIDIA(0): Initialized GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video. NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "DFP:1280x800+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
(II) NVIDIA(0): Setting mode "DFP:1280x800+0+0"
```

/var/log/Xorg.1.log
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux lian-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Nov 22 02:47:35 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 10

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1025,0110 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1025,0110 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1025,0110 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1025,0110 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1025,0110 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1025,0110 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1025,0110 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1025,0110 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d7 card 1025,0110 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4352 card 1025,0110 rev 14 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4222 card 8086,1005 rev 02 class 02,80,00 hdr 00
(II) PCI: 0a:09:0: chip 104c,8039 card 3000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 0a:09:2: chip 104c,803b card 1025,0110 rev 00 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,11), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x54000000 - 0x540fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x54100000 - 0x541fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:3), (0,5,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:30:0), (0,10,14), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 10 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 10 non-prefetchable memory range:
	[0] -1	0	0xd2200000 - 0xd22fffff (0x100000) MX[B]
(II) Bus 10 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 11: bridge is at (10:9:0), (10,11,14), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
(II) Bus 11 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation Quadro NVS 110M / GeForce Go 7300 rev 161, Mem @ 0xd1000000/24, 0xc0000000/28, 0xd0000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[1] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[2] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[3] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[4] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[10] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[16] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[17] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[1] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[2] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[3] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[4] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[5] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[10] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[11] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[12] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[16] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[17] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[18] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce Go 7300 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[16] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[22] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[23] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[24] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[5] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[6] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[7] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[8] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[9] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[19] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[25] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[26] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[27] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce Go 7300"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xD1000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 800
(II) NV(0): Panel is LVDS
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 28.00-33.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x768" (hsync out of range)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x800" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x768" (hsync out of range)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using driver mode "1280x800" (hsync out of range)
(II) NV(0): Not using mode "1280x800" (no mode of this name)
(--) NV(0): Virtual size is 640x480 (pitch 640)
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(==) NV(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd2205000 - 0xd2205fff (0x1000) MX[B]
	[8] -1	0	0x54100000 - 0x54100fff (0x1000) MX[B]
	[9] -1	0	0x54000000 - 0x54003fff (0x4000) MX[B]
	[10] -1	0	0xd2504000 - 0xd25043ff (0x400) MX[B]
	[11] -1	0	0xd2500000 - 0xd2503fff (0x4000) MX[B]
	[12] -1	0	0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[22] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[28] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[29] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[30] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xc0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Synaptics DeviceOff called
Synaptics DeviceOff called
```

Edit: sorry for the huge file of syslog and kern.log. I didn't realize it was THAT big.

---

### Post by lian1238 on 2008-04-11
I've uninstalled the NVidia driver installed by Envy and installed nvidia-glx-new and reinstalled compiz and removed emerald. I've just had a freeze, unrecovered by Ctrl+Alt+F1/Backspace. I found this line in syslog:
```

Apr 11 13:05:27 lian-laptop kernel: [10459.352000] NVRM: Xid (0001:00): 2, CCMDs 00000002 0000357c 0000046c aaaaaaaa 00000006
Apr 11 13:07:15 lian-laptop kernel: [10567.228000] SysRq : Keyboard mode set to XLATE
Apr 11 13:08:16 lian-laptop syslogd 1.4.1#21ubuntu3: restart.

```
Does anyone know what that means?

Edit: the 2nd line is me doing Alt+SysRq+REISUB. But the first line.. it's that NVRM again!

---

