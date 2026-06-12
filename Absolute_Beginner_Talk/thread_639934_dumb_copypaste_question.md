---
title: "dumb copy/paste question"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by missed her show on 2007-12-13
hi

i'm trying to backup the contents of one drive (120gb) to another external drive (New VOlume). 

I'm totally new to linux, have problems with the GUI, and would appreciate any help with the terminal command....thanks!

```
dewey@dewey-desktop:/media/120gb/120gb Audio$ cp -b /Media/New\_Volume
cp: missing destination file operand after `/Media/New_Volume'
Try `cp --help' for more information.
dewey@dewey-desktop:/media/120gb/120gb Audio$ 

```

---

### Post by rodo-&gt;dave on 2007-12-13
hi.

first, try this: -- *Note: the $ denotes your command line prompt*
$ cd "/media/New Volume" 
-->notice I put the path in double quotes "path" -> space separates the command line params

your prompt should look something like:
dewey@dewey-desktop:/media/New Volume:

If you get an error then please post it.. it could be that the name is misspelled.... but assuming that worked...

$ cd -
-->this should take you back to your original directory and your prompt would look like this again:
dewey@dewey-desktop:/media/120gb/120gb Audio$

Next:
you can use the find command and pipe the output through cpio
find: find files
cpio: copy input to output

$ find . | cpio -pmud "/media/New Volume"
--> *Note the use of the double quotes again*
--> this will copy your current directory (ie. dot) (and all sub-directories) to the new "/media/New Volume"

Hope this helps.

---

### Post by jken146 on 2007-12-13
Hi.  In general, if you don't know something about a command, read its man page.  To do this type ```
man <command>
```

In your case with cp, you need to do the following: ```
cp <original file> <new file>
```

I also noticed you used \_ for a space.  You should escape spaces with just a backslash and put the whole path in single quotes, i.e. ```
'/Media/New\ Volume'
```

---

### Post by annda on 2007-12-13
you need to say **what** you want to copy to **where**

so go for something like this:
```

cp /media/120gb/120gb\ Audio /Media/New\_Volume
```

and make sure you use the case sensitive spelling here. i noticed you have /**M**edia....... as destination directory - do you mean /**m**edia or have you created a /**M**edia mount directory?

---

### Post by missed her show on 2007-12-13
thanks for the quick responses.   I'll get back to my linux box and let you know what happens. 

> and make sure you use the case sensitive spelling here. i noticed you have /Media....... as destination directory - do you mean /media or have you created a /Media mount directory?

I *think* the /media was related as a mount directory when i installed ubuntu.

---

### Post by missed her show on 2007-12-13
and another question.....why is my browser crashing/haning when i try to browse the directory (120gb hd) with the GUI interface?

---

### Post by missed her show on 2007-12-13
> **rodo->dave said:**
> 
Next:
you can use the find command and pipe the output through cpio
find: find files
cpio: copy input to output

$ find . | cpio -pmud "/media/New Volume"
--> *Note the use of the double quotes again*
--> this will copy your current directory (ie. dot) (and all sub-directories) to the new "/media/New Volume"

Hope this helps.

seems i'm getting I/O errors.

```
dewey@dewey-desktop:/media/120gb/120gb Audio$ find . | cpio -pmud "/media/New Volume"find: ./various loops and beats: Input/output error
find: ./120gb Music: Input/output error
find: ./DJ stuff/dialolgue voiceovers: Input/output error

```

---

### Post by rodo-&gt;dave on 2007-12-14
ok.
cd to your " /media/120gb/120gb Audio"
type:
$: find . > ~/xx
-- this will find all files in your current directory (120gb Audio) and put the output in the file $HOME/xx

are there any errors displayed?

if not, then you can use cpio using the input file

cd again to "/media/120gb/120gb Audio$"
type:
$: cat ~/xx|cpio -pmud "/media/New Volume"
and see if that works... someone mentioned "man" -> get it -> and use it :)
you can add the 'v' option to cpio for 'verbose' output from cpio... (cpio -pvmud ...).

also, you could "man cp" and try the -R option

don't know about the Gui crash :(
good luck.

---

