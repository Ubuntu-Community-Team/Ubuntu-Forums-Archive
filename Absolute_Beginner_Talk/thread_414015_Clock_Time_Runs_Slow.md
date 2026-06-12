---
title: "Clock Time Runs Slow"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by rjjohnson4 on 2007-04-19
I'm new to Ubuntu...finally jumped on the bandwagon!

I just installed 7.04 and my clock time runs quite slow.  It runs about twice as slow as normal.  My computer is partitioned with XP/Vista as well.  The time works fine on those, but just not on Ubuntu.  What would be causing it to run slow?  What steps can I take to fix this?  Any help would be appreciated!

---

### Post by bwhite82 on 2007-04-19
Hi, one thing to check is to simply right click on the clock, and select "Adjust Date and Time" and check the box "Synchronize clock with internet servers." If for some reason you get an error message when you try doing that, install the following package:

> ntpdate

---

### Post by rjjohnson4 on 2007-04-19
Thanks for the help, but that's not the problem.  I can synchronize just fine, but then immediately the clock starts running slow again.  The time runs about twice as slow as normal speed.  Every time I synchronize, 10 minutes later it only says 5 minutes have gone by.  Really weird!  I'm guessing it's a processor problem or something, but was wondering if anyone knows anything?!?!

---

### Post by zurkog on 2007-05-29
I'm having the exact same problem now, has a resolution to this been found?

My situation - installed Ubuntu 7.04 on my Dell Dimension 4700 a few weeks ago (previously it had Fedora Core 4).  For the last several weeks, it's behaved flawlessly.  I get to work this morning, install updates that are waiting for me (don't remember what they were; is there a log file for update-manager?), and about half an hour later, I notice that the clock is about an hour out of sync.  I know for a fact that the time was correct when I arrived at work.

Playing around with it reveals that it runs about twice as slowly as before.  (in a terminal window: "while true; do date; sleep 1; done" runs twice as slowly as the same line on another box).  Yes, I can turn on "Keep Synchronized With Internet Servers", but that only synchronizes every so often.  For the time being, I turned off Auto-Sync, and am running "while true; do ntpdate ntp.ubuntu.org; sleep 60; done", but I'm sure they'll get tired of me hammering their ntp server pretty quickly.

Help!  Does anyone know what package might have messed up my CPU clock?  

Thanks,
Grant

---

### Post by joehack on 2007-06-04
Welcome to the club! I'm suffering the same problem. 
My system is a Dell Dimension 5000 (P4, 3 GHz). It's about 2 years old. 
On this system, I ran Gentoo, SuSE and unavoidable, WinXP. No problems with
the clock so far.

Jochen

---

### Post by jonward0690 on 2007-06-04
I remember someone having this same problem and a someone els posted back that the battery in the computer could be going bad or could have dust around it.I am just guessing but you might try cleaning the contacts to that littole battery and see maybe just maybe if that helps.I am not saying it will do anything cause it could be some software messing with the clock to.

---

### Post by joehack on 2007-06-04
I kept looping 

```
date && hwclock
```

for a while. It was obvious that the hardware clock was running fine, whereas the clock of Linux lagged behind dramatically.

Jochen

---

### Post by Newbie1Kenobi on 2007-06-04
Having the same problem here, too.  Running Ubuntu through VMWare.  I try to use the "Synchronize with Internet server" but I get a  "NTP support not installed"  I can't install NTP support.  I'm going 'round incircles here!!!  Please help!

---

### Post by jonward0690 on 2007-06-04
Well does it give you an error.

---

### Post by aktiwers on 2007-06-04
I had this problem in Edgy as well.. I never found a solution for it. A fresh install of Feisty fixed it though.

---

### Post by zurkog on 2007-06-06
Ahhh..  hwclock!  I hadn't known about that command.  Thanks, joehack!

Yes, my hardware clock is correct (within a few seconds of what ntpdate ntp.ubuntu.com returns.)

So I used hwclock to set my hardware clock to exact time, then whipped up a script that takes the output of 'hwclock' reformats it, and uses the "date" command to set the O/S clock ("date 060615322007.25", for example).  I run it in a screen session in the background.  Now I just need to turn it into a daemon that runs when the PC boots, and I'm set!  Talk about duct-tape and baling wire...

jonward: I'd agree with you, except for three things: this desktop is only about 18 months old (which is in the realm of CMOS batteries dying, but not likely), 'hwclock' returns the correct time, and last Tuesday morning, the O/S clock was correct.  30 minutes later, after I did a Software Update, it was an hour off, and falling farther behind.  It seems too coincidental for the battery to die just then.  But still possible.  It may be a couple of days before I am free enough to crack open the case, but I'll try cleaning off the contacts, and even break out a voltmeter to test the battery.  Thanks!

Newbie1Kenobi - Why can't you install NTP support?  What error is it giving you?

---

### Post by Newbie1Kenobi on 2007-06-06
[quote="zurkog"]Newbie1Kenobi - Why can't you install NTP support? What error is it giving you?[/quote]

That is the thing...I'm not getting any error messages any more.  I came across a possible fix and tried it.  I no longer get teh "NTP support is disabled.  Click to install NTP suppport" However the clock still runs slow.  I watched it and one second in Ubuntu=five seconds real time.  I am so confused...and it doesn't help I am a total "Newbie" as my name implies :wink:

---

### Post by Bremen Saki on 2007-06-07
Just chiming in on this - same thing here. I think I can safely discount CMOS batteries or anything else relating  to hardware faults. We just got in about 5 brand new HP DC7700 machines, and they all do the same thing.

The issue does not occur in Edgy - one machine was running happily for about a month, then started losing time after the upgrade. I've tried a clean reinstall of Feisty from the live CD as well, and we get the same thing. I haven't yet tried x86 Feisty for testing, they're all on the amd64 builds right now.

Running ntpdate hourly out of cron keeps it from getting too bad, but it's still odd that using ntpd won't work - we still lose about an hour a day.

Will report back after trying a 32-bit install and maybe downgrading the kernel.

[Ah, I found this.](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/102383) Same machine type as mine, so it's almost certainly it. No fix other than the 2.6.21-rc5 kernel, though.

---

### Post by zurkog on 2007-06-11
Good news, everyone!

I just came in to work this morning, downloaded the latest updates that were waiting for me, rebooted, and it's back to one second per second again.  So apparently whatever was in these latest updates (I need to start taking notes on exactly which packages are updated) fixed the "clock runs slow" problem.

Newbie1Kenobi: Don't sweat it.  It may not seem like it, but we were all there once, and had to rely upon the help of others.  Manuals can only go so far.  Download the latest updates, and see if it doesn't fix your clock problem (note- it may take ntp an hour or so to manually set the time).  You can manually update your clock by pulling up a terminal window (Applications -> Accessories -> Terminal), then typing in "sudo su" (without the quotes) and hitting enter.  You'll need to type in your password.  Once you get a root prompt (root@yourpcname) enter: "ntpdate ntp.ubuntu.com".  That will go out to Ubuntu's NTP server, grab the exact time, and adjust your clock.  Once that's done, and once you've applied the latest updates, hopefully it won't slip further out of sync again.

---

### Post by Newbie1Kenobi on 2007-06-11
Thanks for that info...but I think I solved the problem...while working on another.  I'm running Ubuntu through VMWare in Windows Vista and there was a game that was seriously lagging.  I installed the dual-core optimizer from AMD, rebooted and time has kept sync ever since.  I had d/l some updates but it was significantly before installing the optimizer.  After installing the optimizer the time synced when I first booted into Ubuntu and has stayed synced since.  Odd, but working.  Anybosy else run into this?

---

### Post by kevmartin on 2007-07-14
I have this problem too - it started after some issues caused with a partition resize by gparted some weeks ago that I still havent been able to solve.  It did go away at one point, and I thought Linux had just fixed itself.   But it came back and is still happening.  I have all the latest updates (except for some OpenOffice ones that are waiting there for me now.  I tried both manual synchronising and automatically synchronising.  No good.

Seems from this thread that there are enough people with this issue to start considering it a real bug maybe.

Oh, an extra note - the clock corrects itself on reboot, then starts losing time again.

---

### Post by psb6m on 2007-07-20
I ran into this problem and found the solution with a little research. It is a bug in the kernel, and the bug is fixed in the next kernel release--but Ubuntu people who have experienced the problem will have to wait till October. In the meantime, do this:

1. The kernel can use one of several timers. to check which yours is using: Open a terminal and become root (sudo -s). Type

```
cat /sys/devices/system/clocksource/clocksource0/current_clocksource
```

The result identifies the clocksource that has gone wrong.

2. Now find out what other clocksources are available:

```
cat /sys/devices/system/clocksource/clocksource0/available_clocksource
```

You'll see a list of words (e.g. acpi_pm hpet jiffies).

3. Test an alternative clocksource, e.g.

```
echo "hpet"> /sys/devices/system/clocksource/clocksource0/current_clocksource
```

You should notice an immediate speedup in the system clock. If so, go on:

4. We'll add a kernel parameter to make the kernel use a workable clocksource.

```
cd /boot/grub
nano menu.lst
```

Scroll down to the first menu item (a group of lines beginning "title root kernel" etc.). At the end of the "kernel" line (which shows the command line that starts the kernel), add a "clocksource" parameter specifying the clocksource that worked for you in step 3 above. For example, change

```
kernel  /vmlinuz-2.6.20-16-lowlatency root=UUID=030313ac-ece9-49bd-8c39-
5ff6323c34a7 ro single
```

to

```
kernel  /vmlinuz-2.6.20-16-lowlatency root=UUID=030313ac-ece9-49bd-8c39-
5ff6323c34a7 ro single clocksource=hpet
```

5. Save the file and
```
reboot
```
Everything should work correctly now!

---

### Post by joehack on 2007-07-21
That was it! Thanks for your help!!!

Regards,
Jochen

---

### Post by kevmartin on 2007-09-11
> **joehack said:**
> That was it! Thanks for your help!!!

Regards,
Jochen

It solved the issue for me too - months ago when it was posted.  Yesterday, the problem suddenly started again for no apparent reason - except possibly updates to some files from the auto-updater system.  Fortunately I was able to track down this thread and solve it again - but not before I was unwittingly an hour late for work!  Thanks (twice) for the solution.

---

