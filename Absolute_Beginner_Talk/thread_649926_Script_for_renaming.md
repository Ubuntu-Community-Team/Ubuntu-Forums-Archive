---
title: "Script for renaming"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by caclratm on 2007-12-25
Hi, I'm really new at linux and I want to know if it's possible to write an script for replacing the underscore characters in a certain folder's files filenames with blankspace. Basically renaming something like:

"a_certain_filename.ext"

into:

"a certain filename.ext".

Thanks in advance.

---

### Post by Capricori on 2007-12-25
It is possible, in fact, I think I have something lying around here that will do the job...
I'll get back to ya if I find it :)
I would imagine that one line of sed or awk could do the job.

Regards, 

Capricori

---

### Post by Capricori on 2007-12-25
I found the code below, which does the opposite - it would rename "Sample file.txt" to "Sample_file.txt".
It should be pretty easy to modify it to get it to do the opposite though.

Just a word of warning, I don't understand half of this script, so I would wait for someone else to verify it, or come up with a better solution. In short - I can't guarentee it won't do something it shouldn't.
I also don't remember where I got it from, so I can't give credit to the author.

On that note, here's the code.
```
#!/bin/bash
files=$(ls -dQ1 ~/*.* && ls -d1Q ~/*/*.* && ls -d1Q ~/*/*/*.* && ls -d1Q ~/*/*/*/*.* && ls -d1Q ~/*/*/*/*/*.* && ls -d1Q ~/*/*/*/*/*/*.* && ls -d1Q ~/*/*/*/*/*/*/*.*)

if [ -n "$1" ]
then
  if [ -d "$1" ] 
  then
    cd "$1"
  else
    echo invalid directory
    exit
  fi
fi

for i in *
do
  OLDNAME="$i"
  NEWNAME=`echo "$i" | tr ' ' '_' | tr A-Z a-z | sed s/_-_/-/g`
  if [ "$NEWNAME" != "$OLDNAME" ]
  then
    TMPNAME="$i"_TMP 
    echo ""
    mv -v -- "$OLDNAME" "$TMPNAME"
    mv -v -- "$TMPNAME" "$NEWNAME"
  fi
  if [ -d "$NEWNAME" ] 
  then
    echo Recursing lowercase for directory "$NEWNAME"
    $0 "$NEWNAME"
fi
done
```

---

### Post by caclratm on 2007-12-25
Ok, thanks a lot anyway :D.

---

### Post by nick_h on 2007-12-26
There is an easier method - you can use the rename command.
```
rename 's/_/ /g' *.ext
```

---

### Post by caclratm on 2007-12-26
Thanks a lot. It worked like a charm...

---

### Post by Capricori on 2007-12-28
> **nick_h said:**
> There is an easier method - you can use the rename command.
```
rename 's/_/ /g' *.ext
```

Ahh, I love it when I find out that a one-liner could replace a whole script I was using :)

---

### Post by nick_h on 2007-12-29
> Ahh, I love it when I find out that a one-liner could replace a whole script I was using
Your script did more than a single rename - it handled sub-directories.  It also changed the filename to lowercase and removed the spaces around a hyphen.

It also renamed the file to a temporary file first.  I expect that is to ensure that the file gets renamed when just changing from uppercase to lowercase on a FAT filessystem.

---

### Post by Capricori on 2007-12-29
It does? :S

As I said, it isn't my script, and I never actually got round to using it...

I gotta learn some of this stuff...

---

