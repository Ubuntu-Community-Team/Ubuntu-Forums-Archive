---
title: "Shell question - what does &quot;bareword not allowed&quot; mean?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by soulgt on 2008-01-23
I was trying to move my just-downloaded eclipse pdt folder to /usr/lib, and accidentally typed the command incorrectly:

```
mv eclipse /usr/bin/lib
```

This renamed the eclipse folder to 'lib'. To fix the mistake, I decide to rename and move it to where I want it, but when I type:

```
rename lib eclipse
```

I get the following message:

```
Bareword "lib" not allowed while "strict subs" in use at (eval 1) line 1.

```

I googled it, and all I could find was that it had something to do with perl. Is there any way for me to rename this directory without copying all the contents into a new eclipse directory and deleting the old 'lib' directory (though I fear it might not let me do that).

And out of curiosity and for the sake of moving up the linux learning curve, what does 'bareword not allowed' mean?

---

### Post by PeterJS on 2008-01-23
In unix there is no concept of renaming things. To accomplish what appears like renaming something is to move it to a new name without moving it out of it's parent's directory. So to rename a directory you would use:
```

mv -R oldname newname

```

The rename program is for bulk renaming files using the perl regular expression engine.

---

### Post by Terry of Astoria on 2008-01-23
I love linux.

---

