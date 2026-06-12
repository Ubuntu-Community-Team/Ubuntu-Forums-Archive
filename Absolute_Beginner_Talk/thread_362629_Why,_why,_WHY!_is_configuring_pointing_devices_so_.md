---
title: "Why, why, WHY! is configuring pointing devices so darn hard!?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-02-15
Most of the past three weeks, and thanks in no small way to this forum, I've been mostly satisfied with Ubuntu Linux 6.01.  A few teeth-gnashing digressions notwithstanding, my video adaptor now has its proper driver, I've learned how to make USB drives accessible using the command line (short answer -- use the command line to mount them), and I've gotten many -- but NOT ALL -- of my preferences set up.  

For the most part, Ubuntu Linux looks pretty "Dapper", indeed.

BUT today, after four hours of experimentation, some of which rendered Linux unbootable (thank Tux for recovery mode), I STILL can't get any but the most basic functionality of my Logitech Marble Mouse to work.

Oh yes, I've been all over the Ubuntu Forums and  the Internet collecting what is evidently incorrect, or at best ambiguous, information on the subject.  For example:

[http://ubuntuforums.org/showthread.php?t=169423](http://ubuntuforums.org/showthread.php?t=169423)

and...

[http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441)

These are great posts with lots of detail.  Unfortunately, they don't work.  Not just for me, mind you, but quite evidently for other submitters to those very threads.

So now I ask: Why, why, WHY in the twenty-first century is _anyone_ required to experimentally edit *xorg.conf* or install supplemental programs, as recommended in the second of the cited forum threads, to properly configure a multi-button mouse!? 

There are many improvements in Ubuntu that make it more usable than earlier distributions I've tried and abandoned.  But golly, please look at the many, many (MANY!) forum threads asking how to configure mice and trackballs.  Please note, too, how many of these threads eventually slink quietly off into the Great Unresolved.

With this in mind, and especially with four hours of unsuccessful research and  experimentation freshly behind me, is it conceivable that one or more Ubuntu boffins can figure out some way to make it easier for *everyone and anyone* to configure a multi-button pointing device **_*without*_** having to experimentally hand-edit *xorg.conf*?

Just asking...

Cheers, thanks for listening, and hope this eventually helps,
Ric
SFO

P.S. to Forum moderator: My sincere apologies in advance if I've submitted this post to the wrong topic category or forum section.

---

### Post by ramjet_1953 on 2007-02-15
I can understand your frustration, but I think that your ire is mis-directed.
Don't forget that Ubuntu and every other Linux distro is an operating system only.

Unfortunately, in the real world, hardware manufacturers often do not "open source" the drivers for their hardware. The reason that they often give for this is because if they did this, the actual hardware design would then be available to their competitors.

In trying to use a Logitech mouse, you have chosen a company that does not support the open source community in any way. It is the same story with their web cams. They have heaps of different models, some of which work under Linux, some don't.

To reverse-engineer a driver for a piece of hardware is extremely difficult and requires a great amount of time and resources. I think that it is amazing that so many drivers have been developed for hardware that was previously locked-in to Microsoft OS's. And all done voluntarily by dedicated hackers that have embraced the philosophy of open source.

So, instead of complaining that your mouse doesn't work with Ubuntu, accept the fact that manufacturers of some hardware products have probably done deals with Microsft and deliberately make it difficult or impossible to use it under any OS other than windows.

Vent your frustration at them, not at Linux.

Regards,
Roger :cool:

---

### Post by Phrawm48 on 2007-02-15
> Unfortunately, in the real world, hardware manufacturers often do not "open source" the drivers for their hardware.

As best I can tell, _none_ of the many (too many!) threads I've found that discuss pointing devices talk about device _drivers_.  Rather they suggest (often contradicting each other in the process) how to experimentally hand-edit *xorg.conf*.

My point remains, then, that experimentally hand-editing *xorg.conf* to configure mouse behaviors has demonstrably not worked for many would-be users.  (It certainly hasn't worked for me).

As such, I still strongly believe that there's a marvelous opportunity to bring another aspect of Linux usability a bit further along.  To wit, some integrated GUI mechanism that assists the user by:

[LIST]
[*]Detecting the capabilities of a given pointing device, similarly to *xev*.

[*]Guiding the user in assembling those detected capabilities into a sort of interim configuration mode, similar to the way that changing screen resolution temporarily applies new settings so the user can decide whether or not to commit them to the system configuration.

[*]Assisting the user in committing a pointing device's successfully updated configuration to the system configuration, ala modifying *xorg.conf*.
[/LIST]

Again, note that none of these operations have anything to do with drivers (a.k.a. binary executables), per se.

It may be that at some point in the future, I'll understand enough about *xorg.conf*'s mouse section that I'll be able to integrate those more-or-less existing capabilities into some sort of unified "mouse configuration tool."

Note, however, that it'll be some time until I'll be at that level.  So perhaps there's a marvelous opportunity for an Ubuntu boffin to make a truly useful adddition to Ubuntu's notably improved ease-of-use...

Cheers & hope this helps,
Ric
SFO

---

### Post by ramjet_1953 on 2007-02-16
Yes, I know that the Linux world is full of enthusiasts that love the command line.
I don't claim to be a command line expert at all, but in many instances, it provides the most powerful way to tailor a Linux system

Herein lies a fundamental difference between Linux and Windows. If you have the time to really "get under the hood" Linux can be totally tailored to your individual needs. Right down to making your own distribution. The tools are freely available. However, Windows is pretty much locked as far as the user is concerned. You can change cosmetic things, but to really tailor it from the kernel up is not an option.

Nevertheless, I have searched around and found this GUI tool for modifying your xorg.conf file.

I hope it is what you are looking for.
Just right click on it in Nautilis File Manager and choose to install it with the debi package manager.

[COLOR="Red"]Be warned, though that you must ALWAYS back up the original file first.[/COLOR]

Regards,
Roger 8-)

---

### Post by Phrawm48 on 2007-02-16
Sawat dee khrap khun Roger:

Lamentably, despite multiple attempts and strategies, *xorg-edit_06.10.12-1tle1_i386.deb* could not be opened.  All the programs I used indicated the file had become corrupted...

Cheers & "khap khun khrap",
Ric
SFO

---

### Post by ramjet_1953 on 2007-02-16
Let's try again!

Roger:cool:

---

### Post by Warcattle on 2007-02-16
There wouldn't happen to be an AMD64 version of this fix, would there? or does it matter?

I have a feeling it could really come in handy.... (I'm about to install Ubuntu 6.06)

---

### Post by Phrawm48 on 2007-02-16
Roger:

Regarding the second attempt to transmit this file as a forum attachment: Nope.

The Debian package manager responds exactly as it did to the first file -- unable to open, possibly corrupted.  I also tried the archive tool with exactly the same results.

Cheers & thanks,
Ric
SFO

---

