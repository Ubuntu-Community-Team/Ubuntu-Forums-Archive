---
title: "Dual Monitors on Gutsy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-10-19
I installed gutsy on my Dell Inspiron 6000 laptop with my Samsung SyncMaster 151v plugged in. Gutsy automatically set it up as a clone display of my laptop screen. In an effort to change it to an extended desktop, I went to System->Administration->Screens and Graphics. To my surprise, it showed my laptop screen as the default screen, and had the second screen marked as 'disabled'. Since it is disabled, I can not change it to an extended desktop. Is there any other way to do this?

---

### Post by Qwerty_ on 2007-10-19
Your not able to click the secondary monitor button?

---

### Post by jown on 2007-10-19
Hey, can u switch the state of the second monitor with a key combination? like FN+F4 or something?

---

### Post by nhandler on 2007-10-19
All I can do is swap which monitor is the default, and which monitor is "disabled". However, since it is a clone display, it doesn't really change anything.

Well, my F8 key says, "CRT/LCD" on it. But if I hit Fn+F8, it just makes my second monitor go black for a second. It then turns back on, still cloning my laptop monitor.

---

### Post by tolremeno on 2007-10-19
The second monitor feature doesn't seem to work very well. We had a [discussion]("http://ubuntuforums.org/showthread.php?t=573484&highlight=dual+monitors%3F") of it over on the dev forum, where we got it kinda working. Or if you have nvidia there's a tool for it (twinview?).

---

### Post by Seinfeld on 2007-11-03
Hi,

I have Gutsy on my desktop with an nVidia 7200 GS with a dual head digital (DVI) and Analog (VGA). 
 I have my nice LCD screen hooked to the digital (DVI) output but when I hook another VGA screen
so when I go System>Administration>Screen and Graphics to set the screens, it is impossible to let the DVI to be the default. The analog insists to be the default screen.  
Must the analog output of the card be the default screen ?? This does not make sense.

 Help ??

Thanks

---

### Post by .evan on 2007-11-03
> **Cheater said:**
> All I can do is swap which monitor is the default, and which monitor is "disabled". However, since it is a clone display, it doesn't really change anything.

Well, my F8 key says, "CRT/LCD" on it. But if I hit Fn+F8, it just makes my second monitor go black for a second. It then turns back on, still cloning my laptop monitor.
I've had the same problem.  The GUI screens and graphics util didn't work as promised.

By default, I had the same issue as you - where I could only switch the default monitor back and forth.  The GUI tool recognized that I had 2 monitors, but refused to let me enable both simultaneously.

I had to tweak the xorg.conf file and re-boot, which caused both monitors to show up in the screens and graphics panel, but the monitor names were incorrect (it kept wanting to use "plug and play" even though I continually explicitly set it to samsung: sync master 206 bw).

no matter what I did, rebooting always wiped out previous settings and I got the " you must run in limited graphics mode " message.  so I'd boot in limited mode, fix things again, reboot and ... well, now I forget what would happen at that point.

regardless, the problem always returned; the settings were always overwritten; I was always forced to boot in limited graphics mode after making changes.

see my blog for more details:
[http://hobbylobby.wordpress.com/](http://hobbylobby.wordpress.com/)

---

### Post by wombat20 on 2007-11-11
I had trouble with this after I downloaded and installed the offical Nvidia driver from their website.

In the end I backed up my home directory and reinstalled. Then I used the Envy script to set everything up how I wanted it. So now I have two monitors running nicely with Nvidia drivers. No desktop effects, but doesn't matter.

---

