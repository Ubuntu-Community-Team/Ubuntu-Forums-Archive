---
title: "[SOLVED] How to remove xfprot-1.19 from desktop?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-10-30
Hi all,

I downloaded and installed xfprot-1.19 to the desktop, but because of inconsistencies in various guides some mistakes must have been made.  As a result, I wish to be able to remove a directory called xfprot-1.19 (Fprot antivirus) from the desktop but without success.  Here's what the terminal looks like:

root@hoe1-laptop:/home/hoe1/Desktop# rm -i xfprot-1.19
rm: cannot remove directory `xfprot-1.19': Is a directory
root@hoe1-laptop:/home/hoe1/Desktop# dpkg --remove fp-linux-ws
dpkg: dependency problems prevent removal of fp-linux-ws:
 xfprot depends on fp-linux-ws.
dpkg: error processing fp-linux-ws (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 fp-linux-ws

Is there anyway to completely remove all directories and files associated with f-prot antivirus?:confused:

---

### Post by Maestro23 on 2007-10-30
> **iClouseau88 said:**
> Hi all,

I downloaded and installed xfprot-1.19 to the desktop, but because of inconsistencies in various guides some mistakes must have been made.  As a result, I wish to be able to remove a directory called xfprot-1.19 (Fprot antivirus) from the desktop but without success.  Here's what the terminal looks like:

root@hoe1-laptop:/home/hoe1/Desktop# rm -i xfprot-1.19
rm: cannot remove directory `xfprot-1.19': Is a directory
root@hoe1-laptop:/home/hoe1/Desktop# dpkg --remove fp-linux-ws
dpkg: dependency problems prevent removal of fp-linux-ws:
 xfprot depends on fp-linux-ws.
dpkg: error processing fp-linux-ws (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 fp-linux-ws

Is there anyway to completely remove all directories and files associated with f-prot antivirus?:confused:

Can do a:

> rm -r "xfprot-1.19"

Should delete the directory off the Desktop.

---

### Post by iClouseau88 on 2007-10-30
> **Maestro23 said:**
> Can do a:

rm -r xfprot-1.19

Should delete the directory off the Desktop.

Thank you kindly for your help.  This problem has been bugging me for some time, as none of the Linux books I read shows your type of solution.

---

### Post by Maestro23 on 2007-10-30
> **iClouseau88 said:**
> Thank you kindly for your help.  This problem has been bugging me for some time, as none of the Linux books I read shows your type of solution.

No prob man.  That's just one way to do it.  Some things can be done multiple ways in Linux.:guitar:

Glad it worked.

---

