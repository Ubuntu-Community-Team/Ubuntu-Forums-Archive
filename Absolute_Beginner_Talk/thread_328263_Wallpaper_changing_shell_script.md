---
title: "Wallpaper changing shell script"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by davidY on 2006-12-30
Hi, I have searched this forums for a way to make wall papers change randomly. Now this is something so simple I was sure I could find an easy program. Unfortunately all the things seem to be pretty buggy or did not run or had problems. Thus, I was forced to learn about shell scripting and then how to use cron (hey, i should learn these things anyway). Anyway, here is code from somewhere that I found:

```
#!/bin/sh
#Go to our pics
cd /media/documents/Desktops
#Get all the picture files names
IMGS=`find . -iname '*.jpg' -o -iname '*.png' -o -iname '*.svg'`
#Find out how many pictures we got
N=`echo $IMGS | wc -w`
#Take a random number between 1 and N
((N=RANDOM%N))

#Cut the file to get the n'th picture
BGNAME=`echo $IMGS | cut -d '/' -f $N | cut -d ' ' -f 1`

#Call upon gconftool to write into the "registry"
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/media/documents/Desktops/$BGNAME"

```

Now this code would work perfectly, except for the fact that the list of names in BGNAME has to be one single word, which makes it unable to handle either directories, or file names with spaces. I don't mind having no directories, but I would prefer to have file names with spaces. Any solutions?

---

### Post by davidY on 2006-12-30
On second thoughts, (although I will not prefer this alternative), is it possible to rename all files with spaces to files with underscores or other characters?

---

### Post by wildkarde on 2006-12-30
you could try this nifty shell script
```
#! /bin/bash
# blank-rename.sh
#
# Substitutes underscores for blanks in all the filenames in a directory.

ONE=1                     # For getting singular/plural right (see below).
number=0                  # Keeps track of how many files actually renamed.
FOUND=0                   # Successful return value.

for filename in *         #Traverse all files in directory.
do
     echo "$filename" | grep -q " "         #  Check whether filename
     if [ $? -eq $FOUND ]                   #+ contains space(s).
     then
       fname=$filename                      # Yes, this filename needs work.
       n=`echo $fname | sed -e "s/ /_/g"`   # Substitute underscore for blank.
       mv "$fname" "$n"                     # Do the actual renaming.
       let "number += 1"
     fi
done   

if [ "$number" -eq "$ONE" ]                 # For correct grammar.
then
 echo "$number file renamed."
else 
 echo "$number files renamed."
fi 

exit 0
```

---

### Post by davidY on 2006-12-30
... the funny thing is that about the same lines of code were used to maintian correct grammar. thanks for that suggestion, but before i go doing some mass 1000+ files file renaming, I would like to find a way to keep the names.
heaps of pictures like these
[IMG]http://i17.tinypic.com/2e19d0y.jpg[/IMG]

---

### Post by davidY on 2007-01-01
This is the final solution. It works for any thing as long as all pictures are in the directory, regardless of name formatting, subdirectories or hard links(not sure about that one though)

```
#!/bin/sh

# Set your folder with the pics
picsfolder="/media/documents/Desktops/"

# Go to your folder with the pics
cd $picsfolder

# Create an array of the files
files=(./*/*.jpg)

# Get the size of the array
N=${#files[@]}

# Select a random number between this range 
((N=RANDOM%N))

# Get the name of this file
randomfile=${files[$N]}

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

---

### Post by Kat of Zion on 2007-01-26
So if I copy this script, what kind of file do I save it as?

> **davidY said:**
> This is the final solution. It works for any thing as long as all pictures are in the directory, regardless of name formatting, subdirectories or hard links(not sure about that one though)

```
#!/bin/sh

# Set your folder with the pics
picsfolder="/media/documents/Desktops/"

# Go to your folder with the pics
cd $picsfolder

# Create an array of the files
files=(./*/*.jpg)

# Get the size of the array
N=${#files[@]}

# Select a random number between this range 
((N=RANDOM%N))

# Get the name of this file
randomfile=${files[$N]}

# start of gconftool command and set the desktop
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picsfolder$randomfile"
```

---

