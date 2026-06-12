---
title: "gui batch rename"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by andre2p on 2007-01-27
Hello:

I am relatively new to Ubuntu,  but I already dumped M$ and I am enjoying this great OS.

Question:  I need to rename many JPG photos and I want to auto number them.  I tried KRename but what I need is to create that number order based on sorting them by file date.  KRename will number them based on sorting by file name (A-Z or Z-A).

Hope I explained my problem. Thanks in advance,
Andrew

---

### Post by phossal on 2007-01-27
By file date? Huh? Post a couple of names, and give an example.

---

### Post by IYY on 2007-01-27
Sorry, but I don't use the GUI for these types of things. Here is a script that will do it:

```

cd /path/to/directory/where/your/pictures/are/stored/
for x in `ls -c`
do
   i=`expr $i + 1`
   mv $x $i-$x
done

```

I'd suggest that before you run the script, you run the following test script that will do the same thing, except that it won't actually rename anything but just print out the new names, to see if it's what you want:

```

cd /path/to/directory/where/your/pictures/are/stored/
for x in `ls -c`
do
   i=`expr $i + 1`
   echo the file $x will now be called $i-$x
done

```

---

### Post by ComplexNumber on 2007-01-27
try f-spot

---

### Post by andre2p on 2007-01-27
Wow that is almost what I need,  but the sort needs to be by file created date and not last modified.  Thanks for all the quick replies.

Andrew



[QUOTE=IYY;2071583]Sorry, but I don't use the GUI for these types of things. Here is a script that will do it:

```

cd /path/to/directory/where/your/pictures/are/stored/
for x in `ls -c`
do
   i=`expr $i + 1`
   mv $x $i-$x
done

```

---

### Post by phossal on 2007-01-27
> **andre2p said:**
> Wow that is almost what I need,  but **the sort needs to be by file created date** and not last modified.

That's what I wondered. Where would it *get* that info? Are your pictures named by date (by the camera), or do you want to use a system date?

---

### Post by IYY on 2007-01-27
What you are asking may not be possible. As far as I know, the creation date is not actually stored anywhere.

---

### Post by Buck2348 on 2007-01-27
I've wondered about this since I switched to Ubuntu in November.  There is no "date created" in the Properties info about a file/folder.  Anybody know why not?  And whether that info is in each file somewhere and can be extracted?

Buck

---

### Post by phossal on 2007-01-27
One way is to use a perl script to read the inode of the file, but I'm not sure that's what he's trying to do. A lot of cameras name the photos with a date, so I can't tell if his problem is much easier or not.

---

### Post by andre2p on 2007-01-27
Most of what I do is work with photos.  I switched form the Windows program IMatch to Digikam.  I am not sure what date Digikam displays but it does display it right.  It shows a date created and a modified date. In Windows both dates are available when you select properties.  I thought the same was available for a file within Ubuntu.  Thanks again.  Andrew.

---

### Post by andre2p on 2007-01-27
I just found that when i right click on one of my modified photos,  the following is displayed under the properties|Image Tab:

Image Type: jpeg (The JPEG image format)
Width: 2212 pixels
Height: 2952 pixels
Camera Brand: Canon
Camera Model: Canon PowerShot SD800 IS
Date Taken: 2006:12:09 21:37:38
Exposure Time: 1/60 sec.
Aperture Value: f/2.8
Metering Mode: Pattern
Flash Fired: Flash fired, auto mode, red-eye reduction mode
Focal Length: 4.6 mm
Shutter Speed: 189/32 sec. (APEX: 7)
Software: digiKam-0.9.0

That created date is the one I am interested in.

Andrew

---

### Post by phossal on 2007-01-27
So, you want the date taken time?

---

### Post by Buck2348 on 2007-01-27
Duh . . .  I should have remembered that the exif information on a digital photo includes the date taken.  Just browsing through a few recent pictures in my files, I find that the properties dialog more often than not fails to display that info--says "Failed to load image information."  Bummer.  However, in another folder it seems to display for all the files.   Also, I noticed that root owns the photo files--these files were there before I installed Ubuntu.  Group does have read/write permissions so I guess that's ok.  I guess root owns everything in the system except $HOME.

Buck

---

### Post by andre2p on 2007-01-27
Yes.  Date taken.

I noticed the properties|Image tab fails to display information for some photos,  but Digikam does display it correctly all the time. 

I am new to Ubuntu,  but I am already amazed (in a good way) about the community support.  

Andrew


> **phossal said:**
> So, you want the date taken time?

---

### Post by phossal on 2007-01-27
The truth is that I don't know how to do it. I know there are some custom libraries out for Perl, among other languages, but EXIF data isn't universal. How many photos are you dealing with? It seems like that would be best done via a photo management program. I don't know any though. That's way outside my realm of experience.

---

### Post by IYY on 2007-01-27
Could you please send one of your photos to ilya.yakubovich at gmail.com? I don't have any photos of this sort on my machine, so I can't find a command to extract the date. I suspect 'identify' could do it.

---

### Post by parallax68 on 2007-02-02
This one works fine with little update and use the exif data so even you altered the created date it will find it unless you do not have exif info in your pics:
taken from
[http://gentoo-wiki.com/TIP_Organizing_digital_photos](http://gentoo-wiki.com/TIP_Organizing_digital_photos)
updated to suit my needs

```


#!/bin/bash

# Picdir v0.9 rc1

# Copyleft 2005 Gentoo-Wiki.com - This software is OpenSource
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

# Guaranteed to be my personal best!
# ...not guaranteed to work...


# What will this do?
# Search for all JPEG type files within a directory containing EXIF data
# Use the timestamp in the EXIF data to relocate and rename the file
# Using checksums, determine and remove duplicate files
# Uniquely name files which have the same timestamp but different data

# needs BASH FIND GREP CUT FILE JHEAD MD5SUM MV

# 21.11.2006 updated by smarty
# added FILENOEXT variable, file without extension variable
# new files will be as following pattern:
# {YEAR}{MONTH}{DAY}_{HOUR}{MINUTE}{SECOND}_{FILENOEXT}.jpg
# changed mv to cp
# usage
# smarty@xps:~/picdir$ ./cpimg.sh /home/smarty/picdir/in/ /home/smarty/picdir/out/


if [ ! -n "${1}" ]; then
        echo "USAGE: ${0} /my/pictures/unsorted/ [/my/pictures/sorted/]"
        echo "The trailing '/' is kinda important... btw..."
        exit
fi
if [ ! -n "${2}" ]; then
        mkdir -p "${HOME}/picdir/out/" 
        MOVETO="${HOME}/picdir/out/"
else
        MOVETO=${2}
fi

# Call self recursively
if [ ! "${3}" = "RECUR" ]; then
        echo "Finding and organizing all pictures with EXIF timestamps..."
        find "${1}" -type f -exec "${0}" {} "${2}" "RECUR" \;
        echo "Finished."
else
        FILE="${1}"
        HAS_EXIF=$(file "${FILE}" | grep 'JPEG' | grep 'EXIF') # Is it better this way?
        if [ -n "${HAS_EXIF}" ]; then
                TIMESTAMP=`jhead "${FILE}" 2>/dev/null | grep 'Date/Time' | cut -d':' -f2-6` # Or this way?
                if [ ! -n "${TIMESTAMP}" ]; then
                        echo "WARNING: File Not copied, EXIF ok but no timestamp for ${FILE}"
                        exit
                fi
                # Keep original filename wihtout extension
                FILENOEXT=`basename $FILE`
                FILENOEXT=`echo ${FILENOEXT} | cut -d'.' -f1`
                # Deciding path
                DATE=`echo ${TIMESTAMP} | cut -d' ' -f1`
                YEAR=`echo ${DATE} | cut -d':' -f1`
                MONTH=`echo ${DATE} | cut -d':' -f2`
                DAY=`echo ${DATE} | cut -d':' -f3`
                MOVETO="${MOVETO}${YEAR}${MONTH}/" #Directory Structure
                mkdir -p ${MOVETO}
                # Deciding filename
                TIME=`echo ${TIMESTAMP} | cut -d' ' -f2`
                HOUR=`echo ${TIME} | cut -d':' -f1`
                MINUTE=`echo ${TIME} | cut -d':' -f2`
                SECOND=`echo ${TIME} | cut -d':' -f3`
                NEWFILE="${YEAR}${MONTH}${DAY}_${HOUR}${MINUTE}${SECOND}_${FILENOEXT}.jpg"
                # Complete path
                ABSPATH="${MOVETO}${NEWFILE}"
                # Complete path

                if [ -f "${ABSPATH}" ]; then
                # 1) File exists with that name"

                        if [ ! "${ABSPATH}" = "${FILE}" ]; then
                        # 2) The file isn't itself ... yeah ... that makes sense"

                                SUM0=`/usr/bin/md5sum "${FILE}" | cut -d' ' -f1`
                                SUM1=`/usr/bin/md5sum "${ABSPATH}" | cut -d' ' -f1`
                                if [ ! "${SUM0}" = "${SUM1}" ]; then
                                # 3) It isn't a duplicate of the same picture"

                                        i=0
                                        ABSPATH_1="d${i}-${ABSPATH}"
                                        ABSPATH_1="${MOVETO}d${i}-${YEAR}${MONTH}${DAY}${HOUR}${MINUTE}${SECOND}.jpg"
                                        until [ ! -f ${ABSPATH_1} ]; do
                                                (( i++ ))
                                                ABSPATH_1="${MOVETO}d${i}-${YEAR}${MONTH}${DAY}${HOUR}${MINUTE}${SECOND}.jpg"
                                        done

                                        # Giving it a unique name 'd#-FILE'"

                                        echo "Appending 'd${i}-' to ${ABSPATH}: file exists."
                                        ABSPATH="${ABSPATH_1}"

                                # 3) non-duplicate of same name was renamed"
                                else
                                        echo "Checksum match: Duplicate file overwritten"
                                fi

                        fi
                        # 2) if the file is itself, pass-along, mv will handle it"

                fi
                # 1) All that settled, should be safe to move the file
                if [ ! "${FILE}" = "${ABSPATH}" ]; then
                        echo -n "."
                        cp "${FILE}" ${ABSPATH}
                fi
        else
          echo "."
          echo "WARNING: File Not copied, No Exif Data for ${FILE}"
        fi
        #  0) If that even was a picture, it certainly didn't have EXIF data."
fi
# I tested this baby on my precious photos and it worked for me.
# Sorted about 700 photos from about 34,500 files total in a few minutes. :-D


```


hope it helps...

---

