---
title: "Is there a program that will resize a large number of images automatically?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-08-12
I usually take pictures on the highest resolution on my camera, when I don't want to post them to the web at the full size. I'd rather just have a copy of them that's much smaller to put up. I'd like to be able to go through a directory and make a copy that's resized to something managable.

---

### Post by tdrusk on 2007-08-12
when you export from picasa you can choose to resize

---

### Post by asmoore82 on 2007-08-12
the "netpbm" pagkage contains lots of command line image editing tools.

If you are familiar with the command line, there's no faster way to get it done!

---

### Post by dscherry on 2007-08-12
Hi,
Install Imagemagick from the repositories. then this script will do what you're asking.  Change the 256x256 to whatever you think is manageable.  Also, use a higher or lower jpg quality, as you like.
If scripts aren't your thing, then go with the one of the image editors.  Some of them handle batches.
Dan
-----------------------------------

#!/bin/sh
#   reducto *.jpg  (or whatever)

SUBDIR=256x256

if [ ! -d ${SUBDIR} ] ; then
  mkdir ${SUBDIR}
fi

for FILE in "$@"
do
  THFILE=${SUBDIR}/$FILE
  if [ ! -e $THFILE ] || [ -e $THFILE -a $FILE -nt $THFILE ] ; then
    echo "Creating ${THFILE}"
    convert -size 256x256 -quality 75 -resize 256x256 "$FILE" "$THFILE"
    chmod 660 $THFILE
  fi  
done

---

### Post by stani on 2007-09-10
To resize photos and apply effects (shadows, rounded corners, ...), try out Phatch = Photo and Batch! It designed to be very user friendly. For more info and an easy deb installer, look here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

