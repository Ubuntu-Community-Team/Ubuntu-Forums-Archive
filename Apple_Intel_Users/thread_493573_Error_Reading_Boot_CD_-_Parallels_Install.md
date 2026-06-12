---
title: "Error Reading Boot CD - Parallels Install"
date: 2007-07-05
forum: Apple Intel Users
---

### Post by jgaston on 2007-07-05
I am trying to install Ubuntu 7.04 in Parallels 3.0 on a Mac PowerBook Pro using the downloaded .iso file.  I step through the process fine, but when Ubuntu gets to the boot screen I get this message no matter which option I select:

I/O Error: Error reading boot CD (see attached screenshot).

I've done a lot of Googling and have not found this exact error.  I have tried the trick used on the prior version of Parallels of selecting Solaris OS initially and then switching to Unix, but that didn't work either.

I don't understand why it thinks it need to read a boot CD when I directed it to the .iso file on the hard drive.  I copied the .iso file to a CD and tried that and still got the same message.

Anyone have any ideas?  Any help would be appreciated!

---

### Post by cyberdork33 on 2007-07-06
Parallels makes a 'virtual' cd-rom from your iso file. Ubuntu will see it as a real cd-rom.

I am guessing bad download, especially since you get the same error when trying to use your real cd-rom. Try downloading again.

BTW, Parallels runs on PowerBooks? I thought it required an Intel Mac...

---

### Post by jgaston on 2007-07-06
That did it - thanks!  I should have tried that myself.  I mistyped.  I'm running it on a MacBook Pro, not PowerBook.

The help is appreciated.

jg

---

### Post by cyberdork33 on 2007-07-06
Glad to help.

---

