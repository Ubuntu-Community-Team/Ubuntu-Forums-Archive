---
title: "Ubuntu only works when Ctrl key is pressed."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by blinkum on 2007-05-12
Hi everyone,

I've recently installed Ubuntu Feisty on my Emachines T1742 desktop. I've had certain problems with the CPU fan, but I've added an acpi=off flag to grub and fan seems to be working now.

What might sound stupid is the second problem I'm having:

Ubuntu does not seem to be working well when I don't press and hold the Ctrl key. Let me give some examples: 

* I login with my username and password, and there's a startup sound to be played. Ubuntu can play only the first few seconds of the sound and then freezes over (for hours if I don't involve). If I press and hold the Ctrl button, rest of the music comes and the desktop is loaded!

* I open up Firefox and type a web address and hit enter. The progress image starts flipping, but web page is not loaded until I press and hold the Ctrl button (I do it with Ctrl button but I think other buttons might to the trick as well).

* I open up a console and ping my other computer on the network. Of course: no response until I start pressing Ctrl, when I press the Ctrl key all the ping responses get listed on the screen.

However the Ctrl trick is not necessary when I'm doing something interactive (like typing stuff in OpenOffice, or using konsole with typing and entering commands).

This might seem stupid, but it happens to me!

I hope one of you guys can help me out :)

Sincerely.
Mustafa

---

### Post by sandman55 on 2007-05-12
When you download Ubuntu there is a check sum at the site a long hexadecimal number and you use some software to create a Check sum from your download and compare it with the site to make sure there are no errors (this is not 100% fool proof) also when you put in your disk you get the option to check your disk because there can be errors from burning ( you can still do this) Im not an expert but I wonder if your disk could be corrupt

---

### Post by blinkum on 2007-05-12
Hi, 

Thanks for the quick reply. But my disk was fine before Ubuntu. I believe the disk is OK too because it has been installed on other machines too: no problems.

Actually the Ctrl key problem was not there before I've turned ACPI off. I've switch ACPI back on now and I don't have to press Ctrl to run anything.

But if I turn on ACPI, then the CPU fan stops working and CPU gets over heated. 

Do you think I've to pick between a working CPU Fan and a working Ubunt :)

Sincerely.
Mustafa

---

### Post by dstew on 2007-05-12
It sounds like some process is running that uses the ctrl key to start/stop. Do you have Virtualbox installed? The control key is what activates/deactivates virtual windows, and that might be part of the problem. Just a guess.

---

### Post by blinkum on 2007-05-12
Nope, I don't have Virtualbox installed. But the Ctrl key behaviour was also working in the login screen (allowing the audio to be played).

I've tested it again and it seems that not only Ctrl key does the trick, Enter, Esc works too. So I'm gonna go ahead and say that any keystroke helps. 

I guess the key strokes somehow trigger something what ACPI does, because when ACPI is on there's no problem.

Any ideas?

Sincerely,
Mustafa

---

### Post by sandman55 on 2007-05-12
This is over my head but your not alone with this problem
[http://ubuntuforums.org/showthread.php?t=364386](http://ubuntuforums.org/showthread.php?t=364386)
[http://answers.yahoo.com/question/index?qid=20070506131532AAVfS2O](http://answers.yahoo.com/question/index?qid=20070506131532AAVfS2O)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/24308](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/24308)

---

### Post by blinkum on 2007-05-13
Yeah, I've read those. I guess the problems are similar. 

They have a couple of solutions like givin "acpi=off noacpi" parameters to grub, and running lm-sensors, both of which don't work for me. 

I think this might have something to do with my mainboard or something:

CPU:  	Intel® Celeron® Processor 1.70GHz (w/128KB L2 cache & 400MHz FSB)
Chipset: 	Intel® 845GL chipset

I've seen other eMachines owners complaining this too. But I don't think that there's a silverbullet solution. 

I actually don't even want the fan to be "controlled" by my system, it's fine for me if it's always on and running. Given that do you know of anything I could do to solve this? Maybe there's a program which makes the CPU fan run all the time without temperature information (which is obviously bogus in my case).

Best.
Mustafa

---

### Post by sandman55 on 2007-05-13
The only thing I can think of is to power your fan direct from your power supply and not your Motherboard I wonder if there is an adapter plug to interface the fan to the power supply. I think there would be, looks like some thing a google will fix. The only down side is MOBO fans usually have a third wire which would be no problem with an adapter only that wire is designed to give feed back of it running so the bios will shut the PC down because the fan isn't running. That might not be a problem in your case because it is not shutting your computer down.

---

### Post by sandman55 on 2007-05-13
Bingo [http://www.altex.com/product_info.php?cPath=1_238&products_id=2960](http://www.altex.com/product_info.php?cPath=1_238&products_id=2960)

---

### Post by blinkum on 2007-05-14
Thanks a lot Sandman :)

I've bought the ATX-MOLEX converter, and plugged the CPU-Fan to the new molex power outlet.

I've turned the computer on and shortly after the bios screen it turned itself off. Apparently my operating system does not care whether the cpu fan runs or not, but my BIOS does.

So I've plugged the cpu fan to its original place, started my operating system and then switched the cpu fan to the new outlet and bingo it started working :)

This first made me quite happy, but in my city power outages are so common (a couple each day). And I need my computer to be up and running all the time (when I'm away too), so this manual operation is a temporary solution, but not a permanent one :(

I wish there was a software solution to this.

Best.
Mustafa

---

### Post by sandman55 on 2007-05-14
I wonder if you upgrade your bios to the latest if that will help

---

### Post by blinkum on 2007-05-15
Ok, I'll try the BIOS upgrade and post here what happens ;)

---

