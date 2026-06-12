---
title: "OpenOffice only works when I log in as root"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by rmccabe3701 on 2007-08-31
I recently installed Ubuntu 7.04 and immediately after installation OpenOffice worked fine.  Then I spent a few hours getting dual monitor functionality ... after this I found that none of the OpenOffice software worked -- I get a pop-up window which says: 

```

"The application cannot be started.  An internal error occurred." 

```
 However, if I do the following

```

sudo oowriter

```

it works fine.

Maybe I messed up some permissions when I was playing around with the dual monitor stuff.  Any Ideas how to fix?

---

### Post by Celegorm on 2007-08-31
Try ```
ls -l /usr/bin/oowriter
``` to see what the permissions for it are (assuming that is where you have it installed, use "which oowriter" to find out which directory it's in) The default permissions for it should be -rwxr-xr-x. Those last three characters tell you what permissions everyone has for it. r, w, and x stand for read, write, and execute, and '-' implies that a particular permission is not given. In this example the 'r-x' at the end means anyone can read and execute the file, but not write it. If these permission are different for you, try ```
sudo chmod +rx /usr/bin/oowriter
``` to give everyone read and execute permissions again.

---

### Post by FuturePilot on 2007-08-31
Perhaps try deleting your .openoffice.org2 file in your home folder. It's hidden so View>Show Hidden Files.

---

### Post by viciouslime on 2007-08-31
> **FuturePilot said:**
> Perhaps try deleting your .openoffice.org2 file in your home folder. It's hidden so View>Show Hidden Files.

This sounds like the best idea :)

---

