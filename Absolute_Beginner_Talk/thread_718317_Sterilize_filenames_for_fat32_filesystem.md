---
title: "Sterilize filenames for fat32 filesystem"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by lucasl on 2008-03-08
Hi,
I'm trying to copy music to my iPod, but I get the error "cp: cannot stat: ..." because of funny filenames such as &#345;, á, &#283;. I'm guessing XFS uses utf8 but Fat32 doesn't, or something similar.
Is there an easy way to replace these letters with their normal counterparts or simply get rid of them (preferably recursively)?

Thanks,
Lucas

PS. There are so many odd characters that simply using some regex isn't an option.

---

### Post by lloyd_b on 2008-03-08
> **lucasl said:**
> Hi,
I'm trying to copy music to my iPod, but I get the error "cp: cannot stat: ..." because of funny filenames such as &#345;, á, &#283;. I'm guessing XFS uses utf8 but Fat32 doesn't, or something similar.
Is there an easy way to replace these letters with their normal counterparts or simply get rid of them (preferably recursively)?

Thanks,
Lucas

PS. There are so many odd characters that simply using some regex isn't an option.

A simple shell script, using the "tr" command to translate the characters, should do the trick.  Here's a rough version of such, which translates lowercase letters "abcdef" to their uppercase counterparts ("ABCDEF"):
```
#!/bin/bash

IFS="|"

LIST=`find . -name "*.mp3" -printf "%p|"`

for FILENAME in $LIST; do
        NEWNAME=`echo "$FILENAME" | tr "abcdef" "ABCDEF"`
        if [ "$FILENAME" != "$NEWNAME" ]; then
                mv -i "$FILENAME" "$NEWNAME"
        fi
done
```

Notes:

1.  The "IFS=..." and the "-printf.." are to correctly handle filenames with spaces in them.
2.  You'll need to replace the two sets for the "tr" command with the correct values for your situation.
3.  I've specified a "mv -i" so that you'll get a prompt if you attempt to overwrite an existing file.
4.  If you have some of those weird characters in the *directory* names, then the script will behave weirdly.  If so, use the "basename" and "dirname" commands to separate the file name into its components, apply the "tr" to the basename, and then put them back together.
5.  This is a quick-and-dirty script.  It has *not* been heavily tested.  Use at your own risk (I recommend having backups of the files..)

Lloyd B.

---

