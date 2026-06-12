---
title: "Ubunt boot stuck after &quot;check forced&quot;"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Coward on 2007-08-15
I'm using Ubuntu 7.04

Everytime I start my laptop it stops after the following lines
/dev/sda1: Superblock last mount time is in the future. FIXED.
/dev/sda1 has gone 49709 days without being checked, check forced.
/dev/sda1:  |=========                                                                | 17.7%

It's not always exactly 17.7% when it stops, but always around there. I have owned my computer for less than a week so I know the days are wrong.

I had a problem booting and shutting down before. I enabled the nvidia driver and when I restarted it actually managed to turn off (before it would get stuck in a loop with the sound). I don't think this error is related to enabling the nvidia driver because I was getting this error before, so I reinstalled (I hadn't enabled the driver that time).

How can I get past this part of the loading? Is there a way to correct it so that it doesn't force a check?

---

### Post by splintercellguy on 2007-08-15
BIOS battery failing? Your clock seems to be screwed up. As for the fsck issue I guess boot to recovery mode, remount / read-only, fsck?

---

### Post by Coward on 2007-08-15
My system time is correct, I just checked it.

I can't really boot in recovery mode because it always gets stuck after this:
[ 0.000045] CPU#0 had -280 usecs TSC skew, fixed it up.
[ 0.000096] CPU#1 had 280 usecs TSC skew, fixed it up.

I don't know what this means either.

Thanks for the quick reply.

---

### Post by Coward on 2007-08-15
Well, now the number of days it says it has gone without being checked has increased by 1. The problem is still here. Does anyone have an idea of how to get past this? I am new so please explain your steps.

---

### Post by Hobo Joe on 2007-08-15
Find the battery on the motherboard, take it out, wait 5 minutes, and put it back.

This may not be the problem, but it's always a good thing to do anyway.

---

### Post by Hospadar on 2007-08-15
Well it may be also that your filesystem is corrupt.  Try booting off a livecd and fsck-ing your drive from there.

And yeah, it may be your bios battery too.  Be careful with that, make sure you read the mobo manual on how to reset it (also you'll want to disconnect the power supply) Sometimes there is a jumper to reset it (which may not work if the battery is dying).

---

### Post by Coward on 2007-08-18
Well, I reinstalled Ubuntu. It was working great, I even got Beryl working, but then this check forced appeared again. This time the message is:

/dev/sda1 has been mounted 39 times without being checked, check forced.
/dev/sda1 :|======    | 22.8%

It's probably right about the times it has been mounted, but that doesn't change the fact that it still gets stuck.

I'm looking for a way to skip this check. If I have to, I'm also willing to reinstall if someone can tell me how I can stop this check from happening again.

I ran "sudo tune2fs -c 0 -i 0" last time I installed but it seems that didn't stop this check. Well, the website says it disabled interval checks, so does that mean this line only disables checks that happen based on time? If so, how can I disable ones based on the number of times I mount aswell?

(When I do recovery mode I still get stuck where it says TSC skew)

Edit: According to this website the ability to skip the disk check is being worked on. [https://blueprints.launchpad.net/ubuntu/+spec/boot-disk-check-forced-skip](https://blueprints.launchpad.net/ubuntu/+spec/boot-disk-check-forced-skip). I'm pretty sure that means I can't currently skip it, so I'm going to have to reinstall again and somehow disable these checks.

---

### Post by fredj on 2007-08-19
Linux is programmed to check the hard disk for errors at regular intervals. When you first install
it the disk has never been checked so it has a built in interval that is so far in the past that a 
check is always forced. If your system cannot get past this check then it suggests that there is
something really wrong with your hard disk.

---

### Post by Raptor45 on 2007-08-19
Are you sure its actually freezing? How long do you wait before deeming it an issue?

---

### Post by markph on 2007-08-19
I'm having the exact same problem on my laptop.  FSCK appears to be freezing.  It is always at different percentages, but I have not made it past 15.2%.  Some of the random values are 13.3%, 14.4% and 15.6%, etc.

* Checking root file system...
fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 has been mounted 30 times without being checked, check forced.
/dev/sda1: |=========                                                     / 15.2%

I've let it sit there for quite some time, still no recovery.  I power it off and back on, it just starts the fsck and then stops.

The laptop/Kubuntu worked flawlessly prior to this.  I would rather not wipe/re-install, etc.  I do not think this is a drive error everyone is experiencing.

I just found this bug:
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773)
](*,)

---

### Post by markph on 2007-08-19
I booted up using my LIVE CD and ran:
```

sudo e2fsck -C0 -p -f -v /dev/sda2
```

No errors were reported.  I shutdown the laptop, removed the LIVE CD and booted back up into Kubuntu with no problem.

---

### Post by philinux on 2007-08-19
When fsck stops if it gives you a command line use fsck -v this means be verbose and it may start asking relevant question and let you proceed.

---

### Post by markph on 2007-08-20
Thanks **philinux**, that would have been nice if it stopped and gave me a command line.  But it didn't...quite a nasty little bug IMHO.  :popcorn:

---

### Post by Coward on 2007-08-20
I am sure this is getting stuck and not me just being impatient. The progress bar goes quickly until it stops at a random percent (usually between 15 and 20 percent for me) and then I can wait for half an hour without the loading percent changing at all.

How can I disable the automatic check on start up?

Edit: oops, didn't see there was a second page!
Edit2: Thanks everyone. I ran the command posted by markph, rebooted, and it actually booted. I had a problem with the title bar not appearing on the first boot but on a second try all was well. Am I going to have to do this every 39 times I boot, or is this a permanent solution? If it's still going to try to do checks I need to find a way to disable it, since this is a laptop and I don't expect to carry the live CD around with me.

---

### Post by markph on 2007-08-20
> **Coward said:**
> 
How can I disable the automatic check on start up?


Great question, I wish I knew this too.  If anyone finds out, can you please reply.  I'm guessing something in the grub kernel startup line?

> **Coward said:**
> 
Edit2: Thanks everyone. I ran the command posted by markph, rebooted, and it actually booted. I had a problem with the title bar not appearing on the first boot but on a second try all was well. Am I going to have to do this every 39 times I boot, or is this a permanent solution? If it's still going to try to do checks I need to find a way to disable it, since this is a laptop and I don't expect to carry the live CD around with me.

Instead of doing this every 39 times.  You can also adjust and extend the cycle using tune2fs or ignore checks forever.  But I would never accept the latter option.  For me, I would keep putting off the checks... So...
Check out this thread: [_HowTo: Change disk checking/fsck at boot frequency_]("http://ubuntuforums.org/showthread.php?p=1763580#poststop")

Honestly, I would like to see where the user has the option to bypass it.  If the user continues to bypass it, then its on the user.  On the other hand, for someone like me who knows its a good thing to do, I will only bypass it a few times while on the road or on battery, before I will let it run.

---

