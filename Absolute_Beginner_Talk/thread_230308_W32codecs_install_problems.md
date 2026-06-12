---
title: "W32codecs install problems"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-05
Hi
Can't get RhythmBox to play today (although I've never had a problem before).
So, I tried downloading the codecs again but the Windows Codecs (w32codecs) are proving troublesome.
After downloading with this command

```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb
```

I then try to install with this:

```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

but get this error message:

> dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb


Anybody know what this means and what I can do?

Thanks
Paul

---

### Post by Jagot on 2006-08-05
EDIT:  Or indeed ewl1217 may be correct below - didn't notice the file name.  Silly me . . .

---

### Post by ewl1217 on 2006-08-05
It looks like you typed the wrong file name with the "dpkg" command. Double check the name and try it again.

---

### Post by lamego on 2006-08-05
That means you made a typo:
You have downloaded: w32codecs_20060611-1plf1_i386.deb
And you are trying to install: w32codecs_20060611-0.0_i386.deb

---

### Post by ColdDeath on 2006-08-05
In future you can use tab completion to stop this problem from happening again. 

If you start writing out the file name and then press [tab] it will fill the rest of the filename in for you, try it!

:razz:

---

### Post by PaulFXH on 2006-08-05
Thanks to everybody for the quick replies.
However, I didn't actually type ANYTHING, so it wasn't a typo on my part.
I actually got the two commands from the Ubuntu wiki and the relevant page is here:

> [https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

and, yes, it does look like there's a typo here.
Anyway, I tried it again and used TAB to complete the file name in the second command and got the codec installed.

Best wishes
Paul

---

