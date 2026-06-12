---
title: "Installation Process Reporting"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by brit0n on 2007-03-21
OK, this will seem a little odd to those of you with massive budgets, but with all due respect, on our network, we try new things out on older machines.

1. The installation process has some points at which it does not make things clear - for instance, if you have NEVER used Linux before, but read the blurb about Ubuntu, you would think you could install it without problem and without reading the forums first. So when you get to the partitions, however much you knew before, you would not realise that you have to jump from DOS/Windows etc (actually, from BIOS too) using HD0 and HD1 (for example) to a=0 and b=1 etc. It would help if the partition part of the install made this clear - it would only take a few words at the top or bottom and users who knew it would simply ignore it.

2. When the installation process ends, there is an Ubuntu logo and a small bar. Touch some keys (like Ctrl-Alt-Del for instance) and the bar will re-form, grow, shrink and then sit there on the right again. After my second attempt to install (after forcing a power off and then re-downloading, MD5 checksum and burn another CD to be sure I had the whole thing), it was late at night and I had the lights off. I then noticed a small blue patch below the orange bar. I got a magnifying glass and found it was some WORDS! "Remove CD, close tray if open and press Enter to continue" or similar.

Now with all due respects, slick though the install may be (very slow, but slick to look at), if a 15" CRT display on maximum brightness doesn't show the instructions at the very end of the installation process, it does NOT instill one with confidence any more than thinking the installation process had hung.

So I thought the designers might like to know that SOMETHING BRIGHT and BIG ENOUGH TO SEE (640x480 used to be standard for installations until the video adapter and monitor were identified and drivers installed but 800x600 would have been enough on an installation "exit" screen). If you don't want it tried out, OK. But if you do, where on EARTH do we report these things? It aint a bug - it's a FEATURE!

There are a lot more like it which if carefully reported as feedback to whoever designs the installation would help to get more people who never used Linux GUI distributions before to bear with it. So where do we feedback this stuff?

---

### Post by Kateikyoushi on 2007-03-21
Thanks for your feedback, some of these could be reported on as bugs like small text in point 2.
There are teams who work on better guides and to help new users, you could tell them your opinion here. [LINK]("http://ubuntuforums.org/showthread.php?t=376521")
A team is being made who work on communicating forum users opinion to the devs.

---

### Post by brit0n on 2007-03-22
Thanks. I already posted something on the Beginner's forum and got some good stuff back, but that forum is daunting when you see what is in the stickies - even the TITLES make me wonder whether I need a dictionary (and trust me, I aint non-technical - just not Linux oriented .... yet).

There is a whole HOST of stuff which the installation team could consider, but I am not sure I can spell it out in ways which don't produce answers like "ludicrous" (one answer on the Beginners Forum which I got from someone who appears to know rather less than I do about booting/systems in general).

I avoided bug reporting it when I saw the instructions about what NOT to post as bugs.

Thanks.

---

### Post by seshomaru samma on 2007-03-22
brit0n
this is a support forum for people with technical problem running ubuntu. all the people providing the answers are volunteers . the ubuntu developers dont write on this forum. what you get here  are only users who take time to answer other people's questions and who will be more than happy to assist you with any problem regarding the running and maintaining linux. 
ubuntu is a great OS but it still needs improvement - if you know how to programme you can help by modifying the code yourself. you can also help by creating artwork or writing manuels.
welcome to the forum.

---

### Post by brit0n on 2007-03-23
Thanks for the idea. Actually, I installed Ubuntu when I realised on another forum that the people responding to the ideas I put in, who were also developing the software, were stuck in the box. So I needed to get up to date on Linux (last time I studied it at all it wasn't a GUI) in order to help them improve the software.

Once I have sorted THAT out and then used that software for the solution to the Windows problem which I loaded it for and then fed that back to the Windows users (which will encourage MANY MORE of them to get a distro of Linux alongside their Windows OSs because they will already be using a LiveCD version to use the software), I may have time to come back and help!

My point was only that there are irredeemable errors in the thinking at the start of the installer and I wanted to know how to get that back to the devs WITHOUT bug reporting (because it isn't a bug if the code is causing the effect the code was intended to cause....)

If you don't understand, try this (without affecting anything on your hard disks):

1. Download the i386 v6.10 ISO of Ubuntu.
2. Boot from it.
3. Before the default times out, change the video to something like 640x480.
4. Load the OS from CD but don't DO anything in it.
5. Exit to reboot.

Even with a magnifying glass, you will not get the prompt after the CD ejects so you will assume it is hanging.

That isn't a bug. It's a simple design flaw. Not "bug reporting", not "requests for new features". Simply feedback.

But very important feedback if you consider the aim of Ubunti in wanting to attract anyone and everyone to try it. Try an OS on CD? Heck yeah! The installer hangs when you reboot out of it? Heck, download it again, burn it again and try it again. Same problem? Move on to something else - bye bye Ubuntu.

And no bug and no hang but a lot of lost users who would benefit from this great Linux distro.

Anyway, consider this [RESOLVED] if there is a new route back to the devs for this feedback.

---

