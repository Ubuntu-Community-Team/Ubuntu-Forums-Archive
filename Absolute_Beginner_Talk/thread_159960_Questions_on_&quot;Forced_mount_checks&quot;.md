---
title: "Questions on &quot;Forced mount checks&quot;"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-04-13
Thank you for your insight on this one guys...the question is, can a file system mount check be done at any time? Maybe forced? (from what I've read, it's not good to force things in Linux) I'd like to incorporate it into a scheduling routine above and beyond the required forced ones. Or maybe someone could tell me where the forced checks come from so maybe that file could be altered?


You guys as always are the greatest in coming thru on things....

bob

---

### Post by hw-tph on 2006-04-13
**sudo touch /forcefsck** will create an empty file called "forcefsck" in the root of the / filesystem. This will force a filesystem check on the next boot. There are most likely other neat ways, but you cannot fsck mounted filesystems (you can remount the readonly and then fsck them).


Håkan


Håkan

---

### Post by djsroknrol on 2006-04-13
Many thanks hw-tph for your response...so what you're saying then is that the system is checked before it's mounted? Then, that would mean the routine is in the kernal, Am I correct?

---

### Post by dcstar on 2006-04-14
[QUOTE=djsroknrol]Thank you for your insight on this one guys...the question is, can a file system mount check be done at any time? Maybe forced? (from what I've read, it's not good to force things in Linux) I'd like to incorporate it into a scheduling routine above and beyond the required forced ones. Or maybe someone could tell me where the forced checks come from so maybe that file could be altered?
......[/QUOTE]
The boot checks of the efs2 filesystems are actually set in the individual filesystems themselves, and can be set to occur after fixed time periods and/or numbers of mount cycles:

[http://ubuntuforums.org/showthread.php?t=139783](http://ubuntuforums.org/showthread.php?t=139783)

---

