---
title: "protecting Ubuntu install from windows"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-01-24
Hi, I have Ubuntu on sata drive 0 and Windows xp on sata drive 1.  My windows has started running really slowly, so I might reinstall it. However, I want to check that I am not going to ruin the current boot info, which gives me a screen when I bootup offering Ubuntu as default, but also the option to choose windows. Am I right that the boot information will be contained on the Ubuntu drive and messing with windows won't damage it?
Coincidentally, yesterday my bios started doing something strange, instead of getting straight on with the memory check, it comes up with the word "memory", then pauses for about 2 minutes, then finishes the mem check and boots as normal. Never seen that before. You know what that is about?

---

### Post by Canis familiaris on 2007-01-24
Reinstalling Windows in your case will cause Windows to rewrite the MBR. You should be careful. Before taking this step follow the link here:
[http://www.linuxquestions.org/linux/answers/print/441?]("http://www.linuxquestions.org/linux/answers/print/441?")

---

### Post by lamego on 2007-01-24
After reinstalling Windows you will just need to follow:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bernied on 2007-01-24
Windows is a selfish beast - it will behave as if it is the only operating system that exists.
As far as I know, Windows will want to install itself on the first hard drive (first according to BIOS). As part of the install, Windows will overwrite the master boot record (MBR) of the first drive.

For you to be dual-booting, as you are now, you must have over-written the MBR of the first hard-drive, this (if you have a fairly default ubuntu install) is called grub stage 1. Grub is the GRand Unified Bootloader used by ubuntu and is in two or three parts. Stage 1 is only 512 bytes and sits in the MBR, stages 1.5 (not usually necessary) and 2 sit in your boot directory. The file /boot/grub/menu.lst is grub's configuration file.

If you are truly running ubuntu on your first drive and windows on your second, then there is a fairly easy solution - just disconnect your ubuntu drive while you do the windows reinstall and reconnect it once you've finished. This will allow windows to install on the first drive (because the first drive will be missing), and will prevent it from overwriting the MBR. If this is really the case then you will have the following lines in the entry for Windows in your menu.lst file
```
map (hd0) (hd1)
map (hd1) (hd0)
```
these two lines tell grub to reverse the order of the first and second drives, so that windows thinks it is on the first drive, because that is the only place that it is happy to run.

If you do not have those two lines then windows is very probably on your first drive, and ubuntu is on the second. In this case you will not be able to prevent windows from overwriting your MBR, and you will have to rewrite the grub stage 1 MBR, once windows has finished. You can do this through the grub console (from a live cd), by using the ubuntu installation method, or by taking a copy of it before you do the windows reinstall, then restoring your copy when you are finished. For this last method you can use the 'dd' command.

---

### Post by luvinit on 2007-01-24
Thanks a lot. all. I have read a few posts about people having trouble when they are using the 1 drive but wasn't sure about 2 seperates. I will check that out, I suspected the unplug the drive method would work but I will make certain which is number 1/2. I am still debating whether to bother because if I remember correctly it is, at the very least, an all day job installing windows.  I only really use it for games and my number 1 priority is not messing up Ubuntu.

---

### Post by bernied on 2007-01-24
I recommend you look at [this](http://users.bigpond.net.au/hermanzone/) site. Herman (the author of the site) is a regular poster on these forums and really knows how to boot. Have a look at the links at the bottom of that page.

[Here](http://www.debianhelp.co.uk/ddcommand.htm) is a page about the 'dd' command, which includes a command for saving and restoring your MBR.

I recommend that you fully understand your current disk and partition setup, as well as how grub is working for you, before you start this. The forums are full of people who've messed up their dual-boot systems doing what you are about to do.

---

### Post by bernied on 2007-01-24
> **luvinit said:**
> Thanks a lot. all. I have read a few posts about people having trouble when they are using the 1 drive but wasn't sure about 2 seperates. I will check that out, I suspected the unplug the drive method would work but I will make certain which is number 1/2. I am still debating whether to bother because if I remember correctly it is, at the very least, an all day job installing windows.  I only really use it for games and my number 1 priority is not messing up Ubuntu.
It depends on whether you have a SP2 install CD - I did two recent Windows re-installs from an old XP SP1 cd and got so frustrated because Windows spends hours updating SP1, only to then spend another couple of hours installing SP2 over the top. There are many, many updates to be downloaded and installed, so web connection speed is a big factor too.

You could try a scandisk, defrag, spyware check (or three) and virus scan instead.

And have a look at running processes and running services. Windows runs so much stuff that doesn't need to be running.

---

### Post by luvinit on 2007-01-24
My windows xp disc has 2002 stamped on it, and it is service pack 1. I never installed service pack 2 cus I remember when it came out it caused people problems, although I forget the nature of them. I also stopped downloading updates about july last year when the covert WGA download was doing the rounds. I refuse to have Microsoft checking up on me, which is part of the reason I decided to move platform. I already spent a day doing the spyware/virus check, there were the usual few instances which I always find, nothing out of the ordinary. The problem seemed to be low hd speed. This appeared to be related to the Via raid tool startup program taking up 70%+ processor.  Strange, as this has run for years apparently ok, but I took it out and it has helped. However, there is a long pause when I boot windows now, which didn't happen before. Also, the pathnames to desktop shortcuts seem to have been altered, all folders containing an executable file now having a hidden folder called data/resource containing copies of all exec files. I am sure this wasn't the case before. IF i alter the shortcuts, they revert to this broken link. Boy do I hate windows.

---

### Post by bernied on 2007-01-24
I feel your pain.

I think your situation is a bit of a catch-22, because without the updates (including SP2), windows is insecure. I believe this is why they made SP2 free. SP2 includes a firewall, which is only necessary because they leave all the ports open to the outside world in the first place.

My understanding is that there are many security holes in windows, and their updates fix these one at a time, once they work out where they are - usually because someone has created some software that exploits one of these holes. So the corollary of this is, that if there is an update, then there is an exploit that the update addresses, so not updating since July leaves you open to all exploits developed since then. I think the only way to protect the machine against this stuff (if you don't want the updates) is to a) have an external firewall (like on most routers) configured so that it doesn't let anything into or out of the machine, to or from the outside world, and b) don't run any web browsers. So, basically, don't give the machine any access to the internet in either direction. (Or just pull out the cable that connects the machine when you run windows on it.) You could still give it access to the local network, if you trust all the other machines on the network not to mess with it, and it has no route to the outside world.

So your machine is probably busy doing lots of stuff for other people. This is probably why it takes so long to start up - there is software starting up that you don't want.

Which is worse - having microsoft watching you, or some other bugger using your machine for whatever they want?

I don't know anything about your links or hidden folders. I certainly don't have those folders on this machine (running XP-Pro), unless there is more than one grade of hidden. I'm at work and cannot run linux on this machine (I'd be strung up).

---

### Post by luvinit on 2007-01-24
You,ve just reminded me about the problem SP2 gave, it put the firewall on my pc and it totally blocked my Internet connection, thats why I trashed it a long time ago. I tried switching off the Internet connection, but it doesn't stop the slowness, so I think it might be more to do with something having altered setup rather than some spyware/malware taking up processor/disk time broadcasting across the net, but who knows? It is certainly weird that every single folder containing execs now has that copy in data/resource hidden folder! Oh well. :D

---

### Post by mikewhatever on 2007-01-24
There is not much to add to what's already been said. I think you do need SP2, their firewall can be disabled in favor of a better one, and you do not have to download updates from MS. Check [www.autopatcher.com](www.autopatcher.com)

---

### Post by luvinit on 2007-01-24
Just to update I checked the configuration and the ubuntu drive is 0 so i unplugged it and tried to install windows. Unfortunately, XP doesn't recognise SATA, doesn't seem to like my motherboard/sata driver combination and gives me a stop message.  It is just too bad to be true. :o Now if I hadn't discovered GNU/Linux I would be really annoyed.

---

