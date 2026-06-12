---
title: "Organize files with a shell script"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Project 318 on 2006-02-16
I don't know where I'd even start
I have a large music collection and navigating it has become a hassle on my mp3 player, and I'd like to organize my music folder alphabetically.  When I say alphabetically, I mean it literally.
For example:

I have ~/Music/Artist/
I'd like to move it to 
~/Music/A/Artist/
So, an artist that starts with A goes into the subdir of my Music folder, ~/Music/A/ 

Folders that start with B go to ~/Music/B/ and so on.

This is where I get stuck.  I have absolutely no clue how to do this with a script.  Doing it manually would be too time consuming.  

What would a good script for what I want to do?
(also, I'm not sure if this would belong in the programming subforum although its a question)

---

### Post by goatflyer on 2006-02-16
Open a terminal window, type:

```

cd ~
nano makeit.sh

```

... and paste the following script into it, but change the directories to whatever you are using.  Note the new dest directory should NOT be in the original music directory or else bad things will happen.
 
```

#!/bin/bash

#specify where alphabet dirs are to be created.
dest=~/music

#specify where original files are found
mydir=/media/hda1/oldmusic

mkdir $dest
#build directories
for d in a b c d e f g h i j k l m n o p q r s t u v w x y z ; do
 mkdir $dest/$d
done

#copy files (keep ownership and permissions)
for f in `ls $mydir` ; do
 if [ -f $mydir/$f ]; then
  d=`echo $f | cut -c1 | tr A-Z a-z`
  cp -p $mydir/$f $dest/$d
 fi
done

```

Then hit ctl-X, Y, and ENTER to save the file and exit.

Make this file executable, and run it with this command:

```

chmod +x makeit.sh
./makeit.sh

```

I'm sure others will point out how I could have done it easier, etc. but hey -- some of us are still learning...

---

### Post by Project 318 on 2006-02-17
I followed you directions and replaced 
```
#specify where original files are found
mydir=/media/hda1/oldmusic
```
with
```
#specify where original files are found
mydir=~/Music
```
Which is where my music resides.

The script gets as far as creating the a-z folders in ~/music, but nothing else happens.
Could it be that some of the artist folders begin with numbers and some begin with capital/not capital?
edit: spaces in the folder names too

---

