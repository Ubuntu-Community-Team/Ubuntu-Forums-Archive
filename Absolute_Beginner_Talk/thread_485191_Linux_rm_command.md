---
title: "Linux rm command"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Eric the Grey on 2007-06-26
I've just reloaded my Ubuntu system on a new hard drive, one with a lot more space than the old one (20 gig to 120 gig), and have copied my music folder from my windows installation over to my home folder so I have music to listen to without running the USB drive constantly.

Anyway, I'd like to eliminate all the unnecessary files that are in that directory structure, all of which were created by windows, mainly the album art files.   

I'd like to do this without navigating to each and every directory (there are 170 main directory, plus one more for each album under those).

I thought that doing:

*rm -R *.jpg*

would suffice, but all I get is "*rm: cannot remove `*.jpg': No such file or directory*"

It's not the long file name/windows formatting of the directory names (spaces and all) because some of the folders have only one name (like Aerosmith).  The only things that get deleted are in the directory that I'm currently sitting in.

What am I doing wrong? The search function  turns up nothing at all, unless I enter an exact name match.  It worked fine with the "desktop.ini" files that littered each directory, but doesn't find anything if I use a wildcard (*)

Note:   I do realize the danger of using the rm -R command, and am prepared to recopy if things go wrong.  As long as I'm starting in my /home/john/Music directory, I should be safe. :)


:cool: Eric the Grey

---

### Post by Rocket2DMn on 2007-06-26
rm -R . *.jpg
You gotta start with a directory

---

### Post by Inxsible on 2007-06-26
Alternatively, maybe the extensions are not .jpg and .jpeg instead

---

### Post by Eric the Grey on 2007-06-27
> **Rocket2DMn said:**
> rm -R . *.jpg
You gotta start with a directory

I tried it with and without the space between the first . and the * and neither works:

rm: cannot remove `.*.jpg': No such file or directory

and

rm: cannot remove `.' or `..'
rm: cannot remove `*.jpg': No such file or directory

and all the files in question are .jpg, and not .jpeg.  They were downloaded by WMP, what would you expect (although, I did double check). :p


:cool: Eric the Grey

---

### Post by drwho_cn on 2007-06-27
If you stored all your file under myfolder, you can try

rm -r myfolder

If you are under myfolder, you can try

rm *.jpg

---

### Post by Taliskerd on 2007-06-27
Try this:

**find . -iname *.jpg -ok rm {} ';'**
(locate any file below where I am, remove the files that match -but ask me if it's ok (y/n))

When you're certain this work as intended, change the command to
**find . -iname *.jpg -exec rm {} ';'**
which does the same, but doesn't ask before it removes the file(s)

*Taken more or less as-is from 'UNIX Power Tools', isbn 0-553-35402-7 (Highly recommended!)*

---

### Post by Arndt on 2007-06-27
> **Eric the Grey said:**
> I've just reloaded my Ubuntu system on a new hard drive, one with a lot more space than the old one (20 gig to 120 gig), and have copied my music folder from my windows installation over to my home folder so I have music to listen to without running the USB drive constantly.

Anyway, I'd like to eliminate all the unnecessary files that are in that directory structure, all of which were created by windows, mainly the album art files.   

I'd like to do this without navigating to each and every directory (there are 170 main directory, plus one more for each album under those).

I thought that doing:

*rm -R *.jpg*

would suffice, but all I get is "*rm: cannot remove `*.jpg': No such file or directory*"

It's not the long file name/windows formatting of the directory names (spaces and all) because some of the folders have only one name (like Aerosmith).  The only things that get deleted are in the directory that I'm currently sitting in.

What am I doing wrong? The search function  turns up nothing at all, unless I enter an exact name match.  It worked fine with the "desktop.ini" files that littered each directory, but doesn't find anything if I use a wildcard (*)

Note:   I do realize the danger of using the rm -R command, and am prepared to recopy if things go wrong.  As long as I'm starting in my /home/john/Music directory, I should be safe. :)


:cool: Eric the Grey

I would do
```
find . -name \*.jpg | xargs rm

```

Look at the man page for 'xargs'.

"rm -R" is for removing directories and their contents, not for navigating a directory tree and removing only some files.

Maybe it helps to look at the execution of "rm -R *.jpg" as consisting of two parts: first the shell expands all wildcards (or complains if there were no matches at all), then the result gets sent to "rm".

Some shells (zsh, I think, for example, but not bash or ksh) have a ** wildcard, which goes down into the directory structure, and then "rm **/*.jpg" might work.

---

### Post by Eric the Grey on 2007-06-27
> **Arndt said:**
> I would do
```
find . -name \*.jpg | xargs rm

```

Look at the man page for 'xargs'.

"rm -R" is for removing directories and their contents, not for navigating a directory tree and removing only some files..

That's good to know.  Your suggestion did not work, as it had trouble with the directory structure and spaces. (I'll have to take care of that, and I know I've seen a file-renamer program around somewhere...

However, Taliskerd's suggestion worked like a charm.

Thanks everybody for the help.  I only managed to shave off about 100 meg, but it is nice to know how to delete the garbage when I need to...


:cool: Eric the Grey

---

