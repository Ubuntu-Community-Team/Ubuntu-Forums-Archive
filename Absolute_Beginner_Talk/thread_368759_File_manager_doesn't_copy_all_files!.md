---
title: "File manager doesn't copy all files!"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-23
I'm trying to copy a series of files (to back 'em up).
However on a number -- not all! -- of them I get:  "cp:  cannot create directory ... invalid argument" and "cp:  cannot create regular file ... invalid argument".
This happens both with emelFM and emelFM2 file managers.
I have already changed permissions and checked ownership, but to no avail.:confused:

---

### Post by netkid91 on 2007-02-23
Are you sure there is enough space available?  Could you try doing it through the console using the -v to watch what it's doing?

---

### Post by houstonbofh on 2007-02-23
Can you copy the files that do not copy individually?

---

### Post by Blofeld on 2007-02-23
There is enough space on the target medium.
I can't copy the "resistant files" individually.
When I use the cp -r command instead of the file manager (emelFM)  the obstreperous files still refuse to move.
But I have found out that one file which doesn't copy contains double quotation marks (").  When I change those to single quotation marks (') they do copy.
So the problem seems to be illegal characters in the file name.  I'm just surprised that I can create those file names, but then can't copy the files.
Thanks for the pointers, guys.

---

### Post by netkid91 on 2007-02-23
Double quotes are not illegal under Linux, however like any other character of it's sort, it needs to be escaped with and \.  Seems that emelFM forgets to do this.

---

### Post by Blofeld on 2007-02-23
Thanks for the swift reply, kiddo.  I think you're right on the money.

---

### Post by Blofeld on 2007-02-23
Accent grave-d letters (è) are also not being copied.  Accent grave is not an illegal character though, or is it?

---

### Post by Blofeld on 2007-02-23
OK, I copied those files from a Mac to a Linux box.  Apparently some characters, such as è got "corrupted" in the process (replaced by those question mark-placeholder-signs), others are just plain illegal, or at least problematic, under Linux.

---

### Post by Blofeld on 2007-02-23
Umlaute (ö, ä, ü, Ö, Ä, Ü) seem to be OK though.   Phew!

---

### Post by netkid91 on 2007-02-26
Sorry for taking so long, had a lot going on this weekend.  Glad that helped.  need anything else just ask, that's why I'm here.

---

### Post by Blofeld on 2007-02-26
@Netkid:  Cheers, mate.

---

