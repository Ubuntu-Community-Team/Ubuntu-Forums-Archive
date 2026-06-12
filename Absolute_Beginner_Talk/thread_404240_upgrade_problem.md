---
title: "upgrade problem"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-04-08
I upgraded today, and ended up with 6.11 installed and when Ubuntu loads it stops about a 1/4 inch into the bar on the load screen. Any suggestions as to were to begin to look?

I can get 6.10 recovery to load but not 6.10,6.11 or 6.11 recovery.

---

### Post by r00tintheb0x on 2007-04-08
Hit f6 while booting and do a noapci everything (you'll have to look that up) =)

---

### Post by NikoC on 2007-04-08
You could start by booting up in verbose mode to actually see where the problem occurs...
In grub edit the kernel bootup line by removing 'quiet splash' and adding 'verbose'. This will boot you without splash and showing all bootup lines...

---

### Post by rbhigday on 2007-04-08
> **NikoC said:**
> You could start by booting up in verbose mode to actually see where the problem occurs...
In grub edit the kernel bootup line by removing 'quiet splash' and adding 'verbose'. This will boot you without splash and showing all bootup lines...

Thanks this is the code I could not remember :)

will do it and post once I get home from work.

---

### Post by rbhigday on 2007-04-11
It appears that every time my menu.lst get updated automatically or maybe grub get updated I get the statement bottom=break added in my kernel statements. I remove them and I boot fine. Need to remember this that is the 2nd time now :)

Thanks again for the help, forgot which file to look for to attempt to fix it

---

### Post by jhineman on 2007-04-12
I seem to be having a similar problem.  After an upgrade to 6.10 from 6.06 LTS non of the kernel selectable under the grub menu will boot.  If I'm in a 'verbose' boot, the boot seems to just stop without warning (no info of an actual failure).

You mention some statements getting inserted in at the end of your kernel statements.  How do I edit these (or where's a guide that I can learn to edit these)?

---

### Post by rbhigday on 2007-04-15
go to this thread [here]("http://ubuntuforums.org/showthread.php?t=338637") it show what I did to fix this the first time back in January

---

### Post by rbhigday on 2007-05-25
Ok I installed some update and guess what yep the code came back break=bottom on my kernel statement. Any idea as to what is cause this to always come back?

---

### Post by rbhigday on 2008-01-29
Once again this is back, I will not mention how many times I have done this but is there any way to prevent it.

I get bottom=break with almost every other update.

thanks in advance.

---

