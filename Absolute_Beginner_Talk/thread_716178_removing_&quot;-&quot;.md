---
title: "removing &quot;-&quot;"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Fred10 on 2008-03-05
Hi,

I have a bunch of files like "image_year-month-day.pgn" and I wanted to remove the "-".

The problem is that I have file like 
"image_2008-1-11.png" and
"image_2008-11-1.png" which give the same thing when I'm using 

rename 's/-//g' *.png

Is anybody have an idea?
Thanks

---

### Post by Oldsoldier2003 on 2008-03-05
thunar/buk rename? yeah its gui but its nice...

---

### Post by mali2297 on 2008-03-05
What do you want to rename them to?
"image_20080111.png" and "image_20081101.png"?

---

### Post by spupy on 2008-03-05
_**EDIT: Please, disregard this, i didn't read your post very carefully. :(**_

---

### Post by spupy on 2008-03-05
Wow, i think i got the script! :D It is an abomination of code, but i think it works. It replaces "-" before single digits with "0", and remover "-" before two digit numbers.
For example:
 image_2008-1-11.png ->  image_20080111.png
 image_2008-1-1.png ->  image_20080101.png
 image_2008-11-11.png ->  image_20081111.png

Here is the monster (lol):
**_BEFORE running this, please make a backup copy of the files, just in case!_**
```
#!/bin/bash
ls -l *png | awk '{print $9}' | while read oldname
do
  echo $oldname | grep -o -e '-[0-9]\{1,2\}-[0-9]\{1,2\}.' | grep -o -e '[0-9]\{2\}' | 
	while read qwe
		do
			newname=`echo $oldname | sed "s/-$qwe/$qwe/"`
			mv $oldname $newname
			oldname=`echo $newname`
		done
done

ls -l *png | awk '{print $9}' | while read oldname
do
	newname=`echo $oldname | sed 's/-/0/g'`
	mv $oldname $newname
done
```

Just don't ask me how it works! ;) You better thank me for that! :lolflag:

---

### Post by ghostdog74 on 2008-03-05
> **Fred10 said:**
> Hi,

I have a bunch of files like "image_year-month-day.pgn" and I wanted to remove the "-".

The problem is that I have file like 
"image_2008-1-11.png" and
"image_2008-11-1.png" which give the same thing when I'm using 

rename 's/-//g' *.png

Is anybody have an idea?
Thanks

```

for file in *png
do
 newfile=${file//-/}
 mv "$file" "$newfile"
done

```

---

### Post by spupy on 2008-03-06
> **ghostdog74 said:**
> ```

for file in *png
do
 newfile=${file//-/}
 mv "$file" "$newfile"
done

```

Hm, yeah, that would be easy, but, as he said, if he has two filenames named like that:
image_2008-1-11.png and
image_2008-11-1.png
they get mv-ed to one file. That's way my script is so bloated.

---

### Post by ghostdog74 on 2008-03-06
```

ls -1 *.png | awk 'BEGIN{ OFS=FS="-";}
{
 oldfile=$0
 if(length($2)==1) $2="0"$2
 sub(/ +$/,"",$0)
 cmd="mv " oldfile " " $0
 print cmd
 #system(cmd) # uncomment to use
}' 

```

---

### Post by spupy on 2008-03-06
YAY! Battle of scripts! :D

---

