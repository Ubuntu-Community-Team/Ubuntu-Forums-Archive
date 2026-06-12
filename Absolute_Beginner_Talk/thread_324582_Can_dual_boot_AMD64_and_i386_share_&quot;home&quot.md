---
title: "Can dual boot AMD64 and i386 share &quot;/home&quot; partition?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by michaeljustman on 2006-12-24
Okay...

I got through the install of Ubuntu on my HP zv6000 and got my broadcom wireless card to work with ndiswrapper and my ATI Radeon Mobility 200M to work with the fglrx drivers, so I could use Beryl, without asking a single question to this forum, so I'm almost ashamed to ask one now that is so simple.

I've searched with google and the forums and still can't find the answer.

I want to dual boot my machine with an install of Ubuntu running AMD64 and the i386 kernels. I have a separate partition for my home directory.

Would there be any problems with using the same home directory between the two installs of Ubuntu? Would (some of, at least) my settings carry across between installs?

Thanks in advance.

---

### Post by spockrock on 2006-12-24
I cant see why you couldn't........the preference files, shouldn't make a difference in a x86, x86-64 or ppc Ubuntu, or a Linux distro.  Sorry I think, I believe it should be safe to do, so I think, don't take me at face value.

---

### Post by ~LoKe on 2006-12-24
Should be fine.  There's nothing terribly unique in your configs, so as long as your username is the name, I wouldn't imagine there being a problem.

---

### Post by michaeljustman on 2006-12-24
Thanks. I think I'll try it.

---

### Post by berkpaul on 2006-12-26
Hi Michael.  Any luck with the sharing of you're home directory?  I was considering trying to figure out how to either try the same, or wipe my amd64 install entirely.  I'm at a similar point where I'm a new ubuntu/linux user that just finished playing with things like beryl but still lack some familiarity with how linux is set up.  Can you share any tips on how I can easily create add the i386 kernal (to a separate partition) without doing a complete install and preserving my current home directory?

Thanks for any help.

---

### Post by michaeljustman on 2006-12-27
Well, I haven't tried it yet myself (got busy with my kids and family)... I'm rather new to linux myself (two weeks or so), so maybe someone else can give you better advice, but the first step would be moving your '/home' to its own partition. (I followed these directions over at [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").)

When you've moved your home directory, you would just need to re-partition your hard-drive. You can probably use GParted to do this (boot off the Dapper LiveCD so they aren't mounted, so you can resize them. GParted isn't a part of the Edgy LiveCD because it's no longer maintained) , but you need to create a partition for your new i386 Ubuntu install. When you install the i386 make sure you point the installer to the partition you created for your home directory and uncheck the box for formatting the partition, so the installer will put the right info in /etc/fstab

Like I said, I'm new to linux myself. Good luck. I've decided to stick with 32-bit Ubuntu because I've heard that the 64-bit version is hard to get working with some software, codecs, etc. I'm sure you can attest to that. Good luck with your install.

If you want to wipe your AMD64 partition, just use the tutorial to make a seperate home partition (or back up your home dir) and reinstall on the existing linux partition.

Have fun.

- Mike

---

