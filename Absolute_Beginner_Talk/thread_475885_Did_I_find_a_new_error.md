---
title: "Did I find a new error?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-16
I've had no response to my query about mode 0446 and a thorough search of the forums and documentation suggests there is no such thing.

To repeat, "sudo visudo" yeilds a message that sudo: /etc/sudoers/ is mode 0446, should be 0448.

Dave

---

### Post by skymera on 2007-06-16
i dont understand what you mean.

well , heh, i bumped :)

---

### Post by machoo02 on 2007-06-16
Mode 0448?  That doesn't make much sense...when using numeric mode to set permissions the highest value is 7 (4+2+1).  Are you sure it says 0448 and not 0440?  Everything that I've read about the /etc/sudoers file says that it should be 0440.

---

### Post by Jimmyfj on 2007-06-16
Hi 

Doesn't seem that you have. Just by googling the number in two different ways I found that either it has to do with your ACPI not been configured, or it has to do with graphics Google-search turning up an error for that number in operating a 3DFX woodoo card. You can foofle for even more messages on the subject.

---

### Post by machoo02 on 2007-06-16
> **Jimmyfj said:**
> Hi 

Doesn't seem that you have. Just by googling the number in two different ways I found that either it has to do with your ACPI not been configured, or it has to do with graphics Google-search turning up an error for that number in operating a 3DFX woodoo card. You can foofle for even more messages on the subject.

No...Mode errors like the one that Mallette described indicates a problem with file access permissions.  In this case, the /etc/sudoers file had the wrong permissions set to it:
0446 - owner and group can read only (4), everyone else can read/write (6 - bad idea, especially for this file!!!!)

the proper permissions for the /etc/sudoers file is:
0440 - owner and group can read only, everyone else can do nothing with it (last zero)

---

### Post by Mallette on 2007-06-16
Yep, machoo2 nailed it.

I DID have the number wrong and later edited it.  However, I could not find any references to mode anywhere in documentation and only the one obscure reference I quoted in my "Going down for the third time..." thread in a general google search.

What I found very strange was that the sudoer file did not reference this number at all.  Machoo2 provided a cli "chmod" command that did the trick.

I still do not know how this happened in the first place...

Dave

---

