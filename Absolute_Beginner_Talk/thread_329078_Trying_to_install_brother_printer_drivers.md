---
title: "Trying to install brother printer drivers"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by cashman3 on 2006-12-31
OK I know im slow at this but here is were I am at. I am trying to install the drivers for a brother mfc7220 i got the drivers from there site. Am i right when i got the drivers for debian? Then my next question is how do i go about this?

---

### Post by PatrickMay16 on 2006-12-31
I'd say you were right in choosing the driver for Debian, since Ubuntu is based on Debian.

Is this in the form of a .deb file? If so, doing this in a terminal:

sudo dpkg -i file.deb 

will install it.

If not, what kind of file is it?

---

### Post by cashman3 on 2006-12-31
It is a .deb but i get the error message of error processing brmfc7220lpr-2.0.0-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brmfc7220lpr-2.0.0-1.i386.deb

---

### Post by PatrickMay16 on 2006-12-31
> **cashman3 said:**
> It is a .deb but i get the error message of error processing brmfc7220lpr-2.0.0-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 brmfc7220lpr-2.0.0-1.i386.deb

You need to change to the directory that the deb file is in before running the command.
For example, is the deb file on your desktop? Then you would type

cd Desktop

Then run the "sudo dpkg -i file.deb" command again; this time it should work.

---

