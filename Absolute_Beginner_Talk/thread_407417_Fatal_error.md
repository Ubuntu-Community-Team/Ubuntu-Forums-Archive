---
title: "Fatal error"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by geck07 on 2007-04-12
When i start my computer i get an error warning:



                                    A fatal error has occured-yakuake

Konsole is unable to open a PTY (pseudo teletype).It is likely that this is due to an incorrect configuration of the PTY devices.Konsole needs to have read/write access to the PTY devices.



please tell me what to do.I tried to kill yakuake but no use.The warning message still pops up.

Thanks a lot in advance

Geck07

---

### Post by dstew on 2007-04-12
Two possible causes:

1. Somehow your shell preference has been removed from your user information that is stored in /etc/passwd. You can look at this with sudo cat /etc/passwd. If you do not see /bin/bash at the end of your line, edit it.

2. The process yakuake could not create a pseudo-terminal in the /dev/pts directory. I don't know much about yakuake, but maybe it needs to be installed with the superuser bit on, since the /dev/pts directory is owned by root.

---

