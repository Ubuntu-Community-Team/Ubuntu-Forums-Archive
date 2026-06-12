---
title: "KDE programs stopped working"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by blagh on 2007-05-29
I updated the linux headers this morning, and on restart everything KDE isn't working properly, if at all.  I'm not using Kubuntu (although I probably should be, half of what I run seems to be KDE nowadays), but I didn't have this issue before.

Every time I try to start a KDE program, it gives me the following error:

[indent]There was an error setting up inter-process communication for KDE.  The message returned by the system was:

Could not open network socket

Please check that the "dcopserver" program is running![/indent]

dcopserver doesn't show up in my Sessions window, so I tried starting it on the command line and it gave me this:

[INDENT]hannele@megabyte:~$ dcopserver
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/hannele/.DCOPserver_megabyte__0
and start dcopserver again.
---------------------------------[/INDENT]

Searching the forums turned up [a]("http://ubuntuforums.org/showthread.php?t=107269") [few]("http://ubuntuforums.org/showthread.php?p=2627024") [threads]("http://ubuntuforums.org/showthread.php?t=174130"), but these seem to be all permissions issues, and a chmod didn't help.

Should dcopserver be showing up in the Sessions, and should I hence be following these instructions?  Much thanks!

---

### Post by Delkster on 2007-05-29
> **blagh said:**
> ---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/hannele/.DCOPserver_megabyte__0
and start dcopserver again.
---------------------------------
Have you checked if a dcopserver process is actually running? You could use the process list in System Monitor for that, or you could do something like "pgrep dcopserver" or "ps aux | fgrep dcopserver | fgrep -v fgrep" on the command line and see if anything comes up.

If it isn't actually running, have you tried removing the temporary file suggested by the error message?

> Should dcopserver be showing up in the Sessions, and should I hence be following these instructions?

No, you needn't have it in Sessions.

---

### Post by blagh on 2007-05-29
Ah, thanks for the patience with a Linux noob!  I thought I might've been looking for processes in the wrong place.  dcopserver wasn't there, so I deleted the file, and things started mostly working again.  They still had issues with finding klauncher for some reason, but a reboot fixed that.

---

