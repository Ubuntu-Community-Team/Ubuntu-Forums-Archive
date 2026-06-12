---
title: "Xserver problem"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by prem1er on 2008-03-31
I can no longer run xserver over ssh.  When I try to 'startx' on the server I get this error.  Thanks in advance.

Fatal server error:
No valid FontPath could be found.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

---

### Post by rkd on 2008-03-31
What can you remember that happened with the computer since the last time you could do that successfully?

Did you reconfigure X?
Did you install or uninstall any fonts?
Did you make any changes at all to the computer?

If you want to do some quick investigating on your own, open the file /etc/X11/xorg.conf using your favorite editor, and look for lines that begin with FontPath.  They might look like this:```
FontPath        "/usr/share/X11/fonts/misc"
```
Or they might have slightly different names.  Then look to see whether any of the files named on those FontPath lines are present in your computer.

---

