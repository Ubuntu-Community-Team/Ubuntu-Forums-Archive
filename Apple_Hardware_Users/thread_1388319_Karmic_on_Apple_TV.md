---
title: "Karmic on Apple TV"
date: 2010-01-23
forum: Apple Hardware Users
---

### Post by uneekwahn on 2010-01-23
Hi everyone,

I'm finally posting here in desperation to see if anyone can providing any suggestions on how I can diagnose / resolve my current issue.

Brief history:

Installed a Broadcom CrystalHD card into my AppleTV whilst in was running the AppleTV O/S and had installed XBMC on to it.  Had absolutely no problems with it.  The Broadcom card was installed, but there were no drivers or libraries, so it sat dormant.

Finally the drivers for the card were released and working under linux, so I did a netboot install of hardy onto the AppleTV, installed the Broadcom drivers and it worked perfectly with XBMC for about 2 weeks, then it started to just randomly reboot, but only when either first getting into XBMC (past the splash screen and just sitting in the main menu) or when browing through menus in XBMC.  It **never** crashed whilst playing video files (mkv, avi etc) or playing music (mp3, flac) and **never** crashed when in xwindows (gnome) or sitting at the cli.

I then decided to try karmic and did a fresh netboot install and again, everything was working, but only for about a week when I started to get the random reboots again.  I'm not running xwindows on the machine this time, I am booting straight into xbmc in standalone mode, and again, it does not appear to reboot when at the cli.

I've tried:

Unplugging my usb hub / keyboard mouse
Unplugging the broadcom card and reseating it (I will remove it and see if the machine runs stable without it shortly)
Turned off ondemand so the cpu stays at 1ghz with no stepping / throttling
Different xbmc skins
Plugging it into a different powerpoint incase it was somehow surging and rebooting

xbmc.log and /var/log/syslog have not revealed any useful information (imo) to indicate a specific task / issue that may be causing the problem and copies of those logs are available in the xbmc forum thread below.

Here is my thread on the xbmc forums [http://xbmc.org/forum/showthread.php?t=66769](http://xbmc.org/forum/showthread.php?t=66769) which may contain other bits of information I've unintentionally ommitted here.

If anyone can give some suggestions as to other ways I can troubleshoot this to try to determine why it continues to sporadically reboot, it would be greatly appreciated.

Regards,

Jason.

---

