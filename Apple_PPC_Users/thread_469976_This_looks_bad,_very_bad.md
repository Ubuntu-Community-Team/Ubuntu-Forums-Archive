---
title: "This looks bad, very bad"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by luckyd on 2007-06-10
I booted up my iBook this morning, after having no trouble with it yesterday and this happened...

> [    26.388700] PCI: Cannot allocate resource region 0 of device 0001:10:18.0
[    26.388710] PCI: Cannot allocate resource region 0 of device 0001:10:19.0
[    32.081346] RAMDISK: Ran out of compressed data
[    32.081539] invalid compressed format (err=1)
[    32.082668] Kernel panic - not syncing : VFS: Unable to mount root fs on unknown-block(0,0)
[    32.088495]  _ 

This all happens after yaboot, which seemed to run succesfully. What do I do?! :(

P.S. There may be a few typing errors, since I have no possible way of copying and pasting the information.

---

### Post by SycloneMedia on 2007-06-10
Don't worry... I get that like every now and then... nothing bad has happened to your install or anything... just power off and on again... once in a while, it brings that up like 3 or 4 times in a row, but keep powering off and on and it'll boot up.

From what I've read and investigated, it seems to be a problem with ram (3rd party?). I have Crucial but ever since I've installed that I've had occassional problems. And I thought that Crucial was suppposed to be good... hah. Unless I'm mistaken, that's where the problem lies.

If anyone knows any more info, please ellaborate as I'm also curious as to how to get rid of this annoying problem if it's not the ram.

---

### Post by luckyd on 2007-06-10
Thank you, I will try powering off and on again. You are right, I do have third party ram, but I don't think it is bad ram, since it worked with os x for a very very long time without any problems. Mabey it is some linux driver thing  :confused: ???


Edit: I have tried powering off at least 10 times, is it supposed to take that long?

---

### Post by thedarky on 2007-06-11
Hi,
Running a mostly well-behaved Feisty on a 1.25 eMac (USB2.0), I've had the message about devices 18 and 19 from the first time it ran.

Feisty pauses, thinks about the PCI message - sometimes for a minisecond and sometimes for a couple of seconds - and then decides that everything's ok and continues a successful boot. 
I have no idea about the RAM provenance, having  bought the whole machine second hand.

We (Fesity and me) once lost contact with the persistent data (which I guess is stored somewhere between where yaboot hands over to Feisty at boot time) and got stuck without time functions and a lot of the desktop, including access to a power down  software button.  This got fixed by powering down with the hardware  button, after which a diskchecking routine got run by Feisty that fixed "disk errors" to give us back a behaving system.
I don't know if that was connected to the PCI slot problem, but it never hurts to have a fiddle with user-friendly hardware to make sure it looks as good as possible.

So, reading a little about Apple's very constrictive hardware approach, I took out the RAM stick, give the contact points a very thorough gentle cleaning with a gum eraser (same as I do for battery terminals and the like), so as to make sure that as much contact metal-to-metal is made.  I also gave the stick an extra firm push once it was in place - the slots seem to be a little deeper than the contacts on the RAM stick.

Feisty continues to be dismayed about the PCI slots but hasn't refused to run very smoothly since then.

Hope this helps.

---

### Post by thedarky on 2007-06-11
It occurs to me that it may also be useful to boot into the live cd and see what system tools you might have available to check the hard drive.
At least the live cd can tell you that your hard drive partitions look ok, so you can eliminate that as a cause.

And , of course, if the puter won't boot the live cd,  then you at least have narrowed down the problem to exclude the hard drive that way too.

---

### Post by luckyd on 2007-06-11
Ok, I managed to boot into  the live cd and mount the harddrive, so that isn't the problem. Also, earlier I had gone into os x, that is on my external harddrive, and run mem test. This revealed that all of the ram is ok!? At least I can mount the partition through the live cd now, so if anyone has any idea what the problem could be I would be ever so grateful.

P.S. The only thing software installation that I remeber doing on the last successful boot was updating so kernel headers. So if anyone knows that that is the problem, or something else, please help me.

---

### Post by luckyd on 2007-06-11
> **luckyd said:**
> 
P.S. The only thing software installation that I remeber doing on the last successful boot was updating kernel headers. So if anyone knows that that is the problem, or something else, please help me.

Sorry, I forgot to mention that the output of free -m said that there was no swap space, maybe that has something to do with it. maybe?

---

### Post by thedarky on 2007-06-12
Hi,
I think that you can discard the device 18 and 19 messages as error symptoms
[http://ubuntuforums.org/showthread.php?t=471519](http://ubuntuforums.org/showthread.php?t=471519)

This doesn't get you any further in finding out about the RAMDISK error, but I thought it would clean the thread up a bit.

---

### Post by luckyd on 2007-06-12
I really need a fix, I can't keep posting from my friends computer like this. At least somebody try to give me some instructions of what to do, **MY COMPUTER IS TOTALLY INOPRABLE**

---

### Post by stmiller on 2007-06-13
The alternate CD has a rescue mode which can run some disk checks. Sounds like a bad disk.

---

### Post by jimwg on 2007-06-13
Greetings:

On my 900mHz 640meg G3 iBook, my 6.10 live-CD runs great with Persistence on a 1gig flash drive, but on my 1.25gHz 512meg eMac, Ubuntu stalls out right after the initial Ubuntu start-up screen with the growing orange bars, flicking into a colorful text formatted screen out of the '80s mentioning things about can't load because X-device is missing screen driver something or other then blacks out into a Unix screen of death. I've unplugged my DSL, tried running without the flash drive, restarted the computer by hitting the power button numberous times (which I hate to do because the eMac has no real hard-reset button salute). Has anyone had any experience booting Ubuntu on eMacs??

Thanks

James Greenidge

---

### Post by luckyd on 2007-06-13
Thank you stmiller, I ran a couple of rescue shells off of the alternate install cd and now my system boots again. :) The only weird thing now is that the boot time has increased dramatically, any suggestions?

---

