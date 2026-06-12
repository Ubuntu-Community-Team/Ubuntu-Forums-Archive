---
title: "find -type expression"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-04-10
How do I use the -type expression in the find command?

I tried this:
```

find . -type "ASCII text"

```
And didn't work!

---

### Post by htinn on 2006-04-10
I think you're thinking of the -type f option, i.e.:

```
find . -type f "some text"
```

---

### Post by tux101 on 2006-04-10
Didn't work either.  Failed to list all ASCII text files.
```
find . -type f "ASCII text"
find: paths must precede expression
Usage: find [path...] [expression]

```

---

### Post by htinn on 2006-04-10
Hmm, something amiss...

Perhaps you meant to grep?

```
find . -type f | grep "find this"
```

---

### Post by tux101 on 2006-04-10
No output.

How do I find files that have no extensions like text files?

---

### Post by tux101 on 2006-04-11
Still need help.  Please?

---

### Post by markmark on 2006-04-11
I don't know that you can use find to return all text files. -type will allow you to return just sym-links or just directories or just regular files, but I don't think it can pick out text files from binary files.

---

### Post by 5-HT on 2006-04-11
[quote=markmark]I don't know that you can use find to return all text files. -type will allow you to return just sym-links or just directories or just regular files, but I don't think it can pick out text files from binary files.[/quote] 
As markmark said, there is no easy way for the utility to find specific file types. The -type option is for directories, files, sym links, etc.

There would probably be a fancy way of doing this somehow involving redirection or piping, and an edited output of the 'file' command being factored in somewhere, but I wouldn't know off-hand.

However, if the ASCII files as a whole have a unique extension(s), you could just ask 'find' to look for those extensions:

```
 find <path> -iname *.<extension> 
``` 
For example:

```
 find ~/ -iname *.txt 
``` 


If the files do not have (unique) extensions, the manual pages for find, file, and sed may come in handy if you want to figure out how to search to specific file types. Also, if you are not familiar with I/O redirection or piping, the bash manual will be of help. To read them:
```
man find
man file
man sed
man bash      *This one is long, just look for the sections on redirection and piping 
``` 
HTH

---

