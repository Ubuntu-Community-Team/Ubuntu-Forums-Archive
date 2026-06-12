---
title: "How to search for various file extensions?"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-14
Well, I am trying to search all .c and .tt files, but I don't know how. In the help file it says for one-letter file extensions.

---

### Post by Baka no Kami on 2007-10-14
The best I know to tell you is "find -name *c" or "*tt".  That should list every file ending in c or tt in the current dir and all sub dirs.  If there's a better way...

---

### Post by niteshifter on 2007-10-14
The find command:

```
foo@bar:~$ find / -name *\.c
```

```
foo@bar:~$ find / -name *\.tt
```

Now as to what that means / does:

The / specifies the starting point for the search, in this case the root of the filesystem. You can specify any path here e.g. /var/log  or /home etc.

The -name means look at filenames.

And last is the "regular expression" or pattern you wish to match:
  * any sequence of characters
  \. the \ is "escaping" the . ( . has meaning in pattern searches ) so this is saying treat the . as a plain character so as to match it.

---

### Post by hyper_ch on 2007-10-15
well, instead of find you could also use "locate". Locate uses the slocate database and it's faster than using find which crawls the whole system.

If you ahve freshly added files that you want to search, they may not be in the slocate db yet but you can manually update it:

```

sudo updatedb

```

And then look for them like:
```

locate *\.EXT

```

where EXT of course is the desired file extension.

---

