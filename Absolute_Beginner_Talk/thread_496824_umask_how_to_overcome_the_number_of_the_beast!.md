---
title: "umask: how to overcome the number of the beast!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2007-07-09
I am trying to understand how umask works on my system.  I know that I could probably change the defaults using a configuration file, like .bashrc or /etc/profile or even /etc/fstab  However, I want to type umask in a terminal and use the new umask for that session.

The only problem is that I can't make execute permissions with umask.  For some reason, the default that umask is subtracting from is 666 not 777  Some examples:

umask=0000
touch filename testfile
ls -l testfile
-rw-rw-rw- testfile
rm testfile

The permissions should really be -rwxrwxrwx
----------------------------------------------------------------


umask=0111
touch filename testfile
ls -l testfile
-rw-rw-rw- testfile
rm testfile

The permissions are correct.  Notice the result is identical to the previous example of umask=0000
----------------------------------------------------------------

umask=0022
touch filename testfile
 ls -l testfile
 -rw-r--r-- testfile
 rm testfile

The permissions should really be -rwxr-xr-x
----------------------------------------------------------------

In all cases, the umask is applied to a default value of 666 not 777.  In other words, I can't use umask to create execute permissions.

Does anybody know what is going on here?

---

### Post by dstew on 2007-07-09
The umask value is not subtracted. The unary complement of the umask value is ANDed with the full permission value, which for files in octal is 666. So, umask 000 would give ((NOT 000) AND 666). The octal value of NOT 000 is 777, so 777 AND 666 = 666, or rw-rw-rw-. If umask is 111, then (NOT 111) AND 666 = 666 AND 666 = 666! Simple! See the [Wikipedia article]("http://en.wikipedia.org/wiki/Umask").

umask 022 = (NOT(022) AND 666) = (755 AND 666) = 644 = rw-r--r--.

Why anybody created such a scheme is not readily apparent!

EDIT: I think you may be correct that you cannot create executable privleges for files with umask.

ANOTHER EDIT: How umask behaves may depend on the shell you are using. On the man page, it looks like sh and ksh may be different.

---

