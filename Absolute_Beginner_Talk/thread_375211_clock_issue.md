---
title: "clock issue"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by fatdan666 on 2007-03-03
Not that big of an issue but just weird.  

Everytime I log in to Ubuntu the clock is off by 5 hours.  I can fix it by changing the, I think it's ACT or ATC box (I'm at work on XP and I can't remember).  

For example, I log on at noon and it says 5:00.  I *check* that box.  Next time I log on, it's off by 5 hours again.  This time I *uncheck* the box, and it fixes.  

The whole check/uncheck thing baffles me.  I would think that once it's a certain way, it would stay.  

Any ideas?  :confused: 

Thanks in advance!

---

### Post by teaker1s on 2007-03-03
check bios clock time and ubuntu settings are same time:KS

---

### Post by Patrick K on 2007-03-03
Often a clock error is a sign if the cmos battery on the way out. The OS gets it's time from the system clock. I suggest rebooting, entering the BIOS setup and checking the clock there. If is it off then the battery is a very likely suspect. If it is correct and the OS is off, I'm not sure what you can do.

---

### Post by teaker1s on 2007-03-03
as above 
also check time zone is correct in ubuntu
other than that file a bug

---

### Post by fatdan666 on 2007-03-03
> **teaker1s said:**
> check bios clock time and ubuntu settings are same time:KS

Will try when I get home.   Thanks!

---

### Post by fatdan666 on 2007-03-03
> **teaker1s said:**
> as above 
also check time zone is correct in ubuntu
other than that file a bug

Time zone is correct.  I'll check BIOS when i get home and go from there.  Thanks guys.

---

### Post by steve.horsley on 2007-03-03
Do you dual boot? Windows always sets the hardware clock to local time. Unix normally expects the hardware clock to be on UTC/GMT. If your problem is that windows keeps setting the clock to local time, you could set Linux for the Europe/London timezone,
or set windows to use UTC hardware clock:
[http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx)
or set Ubuntu to use local time hardware clock by setting **UTC=no** in /etc/default/rcS.

---

### Post by Apostata on 2007-03-06
This is definitely one of my all-time top bugs in Ubuntu/Kubuntu that never gets talked about.

Similar report [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=135214&highlight=UTC+timezone").

Tried everything: BIOS, tzsetup/tzselect, and I'm not dual-booting either. The fact that we're even having this conversation (ie an OS that doesn't tell the correct time and incorrectly timestamps all incoming email and new files) is ridiculous in 2007.

---

### Post by Mozgus on 2007-04-21
> **Apostata said:**
> This is definitely one of my all-time top bugs in Ubuntu/Kubuntu that never gets talked about.

Similar report [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=135214&highlight=UTC+timezone").

Tried everything: BIOS, tzsetup/tzselect, and I'm not dual-booting either. The fact that we're even having this conversation (ie an OS that doesn't tell the correct time and incorrectly timestamps all incoming email and new files) is ridiculous in 2007.

Quoted for truth. One of the 50 reasons why I just cant move from windows to ubuntu.

---

### Post by oilchangeguy on 2007-04-21
just make sure both os's are set up update from the internet time server. that should take care of the problem. (it did for me)

---

### Post by Toxicity999 on 2007-04-21
Yea really, if you can't actually fix the problem, just use ntp to set the clock to a server time every boot (if you have an always on deal with your connection) otherwise, just do it everytime you get online since boot. though not ideal it's not so big of an inconvenience if you can't fix it =]

---

### Post by Apostata on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/93170](https://launchpad.net/bugs/93170) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **Toxicity999 said:**
> Yea really, if you can't actually fix the problem, just use ntp to set the clock to a server time every boot (if you have an always on deal with your connection) otherwise, just do it everytime you get online since boot. though not ideal it's not so big of an inconvenience if you can't fix it =]

On my system, it makes no difference whether I'm syncing to an NTP or not - whatever I do, whether I change my location from Kansas to Khartoum, I'm stuck in GMT time.

---

### Post by Aetherius on 2007-04-23
Just move to the GMT zone, make life easier for ya. :) 

Just like to say that i've never actually been subjected to this bug, is it hardware specific?

---

### Post by Apostata on 2007-04-23
> **Aetherius said:**
> Just move to the GMT zone, make life easier for ya. :) 

Just like to say that i've never actually been subjected to this bug, is it hardware specific?

Yes, a subtle advantage to having your clock five hours ahead of time is that people think I'm working really really late hours.

Re: hardware, I've heard nothing that would suggest a specific setup. I'm running on a Biostar 6100-939 m'board, fyi.

---

### Post by Bobcatben on 2007-04-23
in kubuntu you could tell it the system clock was local time instead of gmt, is that possible in ubuntu?

---

### Post by Apostata on 2007-04-25
> **Bobcatben said:**
> in kubuntu you could tell it the system clock was local time instead of gmt, is that possible in ubuntu?

This is true - thankfully I can have it display the local time. Unfortunately, this doesn't extend to apps which time-stamp things (ie. email).

---

### Post by Bobcatben on 2007-04-25
it displays the local time, i just want it to stop setting my bios clock to gmt, cause i boot back into windows and my clock is 5hrs fast.

---

