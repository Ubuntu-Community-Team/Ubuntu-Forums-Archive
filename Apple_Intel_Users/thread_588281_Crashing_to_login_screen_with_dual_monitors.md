---
title: "Crashing to login screen with dual monitors"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by ward83 on 2007-10-23
After upgrading to Gutsy, I cannot seem to get my dual monitor setup working right. I had them working with no problems in Feisty. I'm on a 20" Intel iMac, with a secondary 20" HP widescreen monitor, both 1680x1050. Using the same xorg.conf that worked in feisty, as soon as I log in, I see a blank desktop on both screens briefly, and can move the mouse correctly between both, but then I crash back to the login screen. If I edit my xorg.conf and disable the second monitor, all is fine. Also, if I leave the second monitor enabled, and select 'Failsafe GNOME' as my session, I can log in correctly. I do have compiz fusion enabled, which runs flawlessly without the second monitor enabled, but it does not run in failsafe mode. The only suspicious log entry I've found so far is in the syslog:

```

Oct 23 10:41:47 ward gdm[6512]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

```

Any ideas where else I could look, or what to look for?

---

### Post by ward83 on 2007-10-23
Well, after searching around some more, the problem appears to be related to Xgl. By removing "xserver-xgl", I can once again log in and use dual monitors with Xinerama. However, without Xgl, I can't enable compiz. Anyone have any suggestions?

---

### Post by cyberdork33 on 2007-10-23
[http://ubuntuforums.org/showthread.php?t=583642](http://ubuntuforums.org/showthread.php?t=583642)

Also, see 7.10 Release Notes:
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)
[quote="Gutsy Gibbon Release Notes"]
**Dual-head (multi-screen) setups**
[LIST]
[*]  The ati driver has dropped MergedFB / Xinerama support in favour of xrandr 1.2 support, and old multi-head xorg.conf setups will break. To set up dual-head see the guides at [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) or [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
[*]  As xrandr and xinerama are incompatible, you cannot mix some graphics cards using xrandr-enabled drivers with others that are still limited to using xinerama. In this case, you will need to revert to pre-xrandr versions of the respective drivers: for Intel cards, use the old "i810" driver instead of "intel", for ATI cards, use the old [6.6 version]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/1:6.6.3-2ubuntu6").
[*]  With xrandr, it is now possible to use Compiz in a multi-screen setup, however it is dependent on available video card memory. The workaround for this issue is to switch to a lower virtual resolution.[/LIST][/quote]

---

### Post by ward83 on 2007-10-23
Yeah, thats the topic I found which led me to remove Xgl. Basically, I can either have one monitor with Xgl and compiz, or dual monitors with no Xgl or compiz. For now I'm just running one, because Xgl seems to run much smoother and more responsive than without it.

---

### Post by cyberdork33 on 2007-10-23
Note that the release notes also say that xinerama no longer works... so your old xorg.conf is invalid as well.

---

### Post by ward83 on 2007-10-24
Yeah, I thought I had read that we would no longer need Xinerama in gutsy. However, even if you use the new 'screens & graphics' app to set up your secondary monitor, it still adds a xinerama line to xorg.conf. As long as I have Xgl uninstalled, my previous xorg.conf (with xinerama) works fine.

---

