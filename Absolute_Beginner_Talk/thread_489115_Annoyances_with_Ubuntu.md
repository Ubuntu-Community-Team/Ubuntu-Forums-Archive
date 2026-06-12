---
title: "Annoyances with Ubuntu"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-07-01
I am not sure if this goes in "absolute beginner" or not - they're just issues I've had which haven't really affected my overall computing abilities and I thought maybe somebody could help.

1.  Floppy detection.  I didn't get a floppy drive because, well, nobody uses them anymore and I didn't want to shell out the $5 to get one.  But now, every time I start up the computer and it begins detecting devices it says there was a failure in finding the floppy drive, to which I reply with a simple F1 to continue and forget about it.  If possible though, I wish I could make it stop looking for a floppy at all on startup.

2.  Diskcheck - Occasionally on startup the computer will say my disk hasn't been checked the last 30 times it was mounted, so it's forcing a check.  What is this disk check, do I need it, and if not how do I make it go away?  If I do need it how do I make it happen more often?

Thanks for helping, everybody.  And if you happen to know how to write a driver for a Lexmark x5270, keep in touch

---

### Post by geraldm on 2007-07-01
On diskcheck:
man tune2fs

---

### Post by paradoc on 2007-07-01
This may help you

a search came up with>  Re: Use Wine to Drive Printer?
Your printer is based on Lexmark's x5270, so try the Lexmark Z55 driver. It might work with your printer, but no guarantees. It worked mostly with an X5150.
.
..........but don't ask me, I'm fairly new here!...

(you'll find searches easy enough if you put the details in the rectangle that says [color=red**Go**/color])

---

### Post by silverglade00 on 2007-07-01
Check your BIOS for an option to disable Detect Floppy On Boot. The diskcheck is a quick check to make sure that your file system is healthy. Think of it as the equivalent of a Windows defrag and disk check, but in a minute instead of overnight.

---

### Post by univremonster on 2007-07-17
I tried the Lexmark Z55 driver but no dice - I actually at one point even went through all of the generic printer drivers which Ubuntu has to offer in an attempt to find one which would at least print off the Lexmark, to no avail.  Maybe it's time to go invest in an HP...

After learning what it was (although I guess the name is rather intuitive) I decided to leave diskcheck on, and by editing BIOS turned off the floppy detection.  It's amazing how simple some of these solutions are, so thanks everybody for posting replies to what may look like an idiotic question.

---

