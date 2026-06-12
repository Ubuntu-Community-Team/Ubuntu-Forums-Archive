---
title: "Network Manager running invisible?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by DarqueWing on 2007-06-29
I was messing around with my toolbars, trying to make things look the way I wanted to, and somehow the Network Manager icon disappeared.  The NM is still running, which is fine - as long as I'm at home, but I need to keep my roaming options open, as I switch from wireless to wired depending on where I'm at.  When I try to "Add to Panel..." and then select Network Manager, I get something different from before (the swirling dots, and then bars when connected to indicate signal strength is what I want, now it just shows two monitors), and when I try to turn on roaming mode within this "Network Manager," it kicks me offline and doesn't see any signals at all.

So just what did I do here, and how do I put it back?

---

### Post by reset3x on 2007-06-29
> **DarqueWing said:**
> I was messing around with my toolbars, trying to make things look the way I wanted to, and somehow the Network Manager icon disappeared.  The NM is still running, which is fine - as long as I'm at home, but I need to keep my roaming options open, as I switch from wireless to wired depending on where I'm at.  When I try to "Add to Panel..." and then select Network Manager, I get something different from before (the swirling dots, and then bars when connected to indicate signal strength is what I want, now it just shows two monitors), and when I try to turn on roaming mode within this "Network Manager," it kicks me offline and doesn't see any signals at all.

So just what did I do here, and how do I put it back?

This sounds like you added "Network Monitor" to your panel... Not Network Manager... Try going into Synaptic and marking network-manager-gnome for reinstallation.... Then open the terminal and type  killall gnome-panel and hit enter... It should come back...

Good Luck!!

---

### Post by DarqueWing on 2007-06-29
Reset3x - I reinstalled network-manager-gnome and then did the killall command, as you suggested.  My panel disappeared briefly and popped right back up - but no network manager.  I did, however, find an application called "Wifi Radar," which purports to do about the same thing.  It works fine, but it's a clunkier interface and generally not as easy to work with as the network manager that I was getting used to.  Should I uninstall the Wifi Radar and try again?

Edit: I poked around and checked some settings.  Under "Sessions," the network manager is checked as a startup program, but the command line reads "nm-applet --sm-disable."  What is that "disable" suffix?  The NM is apparently coming on, because I was still signing on even without Wifi Radar, just without the convenient little icon showing me connection strength, etc.  Also, I realized that before, anytime I booted up, I was asked for my admin login in order to start "nm-applet," which I now assume means Network Manager, but not anymore.  So now I'm even more confused.

Thanks for your help, Reset3x.

---

### Post by reset3x on 2007-06-29
> **DarqueWing said:**
> Reset3x - I reinstalled network-manager-gnome and then did the killall command, as you suggested.  My panel disappeared briefly and popped right back up - but no network manager.  I did, however, find an application called "Wifi Radar," which purports to do about the same thing.  It works fine, but it's a clunkier interface and generally not as easy to work with as the network manager that I was getting used to.  Should I uninstall the Wifi Radar and try again?

Edit: I poked around and checked some settings.  Under "Sessions," the network manager is checked as a startup program, but the command line reads "nm-applet --sm-disable."  What is that "disable" suffix?  The NM is apparently coming on, because I was still signing on even without Wifi Radar, just without the convenient little icon showing me connection strength, etc.  Also, I realized that before, anytime I booted up, I was asked for my admin login in order to start "nm-applet," which I now assume means Network Manager, but not anymore.  So now I'm even more confused.

Thanks for your help, Reset3x.

You can uninstall wifiradar and then see here... :[http://ubuntuforums.org/showthread.php?t=479157&highlight=network+manager+gnome](http://ubuntuforums.org/showthread.php?t=479157&highlight=network+manager+gnome)

---

### Post by DarqueWing on 2007-06-29
Perfect, Rese3x.  That other thread had what I was looking for - the "Notification Area."  Turns out I was behind on updates, too, and didn't even know it because that's part of the Notification Area, as well.  Now I think I know exactly what happened, too - I found a nifty utility for watching my battery usage, and I liked that better than the one in that Notification Area, so I tried to remove it.  At the time, I thought it worked fine, but I didn't notice that I had removed more than the battery icon.  Well, that's a mystery solved.

Thanks for your help, Reset3x.

---

### Post by reset3x on 2007-06-29
> **DarqueWing said:**
> Perfect, Rese3x.  That other thread had what I was looking for - the "Notification Area."  Turns out I was behind on updates, too, and didn't even know it because that's part of the Notification Area, as well.  Now I think I know exactly what happened, too - I found a nifty utility for watching my battery usage, and I liked that better than the one in that Notification Area, so I tried to remove it.  At the time, I thought it worked fine, but I didn't notice that I had removed more than the battery icon.  Well, that's a mystery solved.

Thanks for your help, Reset3x.

Smokin'!!! Glad you got it fixed!!!

Peace

---

