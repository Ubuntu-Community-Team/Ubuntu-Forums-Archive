---
title: "Here we go loop de loop ... I wish!"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Langstracht on 2006-08-21
I would like a script which will examine the files in a directory
and, depending on a substring in the filename, delete, rename or copy into
another directory.

I've only tried one eventuality so far and ... it doesn't work.  Nor
does a number of alternatives I've tried (with/without $, ', ").  So,
to copy IWISHTHISabcWASNTHAPPENING I tried:

#!/bin/sh
cd old_directory
for loop in "ls -1 *"
do
if [ '$loop'='*abc*' ] ; then
cp '$loop' new_directory
fi
done

I understood, perhaps incorrectly, that the "$loop" variable
sequentially took on all the filenames in the directory.  It would appear
not. 

I'd appreciate any help in getting this to work.

TIA

---

### Post by hw-tph on 2006-08-21
You could use the very powerful **find** tool to do the same with less effort:
```
find . -name "*abc*" -exec mv {} /path/to/new_directory/ \;
```

The period (dot) indicates "this directory", -exec means execute, {} indicates the match (the same command is performed for each match and {} is replaced by the actual filename). So "mv {} /path/to/new_directory/" will expand to "mv IWISHTHISabcWASNTHAPPENING /path/to/new_directory" and do the same for HELLNOabcNOTTHISAGAIN too if a file named like that would exist. The escaped semicolon "\;" terminates the exec command.

Note that find will walk recursively through directories. You can limit this behaviour using the -maxdepth option.

Read find(1) for more information (type **man 1 find**).

Håkan

---

### Post by Langstracht on 2006-08-21
Wow!  

You're absolutely right!  Works like a charm.

Tack sa mycket.

---

