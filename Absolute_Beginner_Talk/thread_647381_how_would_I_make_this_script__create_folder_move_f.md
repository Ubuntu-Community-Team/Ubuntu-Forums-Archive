---
title: "how would I make this script?  create folder move file"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-12-22
I have my movies backed up in one directory.  Some of the movies are in multiple parts, so they're in subdirectories.  Some of them are one part, so they're in the directory.  For example:

/Movies/Two Parter/part1.avi
/Movies/Two Parter/part2.avi
/Movies/One Parter.avi

and so on...

because of the way xbmc sorts files (directories first then files), I want to move all of the .avi files in /Movies into subdirectories named after the file.  So I want a batch that will find

/Movies/One Parter.avi

and move it to

/Movies/One Parter/One Parter.avi

any suggestions?

---

### Post by Biggy on 2007-12-22
read here : [http://ubuntuforums.org/showthread.php?t=647264&page=2]("http://ubuntuforums.org/showthread.php?t=647264&page=2")

---

### Post by randomjohn on 2007-12-22
I did read that before I posted.  I don't see how that guy's question has anything to do with mine.  

I'm looking for a script that will move a bunch of files automatically.  I want to process 200 files in a batch, not learn how to use the "send to" command from xp to move files one at a time.

I would guess I have to do something like take the filename (exclusive of the extension .avi), put that into a variable, create a directory with the variable name, then move variable.avi to variable/variable.avi then lather, rinse, repeat.

---

### Post by vanadium on 2007-12-22
With the basename command, you can strip a filename extension:

basename mymovie.avi .avi

so you can create the directory using

mkdir `basename mymovie.avi .avi`

Then obviously, you move a file to a directory using

mv mymovie.avi mymovie

This can be done for several files using

```

for f in *.avi ; do
  d=`basename "$f" .avi` ;
  mkdir $d ;
  mv "$f" "$d" ;
done

```

and as usual, there possibly are several other (perhaps more efficient) ways.

---

### Post by randomjohn on 2007-12-22
This is definitely a step in the right direction, but I probably should have mentioned that the filenames have spaces in them... it caused a few problems.

I have file names like /Movies/The Big Blockbuster.avi

so it kept trying to make directories for "the"

But it did work perfectly for all the one-word files, so thanks for that!

---

### Post by randomjohn on 2007-12-22
Oh, and I'm going to need to figure out how to stick all the .avi extensions back on the files that didn't move...

---

### Post by randomjohn on 2007-12-22
Well, I went through and stuck all the .avi's at the end of the multi-word filenames.  Anyone know how to make vanadium's script work with filenames that have spaces?

---

### Post by vanadium on 2007-12-23
Well nobody's perfect and i forgot to include the quotes in the mkdir command, which is why it did not work as expected (should have tested with filenames including spaces)

---

### Post by randomjohn on 2007-12-23
This worked perfectly, thank you.  For anyone who wants the script, here it is with the correction

```
for f in *.avi ; do
  d=`basename "$f" .avi` ;
  mkdir "$d" ;
  mv "$f" "$d" ;
done
```then you can either add a shebang at the beginning and make it executable and run it, or just save it as is and sh [filename]

Again, thanks very much.  It actually helped me figure out how to do a bunch of other interesting stuff.

---

