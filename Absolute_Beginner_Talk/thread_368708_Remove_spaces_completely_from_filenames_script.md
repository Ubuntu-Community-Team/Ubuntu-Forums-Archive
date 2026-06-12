---
title: "Remove spaces completely from filenames script"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by dccmyst on 2007-02-23
I use this script to replace spaces in filenames with underscores. How do I alter this script to just remove the spaces. The new filename must have no underscore nothing.

eg.

Annoying Filename.mp3
to AnnoyingFilename.mp3

I've tried changing 

newname=`echo "$name" | tr " " "_"`
to newname=`echo "$name" | tr " " ""`

but this returns an error: 

tr: when not truncating set1, string2 must be non-empty



```
#!/bin/bash

IFS='

'

j=`find $1 -printf "%d\n" | sort -u | tail -n 1`

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

#####################
```

I've been trying to get this to work for some time, I have a load of mp3s I want to rename

---

### Post by dccmyst on 2007-02-24
Bump.

---

### Post by highneko on 2007-02-24
There's a program called rename that works great for stuff like removing spaces from filenames. If that's what you want then this'll help:
```
[COLOR="DimGray"]# Test it out by using the -n option[/COLOR]
rename -n 's/ //g' "filename with spaces"
[COLOR="DimGray"]# Same thing but with globbing:[/COLOR]
rename -n 's/ //g' *.ext
```

---

### Post by xenmax on 2007-02-24
Try ```
newname=`echo "$name" | tr -d " "`
```

---

### Post by highneko on 2007-02-24
Another way for renaming could be:
```
for i in *.mp3; do mv -i "$i" "${i// }"; done
man bash # search for parameter expansion
```

---

### Post by dccmyst on 2007-02-24
thank you xenmax, that did the trick.

---

