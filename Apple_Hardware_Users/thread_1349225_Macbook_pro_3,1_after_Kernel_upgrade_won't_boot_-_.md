---
title: "Macbook pro 3,1 after Kernel upgrade won't boot - What do I do?"
date: 2009-12-08
forum: Apple Hardware Users
---

### Post by lael on 2009-12-08
I have Ubuntu 9.10 (upgraded from 9.04) on a 17" Macbook Pro(3,1) with rEFIt.  I have been doing software development professionally on it for the past ~ 8 months and have been using Karmic on it for the past month. Go Ubuntu in the workplace!!

Last night I had a kernel upgrade come across the update manager.  I installed it, and rebooted the system without issue.

I left the system on overnight and used it a little bit in the morning.
When I shut it down before going to work - it didn't shut down all the way so I let it sit for a minute, then held the power button down to shut it down the hard way.

When I got to work this morning, the laptop wouldn't boot.  It didn't even give USB power to my keyboard & mouse.

I tried all sorts of Apple startup key combos but none of them seemed to work.  I got a Linux LiveCD and stuck it in there and after that it gave USB power for a little bit.

It occasionally chimed like it was going to boot but didn't.

After ~ 20 minutes, I tried another key combo (that I had tried before) and it started into the grey screen then [my rEFIt menu]("http://colinharrington.net/blog/2009/05/customizing-refit-an-efi-bootloader-intel-macs-slick/").

At the end of the day, I shut it down and it wouldn't boot all over again.

Later in the evening when I went to figure this out it took 10 minutes of trying startup key combos before I could get it to boot up.  This time I chose OSX so that I could re-enable rEFIt.  I ended up installing an OSX update for which it rebooted and came back up to my rEFIt boot menu.  I booted again into OSX and ran the /efi/refit/always-enable.sh script

After shutting down, I am unable to get the machine to boot now.  It won't even chime or give me back my boot CD (which it would eventually do previously)

I am at a loss on what I could try to revive this machine.

What can I do?  Any ideas or pointers?

Do you think that a new Kernel could have anything to do with this?

When I did a hard shutdown, what might I have corrupted?

Thank you!

---

### Post by lael on 2009-12-11
So this one turned out to be hardware failure.  The Motherboard died.  Apple fixed it under Apple Care and it was back to me fairly speedily.

---

### Post by linuxopjemac on 2009-12-12
can you make this post solved ?

---

