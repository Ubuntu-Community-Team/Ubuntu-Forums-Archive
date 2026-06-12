---
title: "Does a crash in Ubuntu cause any lasting harm?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by bguy on 2006-11-28
Hi,
I was viewing an E Hallmark birthday card when suddenly the computer froze up.  I had to pull the electricity cord as Ubuntu was non-responsive.  Does a crash like this cause the software any harm?
THanks,
B
PS I've been a Ubuntu user since 6.06 now 6.1 and am utterly thrilled with it.  Automatix was the development that finally allowed me to switch over from windows on a permanent basis as i was not technically savvy enough to install all the software (java, flash, media players etc...,) that i require.  Thanks to everyone who contributes to this wonderful project!!

---

### Post by KingBahamut on 2006-11-28
It could possibly cause issues, but normal inode checks for drive inconsistencies would address this issue normally (youll see it as a text bit at boot up that says something like - Check Forced). This process called fsck. 

[http://www.die.net/doc/linux/man/man8/fsck.8.html](http://www.die.net/doc/linux/man/man8/fsck.8.html)

---

### Post by bguy on 2006-11-28
thanks

---

### Post by insane_alien on 2006-11-28
wow a crash in ubuntu. i mean i've seen it before but the hardware was more than a tad shoddy which caused it.

---

### Post by livinginx on 2006-11-28
Next time, instead of pulling the power cord from the computer, try either a) holding the power button in for 4-7 seconds or b) hitting the reset button on the tower.

When power is suddenly lost to a hard drive, it can tend to cause problems as the heads were not parked.  That is why whenever possible, you should use the proper shutdown procedures.

---

### Post by mdsmedia on 2006-11-28
> **insane_alien said:**
> wow a crash in ubuntu. i mean i've seen it before but the hardware was more than a tad shoddy which caused it.It sounds more like a software glitch than an Ubuntu crash as such.

I run Firefox, Thunderbird, Kontact and OpenOffice. Sometimes when a (unknown) combination of these is open and say I try to run a PPT presentation in OOo the cpu light will be constantly on, and mouse movements are frozen or sketchy at best.

I've found, generally, ctrl-alt-F1(through F6), then in the terminal, login and use "top" command. Then kill one or more of the "offending" packages and it usually brings back a clean session.

It sometimes takes a while to get through all of that before killing the apps as cpu seems to be about 100% occupied, but if you're patient you shouldn't generally need to power down.

As was said though, pulling the power cord is NEVER necessary and is NOT a good idea. I'm running a notebook installation, so pulling the powercord won't do me any good anyway as the battery takes over, so obviously it's not necessary and there are better methods of powering down that have already been mentioned.

---

### Post by bguy on 2006-11-28
Hi,
I have heard that crashes in linux are fairly rare but they have happened to me on occasion though probably less frequently than what i experienced using windows xp.  I have on occasion wondered if there was some kind of hardware problem with my system as others seem to experience crashes less frequently.  

Now that you mention it i think i have in the been able to power off my computer after a freeze by holding down the power button.  I didn't realize that this was less harmful to the computer than pulling the plug.
Thanks everyone,
Take care,
B

---

### Post by Sef on 2006-11-28
> When power is suddenly lost to a hard drive, it can tend to cause problems as the heads were not parked. 

A transformer blew near here and lost power for about 5 seconds.  Upon booting up, I found that I had lost my swap.  Rebooted with [GParted]("http://gparted.sourceforge.net/livecd.php"), and reinstalled my swap.  

It was not hard for me, but for someone who doesn't know about partioning, it probably would have been difficult without reinstalling.

---

### Post by 3rdalbum on 2006-11-28
I don't know if holding down the power button is less damaging than pulling the plug out.

But here's something worth trying. If/when you get your next full crash, press:

Alt-Printscreen-S to sync data on your drives. Wait a few seconds, then:
Alt-Printscreen-U to unmount your drives and remount them read-only. Then:
Alt-Printscreen-B to reboot.

If you don't see a "Print Screen" or "Prt Scr" key on your keyboard, it might be labelled "SysRq". Those key combinations should work as long as the kernel is still running, and they will minimise the possibility of data loss.

---

### Post by Zaen on 2006-11-28
In my experience, cutting the power like that is a hit and miss thing. Most of the time it won't damage anything. sometimes it causes errors, and other time it kills the install. I've had good luck just hitting the power button, but a lot of the above ideas are much better than that. if you're now nervous about cutting power, you could just try waiting for it to respond, sometimes the system inexplicably gets bogged down. hope it doesn't happen again.

---

### Post by livinginx on 2006-11-29
> **3rdalbum said:**
> I don't know if holding down the power button is less damaging than pulling the plug out.

Do you ever hear that little click coming from the drives area of the tower after holding the power button in right before the tower loses all power?  When you do that, it actually parks the heads of the HDD.

I lost a laptop hard drive inside a Creative MP3 player when my batteries died, beyond basic partion repair.  It would need an actual repair.  And I have corrupted many-a-windows partitions by doing hard shutdowns.

You can still corrupt your data by not cleanly unmounting your system, but no physical damage if you use the reset/hold power button in.

---

### Post by P235 on 2006-12-09
I'm definitely going to give 3rd's advice a try the next time my laptop freezes up.

---

