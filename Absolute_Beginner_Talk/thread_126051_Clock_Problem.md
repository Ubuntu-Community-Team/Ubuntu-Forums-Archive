---
title: "Clock Problem"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Hygelac on 2006-02-05
I'm having a problem with the automatic clock synchronization.  I was setting up a wireless network with two Kubuntu Breezy notebooks (amongst others) on it today.  This worked fine (\\:D/), and for the first time these computers can do their boot-time clock sync.  They are both set to the timezone where Montréal is (GMT - 0500 I think) but one syncs to Greenwich no matter what timezone I set it to, meaning that the clock always reads five hours ahead of now.  I know there are worse problems than this, but does anyone know what is going on?  The computer is an HP zv6000 running in 64-bit, if that helps.

---

### Post by bscbrit on 2006-02-05
I'm not sure, but I suspect that you've set one computer with the clock storing GMT and software correcting it for display, and the other set for storing local time.

Right click on your time display on the top panel of the desktop and see if you have UTC selected on one and not on the other.

Mind you, this is mostly guesswork :p

---

### Post by Hygelac on 2006-02-05
When I go to adjust the time/date settings it simultaneously says both UTC and «America/Montreal», which makes no sense to me.  When I tell it to be somewhere else, and then restore it to Montréal, it reads EST and the proper time appears on the display in the window.  However, the time on the actual clock (on the panel) never changes and when I close and reopen the time/date adjustment window the UTC is back.

The other computer said EST and «No timezone».  I changed «No timezone» to «America/Montreal» and now it has the exact same problem with only displaying UTC.  #-o

So, does that help?

By the way, your help with someone in a post on wireless card configuration helped me a lot; so thanks for that! :D

---

### Post by Hygelac on 2006-02-06
I figured-out something else today.  The clock display was set to show "Local Time," which I guess is what it insisted would be UTC no matter what I would tell it.  When I tell it to display in the 'distant' Montréal timezone, it does (finally), but now it has a large annoying label I cannot get rid of in any apparent clock settings.

Is there one of those powerful little text files somewhere (like xorg.conf) that controls the clock?  I'm thinking that I could tell it EST there.  I ask because of a bug with kcontrol that causes changes to the gateway entry not to be recorded in the /etc/network/interfaces file (I'm wondering if there is a similar bug that is preventing me from changing UTC to EST as my local timezone).  Does anyone know? :-k

---

### Post by bscbrit on 2006-02-07
Well, there is a file called /etc/timezone which contains just that - the timezone.  E.g. mine says Europe/Madrid.  I suppose that editing this would do what you expect it to.   But the problem is that your hardware clock is set to store UTC on one machine and the local timezone on the other.  I'm not sure how to change that on a running computer, but I'm looking into it.  It is probably very simple but I haven't stumbled upon it yet.

---

### Post by bscbrit on 2006-02-07
Right click on the clock and select Preferences achieves the same thing but, on my machine, does NOT appear to change the hardware clock.

---

### Post by Hygelac on 2006-02-07
Thanks for what you've done so far.  In /etc/timezone it does say "America/Montreal," but as you explained that is not where the problem is.

If push comes to shove I could just reset my watch to UTC. :rolleyes:

---

### Post by bscbrit on 2006-02-07
Try these links:

[http://www.linuxsa.org.au/tips/time.html](http://www.linuxsa.org.au/tips/time.html)

[http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html](http://www.debian.org/doc/manuals/system-administrator/ch-sysadmin-time.html)

[http://www.tldp.org/LDP/sag/html/showing-setting-time.html](http://www.tldp.org/LDP/sag/html/showing-setting-time.html)

Good Luck!

---

### Post by bscbrit on 2006-02-07
Also 

'man clock' 

or

'man hwclock'

I hope that this solves your problem or, more accurately, gives you enough information to let you solve your problem.  Good Luck!

---

### Post by Hygelac on 2006-02-07
Thanks, that's a lot of stuff.  I'll take a look and see what I can figure-out.

---

### Post by tiodan on 2006-02-18
i ran into this same problem on a new install, and just fixed it. look in /usr/share/zoneinfo to see if there's a link in there called /usr/share/zoneinfo/localtime. it should exist and point to /etc/localtime. the problem i had was that /etc/localtime didn't exist (i guess the system failed to create it), and i rectified it by typing 

'sudo ln -s /usr/share/zoneinfo/US/Pacific /etc/localtime'

at the command line. of course you should substitute your local zone for /US/Pacific.

---

### Post by bscbrit on 2006-02-18
Thanks, Tiodan.

---

### Post by Hygelac on 2006-02-18
This is interesting; I have neither the /etc/localtime file nor the link to it in /usr/share/zoneinfo... :-k 

I haven't done much to fix the clock yet because I've been horribly busy.  This new week will be full too, but it'll be fine for a while after that.  I'll take a look at the clock then and tell you all how it went. ;)

---

### Post by jimbren on 2006-03-08
I realize this is an old issue, but I found an easy fix for anyone who has this problem in the future.  run time-admin and set the timezone.

---

### Post by Hygelac on 2006-03-08
I still haven't had the time to fix that clock, but your assistance is still appreciated.  Time-admin does not seem to exist ("Command not found"); is it a GNOME thing?

---

### Post by doundounba on 2006-03-17
Hygelac, did you fix this?  FWIW, I just ran into the same problem.  Everything had been just fine ever since installed until I decided my system was a few minutes ahead this morning and tried to adjust the clock.  Things went downhill from there. :-?  All of a sudden it started displaying the UTC time and nothing I've been able to do changes that.  Like you, I can ask the clock to Show Timezone -> America/Montreal, but other things that display time (like a Superkaramba clock applet) remain broken, so I'd like to get back to my original starting point where everything was fine.

BTW, someone in another thread suggested: "Open terminal and run 'sudo gedit /etc/default/rcS'. Now find the line with 'UTC=yes' and change that to 'UTC=no'. Save and restart your machine. Set the time and timezone if you need and your problem is gone".  I did that, to no avail. I've also tried tzsetup without it helping (it correctly shows me as in timezone America/Montreal).   Oh yeah, as you can see I'm also in Montréal, so we could go for coffee if we can agree on a time... ;)

Currently trying to see if I can figure out how to use "date" to set the timezone from the CLI...  This is pretty annoying. :evil:

---

### Post by Hygelac on 2006-03-18
I just fixed it!  Doundouba, you mentioned 'tzsetup' correctly telling you that you were in 'America/Montreal'?  Did you tell it to change timezone anyway?  I did that, telling it from tzsetup that I was in Montréal, and now it displays the correct local time as the local time instead of UTC as the alleged local time.  \\:D/  Also, the thing under KDE clock settings says EST instead of UTC again.

---

### Post by doundounba on 2006-03-19
[QUOTE=Hygelac]I just fixed it!  Doundouba, you mentioned 'tzsetup' correctly telling you that you were in 'America/Montreal'?  Did you tell it to change timezone anyway?[/QUOTE]

Bingo!  Thanks Hygelac.  I'm also back to normal.  \\:D/

---

