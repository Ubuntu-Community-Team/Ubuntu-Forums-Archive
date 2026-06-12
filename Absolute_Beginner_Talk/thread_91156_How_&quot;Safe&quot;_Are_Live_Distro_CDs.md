---
title: "How &quot;Safe&quot; Are Live Distro CDs?"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by polo_step on 2005-11-16
This is a *real* beginner's question, huh? ;) 

Is it possible for a "Live" distro Linux CD to mess up an existing XP (or other) system on the demo-ing computer?

I ask because I have heard a number of anecdotal reports that on hot reboot to XP after removing the "live" Linux CD, the installed system experiences moderate to major problems, including failure to boot, corrupted CMOS, etc., etc.  One claim is that there's something still in RAM unless the system is completely powered down.  I dunno, so I'm asking.

I have myself experienced XP booting problems immediately after running Ubuntu Live, but I have not been able to be 100% sure that Ubuntu was the cause...still, these reports cause me some concern, especially as I want to try 5.10 Live on my new notebook to check for compatibility and can't afford to screw it up.  I'm also reluctant to pass out Ubuntu CDs until I know for certain I'm not poisoning someone's box.

Thanks for any really authoritative answer on this.

---

### Post by Kyral on 2005-11-16
I've never experianced any screwups with LiveCDs and I have used them on many computers. Stuff left in RAM...I don't think so...

---

### Post by Rackerz on 2005-11-16
People who say stuff left in RAM need to back that up a little. I've used about 5 livecd's in the space of 2 days and haven't experienced problems so your safe unless you do something you shouldn't.

---

### Post by Kyral on 2005-11-16
In theory as soon as the power goes, the RAM is cleared. Even then it shouldn't matter unless the code is REALLY screwed up (a basic C++ course will explain why)

---

### Post by polo_step on 2005-11-16
[QUOTE=Kyral]In theory as soon as the power goes, the RAM is cleared. [/QUOTE]
The claim is that it isn't completely gone in a hot reboot, presumably because of the charge in the electrolytic caps or something. [shrug]

Anyway, I'd like to hear from one of the Ubuntu team on this one way or the other, for sure.  Everything else is just more anecdotal experience.  If one of the Ubuntu pros signs off on this as being technically a total, foolproof non-problem, then I'm done.

---

### Post by Kyral on 2005-11-16
Like I said it shouldn't really matter. The only time it might come into play is if a variable is created without being given a value. Then it holds whatever value was in the memory address it is assigned to. But that is just REALLY bad coding if thats happening.

---

### Post by andy101 on 2005-11-16
can you damage XP with a live CD?

Depends what kind of stuff you are doing really. I only ever had a problem with 1 live CD, (Knoppix) it crashed. Powered off machine, waited a few seconds, rebooted, worked fine (after taking the CD out of course)

You can damage data on you NTFS I think. But that would only happen if you mounted it read/write. Some live CDs will write onto an NTFS but there are apparently risks to doing it. (I personally have a FAT32 partition to share between Linux and Windows). Also if you tried to repartition you hard drive from a Live CD it could go wrong. Never known this to happen personally (I shrank my NTFS and added a partiton from a live CD).

RAM is volatile so when it loses power everything on it should be wiped. It might retian power for a short time from capacitors or something. But as has been said it shouldn't really be a problem.

I have used several differant Live CDs, and I know others who have and have never known anyone damage windows while doing it. I once managed to rescue a friends computer with a Live CD though.

My copy of windows crashed before I ever used a live CD though, so I wouldn't tell unless something went seriously wrong, i.e. boot failled.

Only thing thats ever happened to me after using a Live CD is windows ran a disk check, and that was because I re-sized its partiton, (for anyone whos interested this disk check didn't find any problems)

---

### Post by apjone on 2005-11-16
I think you need to question the source's of these claims?? Some people spend alot of time trying to scare the masses away from linux, not mentioning any names or corp's .

---

### Post by aysiu on 2005-11-16
I've used live CDs on about six different computers (Ubuntu and others--Knoppix and Mepis), and I have never seen any ill effects on the hard drive--ever. I've read about a couple of people on Linux Questions blaming a hardware failure or some other thing on having "just used a Linux live CD," but it just isn't possible.

If it's running off RAM and the CD, it can't damage your hard drive accidentally. It can purposefully, if you mount the Windows partition read/write and delete all the files.

---

### Post by poptones on 2005-11-16
New operating systems like linux and XP do not use the motherboard BIOS, but they do on bootup. If the option in the motherboard CMOS has enabled shadow BIOS, then a warm boot may leave remnants of the live CD's BIOS table in memory which the motherboard BIOS will be using without knowing it. Because motherboards are themselves now dynamic state machines (ie massive arrays of programmable logic) a warm boot could leave that machine in a state not expected by the motherboard BIOS. Warm boots from reset are not treated the same as cold boots, and this can cause problems.

this can cause odd behavior, but not hard drive damage. However, live CDs have no respect for the sanctity of the hard drives connected to the host. For example, don't boot someone's machine, go to a command line, and type

dd if=/dev/zero of=/dev/hda

Serious borkage... of course, this power is also why they are an administrator's best friend.

---

### Post by polo_step on 2005-11-17
[QUOTE=poptones]Because motherboards are themselves now dynamic state machines (ie massive arrays of programmable logic) a warm boot could leave that machine in a state not expected by the motherboard BIOS. Warm boots from reset are not treated the same as cold boots, and this can cause problems.[/quote]
Thanks!

That sounds to me exactly like the issue, and is consistent with the information I saw, but did not fully understand.  I also believe that this situation can corrupt CMOS settings, leaving a mess that snowballs, as it appeared to in my case.

Short answer, then:  For safety sake, do a full power down after using a "Live" CD before booting to the different, installed OS.

---

### Post by chazzjazz on 2005-11-17
modern motherboards dont leave things in shadow bios, even if they do, linux code is unuseable from windows so it wont load. its that simple

live cd will damage a hdd only if programmed to write to it...if you want a windows partition and dont have windows, get a mate with windows to make the partition. making a windows partition from linux is asking for trouble...

---

### Post by poptones on 2005-11-17
Dude... BIOS code has *nothing at all* to do with linux or windows. The CPU does what it does, the vector tables work the same way no matter the operating system. This is not a "sytems issue" it's a firmware issue.

This, however, is **not at all** likely to corrupt cmos settings. If you are having issues with cmos settings, replace the battery on the motherboard.

---

### Post by jdong on 2005-11-17
Yes -- what people said about mobo's. I've seen some retail demo systems not boot back to XP properly on warm boot, though a shut-off and turn-on will fix the problem...

---

