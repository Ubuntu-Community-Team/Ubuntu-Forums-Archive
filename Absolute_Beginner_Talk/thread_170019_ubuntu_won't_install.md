---
title: "ubuntu won't install"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by niteshade on 2006-05-03
hi there

trying to install ubuntu 5.10 Breezy on an old grey box... Pentium II with a 4.3GB drive.  Gets up to the boot loader install, then chokes.  Fatal exception errors.

My gut tells me it's either that the installer needs to download stuff from the internet (the box relies on wifi, which I plan to configure after I install Ubuntu), or that I don't have enough disk space.

I'm a Mac user in general, and am a little unfamiliar with Intel boxen.  Is this a familiar problem?

thanks

---

### Post by nanotube on 2006-05-03
hmm, well, the first guess is always that you might have a bad cd. try burning another one at a lower speed, and see if errors persist.

---

### Post by tribaal on 2006-05-03
Also make sure you have enough RAM for it... I cannot remember the minimals for that on top of my head, but it's like 256Mb for a desktop install probably. 

That is, it you want to run it kind of smoothly of course ;)

- trib'

---

### Post by Ptero-4 on 2006-05-03
Minimal RAM is 128MB.

---

### Post by Digidiz on 2006-05-03
lemme see have you put the install option linux acpi=false at the begining? because p2 computers dont have acpi management

---

### Post by niteshade on 2006-05-04
acpi?  Hmmm... I have no idea what that is.

And which partitioning scheme should I use?  This computer will have only Linux.

Oh, and I've already tried burning a new CD... same thing both times.  The CD verifies just fine with the built-in Linux installer and Toast on my Mac.

Also, I'm fairly sure I have 256MB RAM on the machine.

---

### Post by Digidiz on 2006-05-05
use the linux default then. acpi is **[SIZE=4]Advanced Configuration & Power Interface[/SIZE]**
**[SIZE=4][/SIZE]** 
[SIZE=4]it does exactly what it says on the tin[/SIZE]

---

### Post by niteshade on 2006-05-05
I'm going to try another install in an hour or so.  Is the acpi option available in the automatic installer?  I don't recall choosing it, but I'll keep more awake this time.

So what does acpi have to do with the boot loader?  Does the boot loader have specific power requirements?

Please pardon my ignorance... I looked for install troubleshooting/FAQs but haven't found any useful ones.  I'm not tech ignorant, but in using Macs I've been blissfully unaware of most hardware issues.  Would I do better to find an older Linux flavor, Debian perhaps, that wouldn't rely on post-PII hardware?

Eventually this box will become a wifi server, so it needs to have drivers for the wifi card installed, and use modern networking software.

---

### Post by nanotube on 2006-05-05
to try installing without acpi, when you boot from the install cd, at the point where there is a "boot:" prompt, rather than just hitting enter for defaults, type the following:
```
linux acpi=off
```
and see if it installs then.

---

### Post by niteshade on 2006-05-05
I tried installing again, this time with the "linux acpi=off" option specified, but I got the same exceptions as before.  These are:

```
[!!] Install the base system
Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
Check /target/var/log/bootstrap.log for details.
<Go Back> <Continue>
```

```
[!!] Install the base system
Installation step failed
An installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Install the base system
<Continue>
```

Hitting <Continue> brings me back to the Ubuntu installer main menu.

I looked in /target/var/log/ but didn't see any file named bootstrap.log.  Not that the built-in shell has vi, pico or emacs installed to view it anyways.

Any ideas?  Do I need network access for this to work?

---

### Post by nanotube on 2006-05-05
hmm, well, check this long thread for more info:
[http://www.ubuntuforums.org/archive/index.php/t-75430.html](http://www.ubuntuforums.org/archive/index.php/t-75430.html)
it seems that a LOT of people had this problem and got it solved by burning another cd at a slower speed. you should try that first.
if that does not work either, then try booting with 
```
linux acpi=off noapic nolapic
```
and see if that gets you through. but still, the first thing to try, as i recommended in the beginning, is to burn another cd at a slower speed.

---

