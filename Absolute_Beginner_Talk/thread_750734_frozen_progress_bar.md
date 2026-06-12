---
title: "frozen progress bar"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by blairm on 2008-04-09
Hi there,

My Parents are running Ubuntu and loving it, but there's one issue which is proving annoying.

One my computer, the check which happens after the file systems have been mounted 32 tmes (think that was the phrasing anyway) happens automatically, which is great.
But on my parents' one, it doesn't; instead the progress bar when Ubuntu is started stops about a third of the way through and freezes.

To fix it, they have to boot in recovery mode, at which point the check is done.

Their machine is AMD 4200+, integrated nvidia 6100 graphics, 1gb of ram. They're running Fiesty Fawn.

Any ideas, anyone?

Cheers,

Blair

---

### Post by warbread on 2008-04-10
How long did you give it before deciding that it's frozen?  My computer will lag at this point significantly.  The bigger the hard drive, the more files you delete and the longer it's on between boots, the longer this check is going to take.  

There is a way to stop Ubuntu from doing the check at all, but I wouldn't suggest it.  That check is necessary for keeping the system running smoothly.  If there's a problem here, it's probably with the hard drive itself.  

What you can do is force a disk check and then time it to see how long it will take.  Do it at a time when your parents won't be needing the computer for a few hours.  It's better to do this test the right way once and not have to worry about it if they need their computer on in a hurry.

Boot to recovery mode or from a live disk.  If you already know what partition you want to check, just type in "sudo fsck /dev/<hard drive>".  If you're not sure, start with "sudo fsck -l" and it will list all of your partitions.  If you are unsure of which to check, try the largest one.  Type in the aforementioned command and let it run to the end.  You'll know it's actually frozen if the HD activity light stops blinking and/or you cannot hear the HD running for a good long time.  

Hope this helps.

---

