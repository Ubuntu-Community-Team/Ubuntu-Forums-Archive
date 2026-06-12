---
title: "How important is NOT having spaces in filenames?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-11
I've finally got a working installation (I hope) of Ubuntu running and I'm about to start moving my backed up files to the system.  However, most of my documents, including programming projects, school work, mp3s, pictures, etc, have spaces in the filename, and I was told that that is a bad idea under a linux environment.  Is it really, and why?  I'm sure there is a script to replace spaces with underscores, or I could write my own in Python, but I am really not a fan of underscores and prefer spaces.  Any help is appreciated, thanks.

---

### Post by PriceChild on 2007-08-11
They'll still work fine really... Most applications should be able to manipulate them normally.

---

### Post by kavon89 on 2007-08-11
It's more of a pain in the butt to have spaces in filenames if you use the terminal a lot. For a regular desktop user, it should be ok. You just have to remember to put quotes around the directory when typing it. Or else it would cut off, like this:

```
cd /home/kavon/Program Files/Teamspeak2 RC 2/
```

The command above to change directory would mess up with something like " /home/kavon/Program  no such file or directory."


The correct way would be:

```
cd "/home/kavon/Program Files/Teamspeak RC 2/"
```

I'm not 100% sure, but to execute a file in the terminal with a space, I think would look like this:

```
."/some script.sh"
```

For servers, capitals and spaces cause problems for automated things. I'm not too sure about why, but that is just what I know.

---

### Post by UltraMathMan on 2007-08-11
Or if you don't want to use quotes, you can take care of spaces when executing terminal commands by preceding the space with a backslash like this ```
cd /home/kavon/Program\ Files/Teamspeak2\ RC\ 2/
```

---

### Post by girishv on 2007-08-12
Using the tab completion should also take care of the spaces (by automatically including \ es)

between, if you want to change the space in a filename to some other (say underscore), you can use simple rename command. It uses the vi(m) command syntax.

rename 's/ /_/g' *.mp3

If you want to convert all the files whose name ends with mp3 recurively, use find command
find . -name "*.mp3" -exec rename 's/ /_/g' {} \;

Dont forget the flower brackets, backslash and semi-colon at the end, for the reason I can not comprehend, they are required :)
A little explanation (if you donot know already)

. in the above command tells which directory to start looking for
-name "*.mp3", tells what to look for 
command following -exec is what to do with the file 
{} - argument (ie., filename) for the command


will replace all the occurances of space in  filenames ending with mp3 in the current directory to underscore

Girish

---

### Post by Old Pink on 2007-08-12
Not at all important, never take it into account, and all my music files, along with many of my other files.

The only time it *could* be a problem is, as mentioned, spaces in terminal. In which case, just write on up to the space, and hit tab for it to fill in for you.

---

