---
title: "Is Linux killing my USB drive?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by whitefort on 2008-04-06
Hi,

I've been using a USB harddrive with my (Ubuntu) laptop, but I've noticed that when I shutdown the drive makes an unhappy sort of popping sound that I never get when it's used on a windows machine.

I get the feeling it's not shutting down the way it should, and since I've heard this can kill a drive, I'm getting slightly worried.

I always right-click and 'unmount' the drive before I shutdown, but it doesn't seem to make any difference.

I'd be grateful if someone could tell me:

a) Is this something I should be concerned about, or am I worrying about nothing?

b)  If it IS a Bad Thing, is there an (easy!) way to fix it?

Many thanks.

---

### Post by viciouslime on 2008-04-06
It sounds like ubuntu isn't parking the heads properly. You should file a bug in launchpad :)

It is bad for the drive, but it won't kill it very quickly....

---

### Post by Rocket2DMn on 2008-04-06
It definitely should not be making funny sounds, so just to be safe I would suggest getting your hands on another drive to backup the important stuff on.  It's possible that the insides are not settling properly when you shut it off (or the disc spindown is getting friction).  With hardware problems, there really isn't any way to know if it's going to fail until it actually does.  This doesn't mean that your drive is unusable, but just that you should always be weary when it doesn't act normally.  Since hard drives have moving parts, they are more prone to hardware failure than most other devices.

---

### Post by whitefort on 2008-04-07
Thanks, guys.

I've been experimenting - it definitely seems to be a Ubuntu problem.  I've now tried two other USB drives (making a total of 3) and they all make the popping sound when the Ubuntu computer shuts down.  None of them do it on the Windows machine.

So you think it's a Ubuntu bug?  I love Ubuntu, but the thought that it might do stuff that damages my hardware really scares me.

I'd hoped that I was just overlooking something, and needed to type in some command or something to get the USB drive to spin down properly.

---

### Post by TenPlus1 on 2008-04-07
I have an external HD that mounts ok and dismounts ok, but I do switch it OFF before shutting down the Pc for safety and surge reasons...

---

### Post by SunnyRabbiera on 2008-04-07
well have you tried to safely unmount the drive?
this sounds like a very unusual error, what kind of USB drive is this?

---

### Post by whitefort on 2008-04-07
> **SunnyRabbiera said:**
> well have you tried to safely unmount the drive?
this sounds like a very unusual error, what kind of USB drive is this?

Hi.  I've tried three (all Western Digital).  Yes, I right-click the on-screen icon and select 'unmount'.  Then the icon vanishes.  But this seems to have no effect on the drive at all.  If I put my hand on it, I feel a vibration as if it's still spinning, and when the computer powers down, the drive gives that worrying little 'pop' noise.

Turning off the drive before powering down the laptop isn't an option, as the drive gets its power from the USB connection and has no on/off switch.

I'm getting the sinking feeling that this problem is maybe unique to me... :(   I was hoping everyone was going to say, 'Oh, that's easy!  Don't you know you have to do (whatever) before turning off the computer...?'

This is not, by any means, going to turn me off Linux - I'm now a rabid convert!  But it's worrying to think that my OS could be shortening the life of my hardware.

---

### Post by SunnyRabbiera on 2008-04-07
well linux is software not hardware...
i see no reason why its doing this.

---

### Post by whitefort on 2008-04-07
A quick PS - it looks like this is a recognised Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713)

I'll try the workaround later today and report back.

---

### Post by whitefort on 2008-04-07
Yes, the script listed on the bug report page seems to do the trick.

For anyone else with the same problem, here's what I did.

Saved this script in my home directory (I called it wdoff). Oh, I also had to install sdparm to get it to work.

#!/bin/sh
WD=/dev/sdb1
sudo umount $WD
if [ $? -eq 0 ]
then
 echo Stopping heads
        #Stop properly the heads and cylinders
 sdparm --command=stop $WD
else
 echo Unmount Failed !
fi

Then made it executable.  Now, before turning off the machine, instead of using 'unmount' I open a terminal and type ./wdoff

My WD drive stops spinning and unmounts.

So, problem solved.
It's knocked my confidence in Ubuntu, though.  I would have thought that when there's a bug that actually damages hardware, the fix would have been a bit better publicised or (better) build in to an update.

I wonder how many users are slowly destroying their hard drives because they aren't aware there's a problem?

---

### Post by stchman on 2008-04-07
> **whitefort said:**
> Hi,

I've been using a USB harddrive with my (Ubuntu) laptop, but I've noticed that when I shutdown the drive makes an unhappy sort of popping sound that I never get when it's used on a windows machine.

I get the feeling it's not shutting down the way it should, and since I've heard this can kill a drive, I'm getting slightly worried.

I always right-click and 'unmount' the drive before I shutdown, but it doesn't seem to make any difference.

I'd be grateful if someone could tell me:

a) Is this something I should be concerned about, or am I worrying about nothing?

b)  If it IS a Bad Thing, is there an (easy!) way to fix it?

Many thanks.

Question?  Does the USB hdd feed power from the USB port or does it have an external power pack?

If the hdd feeds power from the USB port then it should shut down and park the head when the power is no longer applied.

If the hdd has an external power source shutting down the laptop will not cause the hdd to turn off.  I have an external hdd with separate power and after I shut PC off I shut hdd power switch off.

---

### Post by whitefort on 2008-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117713](https://bugs.launchpad.net/ubuntu/+bug/117713) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **stchman said:**
> Question?  Does the USB hdd feed power from the USB port or does it have an external power pack?


It gets power from the USB port, but still doesn't park the head - as mentioned in one of my previous posts, this is a known bug in Ubuntu.

I think it's really shocking that (apparently) it still hasn't been fixed in the  soon-to-be-released new version of Ubuntu.  It blows my mind that a hardware-damaging bug doesn't seem to be regarded as any kind of priority.

---

