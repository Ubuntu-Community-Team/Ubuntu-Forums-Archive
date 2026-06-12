---
title: "Bash script to create folders based on file names"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Big_Rog on 2008-02-27
I'm in the process of organizing a directory of about 2000 images, and want to convert their format (easy) and move them into directories based on the first and second parts of the file name (hard, pain to do by hand).  I'm new to bash and regexp stuff, but i'm poking around the net to see if i can get my head around the concepts.  Here's a quick example of what i mean:

File names:
[INDENT]INV_Misc_Spoon_01.png
INV_Misc_Plate_03.png
INV_Food_Ham_01.png
Spell_Nature_06.png
[/INDENT]

Make a directory based on the first part of the name (the INV part). Make subdirectories based on the second word in the name and drop the converted files into the appropriate directory.

Like i said, i'm new to bash and don't really know where to start coding.  I understand the basic logic flow to the operation:
[LIST]
[*]check the number of files in directory (minus . and ..)
[*]make a FOR loop of that many iterations
[*]grab the next file in the directory
[*]read the first part up to _
[*]read the second word in the filename using a regexp (match INV_ and clip to the next _)
[*]check to see if the directories already exist: if not, create them
[*]convert the .png to .jpg using imagemagick convert command (with destination?)
[*]move the file to the appropriate directory
[*]iterate loop until completed
[/LIST]

I saw a thread about using 'ls -A' to ignore . and .. so i'm anticipating that, but i'm lost on almost everything else...  Your input is greatly appreciated!

---

### Post by .nedberg on 2008-02-27
This would get the parts of the file name. You would have to check if the folder exists and move the files yourself.

```

#!/bin/bash

for f in `ls -1`; do
	p1=$(echo $1 | cut -d _ -f 1)
	p3=$(echo $1 | cut -d _ -f 3)
	#check for folder here
	echo $p1
	echo $p3
done

```

---

### Post by Mr. C. on 2008-02-27
Your filenames have inconsistent numbers of parts (some have two underscores, some have three).  Are you basically trying to convert just the underscores into path separators (/), like:

```
INV_Food_Ham_01.png  => INV/Food/Ham/01.png
Spell_Nature_06.png      => Spell/Nature/06.png
```

Otherwise, what is your rule for splitting these?

Testing for, and creating non-existent directories is easy:

```
[ -d $newdir ] || mkdir -p $newdir
```

and the for loop is more easily accomplished with:

```
for file in *; do
  ...
done
```

MrC

---

### Post by Big_Rog on 2008-02-28
Thanks for the prompt reply!

So to setup the loop, i'd do
```
for file in 'ls -1A'; do
```

With the splitting, there isn't a pre-set number of underscores (usually 2 or 3) and the first part is not a fixed size.  Would it be doable to make a sub-loop that parses one char at a time until it hits an underscore, and concatenates a string with the scanned character? pardon my pseudo code, but i'm trying to illustrate the concept. =)

var int position = 1
var char scanned
var string part1
var string part2
var string filename (read in filename as string)

for(i=0, i<2)
 [INDENT](look at one character at 'position' in 'filename' and call it 'scanned')
 if scanned != '_' && i =0;
  [INDENT]part1 += scanned;[/INDENT]
 else if scanned !='_' && i=1;
  [INDENT]part2 += scanned[/INDENT]
 else if scanned = '_'
  [INDENT]i++[/INDENT]
 end[/INDENT]
end

now we can do the dir check, but i'm not sure about using multiple variables as folder names, e.g.
```
[-d $part1] || mkdir -p $part1
```
and then
```
[-d $part1/$part2] || mkdir -p $part1/$part2
```

am i on the right track?

---

### Post by Mr. C. on 2008-02-28
Splitting is the trivial part; the hard part is for you to specify *where* the splitting should occur.  Hence my question about the converting the underscores to essentially paths.  This can be done with a single line of code, so don't sweat that.

You're falling into a common programmers trap, which is to begin the problem solving process by focusing on *how* to accomplish something, and not correctly on defining the problem well enough (aka: the requirements).  So I ask again, what should happen to each of those underscores, or more properly, what happens to each word before and after an underscore?  Do they all become directories except for the final one ?

MrC

---

### Post by Big_Rog on 2008-02-28
sorry for not being more specific, i was in a rush to get out the door to work.  came home and realized my hasty reply was still in the 'preview' state =P

The idea is that since there are way too many images in the folder to be easily browsed, to break them down using the first and second portions of the name, e.g. 
```
INV_Food_Ham_01.png => /inv/food/inv_food_ham_01.jpg
Spell_Nature_06.png => /spell/nature/spell_nature_06.jpg
```
For now i'd like to keep the whole file name, but knowing how to split it wouldn't hurt.  The images will eventually be added to a web page, so i'd like to convert them to lowercase as well to ease coding down the line.

---

### Post by Mr. C. on 2008-02-28
Here's the one liner I promised.  First the testdata:

```
$ ls -l
total 12K
drwx------ 4 mrc users 4.0K Feb 28 01:07 Destdir/
-rw------- 1 mrc users    0 Feb 28 00:42 INV_Food_Ham_01.png
-rw------- 1 mrc users    0 Feb 28 00:42 Spell_Nature_06.png
drwx------ 3 mrc users 4.0K Feb 28 01:06 inv/
drwx------ 3 mrc users 4.0K Feb 28 01:06 spell/
```

Now the command....
```
$ /bin/ls -1 INV_Food_Ham_01.png Spell_Nature_06.png | tar -cf - --files-from=- --transform 's#^\(\([^_][^_]*\)_\([^_][^_]*\)_.*$\)#\L\2/\L\3/\L\1#'  | (cd Destdir/ ; tar -xf - )
/home/mrc/test/Destdir
```

and the results:
```
$ ls -l -R Destdir/
Destdir/:
total 8.0K
drwx------ 3 mrc users 4.0K Feb 28 01:07 inv/
drwx------ 3 mrc users 4.0K Feb 28 01:07 spell/

Destdir/inv:
total 4.0K
drwx------ 2 mrc users 4.0K Feb 28 01:07 food/

Destdir/inv/food:
total 0
-rw------- 1 mrc users 0 Feb 28 00:42 inv_food_ham_01.png

Destdir/spell:
total 4.0K
drwx------ 2 mrc users 4.0K Feb 28 01:07 nature/

Destdir/spell/nature:
total 0
-rw------- 1 mrc users 0 Feb 28 00:42 spell_nature_06.png
```

The list of files comes from the current directory.  You can change that as you require.

MrC

---

### Post by Big_Rog on 2008-02-28
> $ /bin/ls -1 INV_Food_Ham_01.png Spell_Nature_06.png | tar -cf - --files-from=- --transform 's#^\(\([^_][^_]*\)_\([^_][^_]*\)_.*$\)#\L\2/\L\3/\L\1#'  | (cd Destdir/ ; tar -xf - )
/home/mrc/test/Destdir
hmm, lemmie see if i can wrap my head around what's happening here:

'ls -1' gets the contents of the directory.  i'm not sure why the two files are listed in the command, as putting them in manually seems to defeat the purpose of automating the task.

using 'tar' to make an archive lets you apply a sed transform on the fly, but it looks like there's a stray '-' in between -cf and --files-from.  Is that supposed to be a -T?

i still need to change the file type though, but i'm thinking you'd need to expand into a full script to get that into the mix, yes?

---

### Post by Mr. C. on 2008-02-28
> **Big_Rog said:**
> hmm, lemmie see if i can wrap my head around what's happening here:

'ls -1' gets the contents of the directory.  i'm not sure why the two files are listed in the command, as putting them in manually seems to defeat the purpose of automating the task.

It lists the filenames of the arguments.   It is a placeholder for you to substitute your directory name where your files are located (eg: cd /path/to/your/files ; ls -1  . | .... ).

> **Big_Rog said:**
> 
using 'tar' to make an archive lets you apply a sed transform on the fly, ...
Exactly!  Let tar do the work for you.  It is good at creating directories hierarchies.

> **Big_Rog said:**
> 
...but it looks like there's a stray '-' in between -cf and --files-from.  Is that supposed to be a -T?
No stray.  The - after the -f argument means the archive goes to STDOUT rather than to a file when in create mode (-c) and means to read from STDIN when in extract (-x) or table-of-contents (-t) modes.  We want the archive to be sent to STDOUT, so that the tar on the other side of the pipeline reads it from STDIN.
> **Big_Rog said:**
> 
i still need to change the file type though, but i'm thinking you'd need to expand into a full script to get that into the mix, yes?
But after you have the archive, that's trivial.  Just use **find** to send the list of files to **convert**, performing the conversion for each jpg.  Something like:

```
find . -type f -name "*.jpg" | xargs convert *ConvertArgsHere*
```

MrC

---

### Post by justleen on 2008-02-28
Guys, guys! keep in mind, this is the "Absolute beginners" ;)


Thats very nifty Mr C, cheers for that one! I'd never even began thinking about using tar that way..

---

### Post by Big_Rog on 2008-03-13
Ok, been sidetracked by a hardware upgrade, but now i'm back on this project.  I tried the script (replacing the two file names with '.') and left off the -xf part.  Totally corrupted the terminal.  doh!

Tried again, with just ls -a1 | ... and realized that it was grabbing all the files in the directory, not just the ones i wanted.  So I ran it again with ls -a1 *.png | ...  and it completed within a second or so.  I thought there must have been an error, since there were no messages or anything, but looking into the folder showed everything as being exactly where it belongs!  Thanks so much for your help.

---

