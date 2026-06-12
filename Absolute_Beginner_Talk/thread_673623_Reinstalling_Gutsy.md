---
title: "Reinstalling Gutsy"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by PJoseph on 2008-01-20
Brand new to Linux...installed Gutsy totally, wiped XP out.  Began having trouble with ATI graphics card drivers - running HP zt3000, ATI Mobility Radeon 9200.  Don't know exactly what I did in trying to get desktop effects to work - but messed with xorg fglrx and the normal ati drivers...it's all a mess.

So, wanted to do a complete reinstall of gutsy and start over clean.  Nothing to keep on this drive...clean wipe.  I have my Ubuntu LiveCD which I used to move from XP.  I can't get it to boot.  Have an iso of the alternate cd on desktop.  

How should I go about wiping and reinstalling?  Just not familiar enough with Linux to know where or how to go about it...:confused:

No partitions, no dualboot, nothing but gutsy present

---

### Post by JoshuaRL on 2008-01-20
Should be pretty straightforward.  Just install and when you get the option to partition, select the one that uses the whole drive and is guided.  That should wipe the drive and start fresh.  Also, you might run:

```

sudo dpkg-reconfigure xserver-xorg

```

either first before you reinstall, or right after to see if that can get the right drivers loaded.  Worth a shot.

But I know what you mean, I started over 4 times before I got it working.  But to be fair, I really didn't need to and didn't know that.

Are you sure you need to reinstall?

---

### Post by sports fan Matt on 2008-01-20
Ive probably started over a dozen times, notr taking the time to learn in the beginning, but now I figure if i can do it without a reinstall. im better off..Linux isnt harder, its different..alot of copying and pasting but i prefer it..I know what you are going through though:)

---

### Post by PJoseph on 2008-01-22
Thanks for the responses.  Let me clarify...the problem is probably pretty basic for you guys.  My LiveCD won't boot - it is enabled as first in the boot order - the machine just skips it and goes through GRUB and into Ubuntu.  So, that being the case, how do I go about reformatting?

Otherwise, I did try your "sudo dpkg-reconfigure xserver-xorg" suggestion.  I still get errors when I run it that say xorg-fglrx couldn't be removed or doesn't exist, etc.  Is there some way to reset things to the original install setup?  With just the video drivers?

---

