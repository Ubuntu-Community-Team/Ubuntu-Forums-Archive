---
title: "How do I move a large amount of files with root priveleges?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by supazio on 2007-06-25
I have around 50 files that I need to move somewhere, but the destination requires root privileges, so my question is: how can I a) move the contents (but not the folder) of a folder in the terminal (without doing 'sudo mv 'ALL THE FILES'") or b) drag and drop graphically in sudo.

---

### Post by Steveway on 2007-06-25
You can do this:
$gksudo nautilus --no-desktop
or
$gksudo thunar
depending on the filemanager you wish to use.

---

### Post by PiratePhysicist on 2007-06-25
If you use a wildcard (an asterisk *) then it will apply to all of the files, so:

sudo mv test/* test2

Will move all of the files from test to test2 (unless there are folders in test, then you will need to use the flag -r which will cause it to copy the folder too)

---

### Post by supazio on 2007-06-25
I tried the nautilus command, but I got this:
"supazio@dellbox:~$ gksudo nautilus --no-desktop
gksudo: unrecognized option `--no-desktop'"

---

### Post by jackmc on 2007-06-25
I just do sudo nautilus, works for me...

---

