---
title: "How do I remove, not replaces spaces in filenames"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by dccmyst on 2007-02-16
I use this script to replaces spaces in filenames with underscores. How do I alter this script to just remove the spaces. The new filename must have no underscore nothing. 

eg. 

Annoying Filename.mp3 
to AnnoyingFilename.mp3. 

```


#!/bin/bash
IFS='
'
j=`find $1 -printf "%d\n" | sort -u | tail -n 1`
j=$((j-1))
echo "Max dir depth:" $j
for (( i=0; i<=j ; i++ ))
do
for name in `find -mindepth $i -maxdepth $i -iname "* *" -printf "%p\n"`
do
newname=`echo "$name" | tr " " "_"`
echo "$name" "$newname"
mv "$name" "$newname"
done
done
##########

```

As well, I was wondering if this is in any programming language? what syntax should you use in scripts?

Excuse the noobness.

---

### Post by LotsOfPhil on 2007-02-16
It's a bash script.

If you want to get rid of underscores, change the 

newname=`echo "$name" | tr " " "_"`

-to-

newname=`echo "$name" | tr " " ""`

Just delete the underscore, keep the " marks.

---

