---
title: "Bash character ranges"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by curtisf14 on 2006-09-30
I'm learning how to use the bash shell, but I'm finding that uppercase vs. lowercase character ranges are behaving stragely when I use "[a-z]" and "[A-Z]".  For example, I go to "~/Desktop" and run

```

echo "test" >> testfile
echo "test" >> Testfile

```

then, if I do something like "ls [A-Z]*", it prints out both "testfile" and "Testfile".  Here are the results of some my tests:

```

$ ls [A-Z]*
testfile  Testfile
$ ls [a-z]*
testfile  Testfile
$ ls T*
Testfile
$ ls [T]*
Testfile
$ ls [T-T]*
Testfile
$ ls [S-T]*
testfile  Testfile
$ ls [!a-z]*
ls: [!a-z]*: No such file or directory
$ ls [!t]*
Testfile

```

Any ideas on what's going on here?  Thanks!

---

### Post by steve.horsley on 2006-09-30
It is all down to command line expansion in bash. You will find that the command **echo [A-Z]** gives the same results. For details, use the command **man bash** and search for **Pathname Expansion**. As with all the bash help, it's very terse and not very helpful. But apparently the A-Z forms a range expression, and that uses the "current locale's collating sequence" whatever that means.

---

### Post by curtisf14 on 2006-10-01
After looking at "man bash" and doing some internet searching, I found that putting the following in my .bash_profile file will fix the problem:

```

export LC_COLLATE=C

```

Weird, huh?  It seems that it's not set to anything by default (or at least anything I can see by doing "echo $LC<TAB><TAB>" on the command line), but "LC_COLLATE=C" or "LC_COLLATE=en" seem to be standard variable values.  I found this solution here: [http://www.zsh.org/mla/users/1998/msg00741.html]("http://www.zsh.org/mla/users/1998/msg00741.html").  Even though this is for the Z-shell, it seems to work for bash too.

---

