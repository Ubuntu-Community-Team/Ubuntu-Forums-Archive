---
title: ".deb package problem"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by H_Roark on 2005-07-12
I downloaded a tarball of a secure delete utility, and unpacked it.  When I tried to install it using dpkg -i, I got the message that it could not find the file.  Using the GUI, I moved the whole thing into the /tmp file.  The LS command will list it, but the same problem continues.  Anyone have any idea how to install this?

Failing that, is there a secure delete tool located in one of the repositories?  If so, where?

Thanks in advance.

---

### Post by musicman2059 on 2005-07-12
That's because you can't dpkg a tarball.  It has to be compiled manually using the ./configure, make, make install method, but it can get pretty hairy to do if you're not an advanced linux user.

---

### Post by H_Roark on 2005-07-12
[QUOTE=musicman2059]That's because you can't dpkg a tarball.  It has to be compiled manually using the ./configure, make, make install method, but it can get pretty hairy to do if you're not an advanced linux user.[/QUOTE]

Ah, well that explains it.  Is there a guide on how to compile it anywhere?
BTW-the original file had a .deb extension.  Does the above still apply there?

---

### Post by musicman2059 on 2005-07-12
[quote=H_Roark]BTW-the original file had a .deb extension. Does the above still apply there?[/quote]

Alright, you got me there.  Are you saying that there's a .deb and a .tar.gz, or that it's a .deb that was somehow renamed to .tar.gz? (The latter makes no sense to me whatsoever)

As for compiling, most .tar.gzs have a file named INSTALL, or in some cases README, (look for README.Debian for Debian-specific info) and it should give you a bit of a guide on how to get it installed.

---

### Post by H_Roark on 2005-07-12
[QUOTE=musicman2059]Alright, you got me there.  Are you saying that there's a .deb and a .tar.gz, or that it's a .deb that was somehow renamed to .tar.gz? (The latter makes no sense to me whatsoever)

As for compiling, most .tar.gzs have a file named INSTALL, or in some cases README, (look for README.Debian for Debian-specific info) and it should give you a bit of a guide on how to get it installed.[/QUOTE]

I was wrong-the .deb file is something else I'm going to install.  I think this one requires the manual compile.

---

