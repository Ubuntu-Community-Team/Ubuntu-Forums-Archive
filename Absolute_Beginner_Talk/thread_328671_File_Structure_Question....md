---
title: "File Structure Question..."
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by SlimJimSouthpaw on 2006-12-31
I'm sure there is a simple answer to this so here goes...

I am trying to combine some video files via the cat command, however I simply want to cd to the location of the files before I do so.

Here is the problem...  I have a second physical HD that I keep all of my media files on, this HD is named B1 Home, I have a shortcut on my desktop to it and it also resides at /storage/B1 Home under my file system.

Here is the command I'm using and the output of said command...

/storage/B1 _Home/Videos

bash: cd: /storage/B1: No such file or directory

I've tried several different commands to navigate to the directory, but all of them return the same message.

What am I missing?

Thanks in advance,

J

---

### Post by psycho78 on 2006-12-31
> my desktop to it and it also resides at /storage/B1 Home under my file system

You have a blank in your Name "B1 Home", so have you tried to:

cd "/storage/B1 Home"    ??? Use  "" when there are Blanks in your path...

I hope this helps :)

---

### Post by SlimJimSouthpaw on 2006-12-31
I'll give it a shot, for what it's worth, I also tried renaming the path to B1_Home and that didn't work either, brb to try the " trick.

Thanks.

J

---

### Post by SlimJimSouthpaw on 2006-12-31
Psycho,

Thanks buddy, the " placeholder for a space worked.  I assume that the _ is also considered a blank space as well, which is why it didn't work either way I tried it.

J

---

### Post by psycho78 on 2006-12-31
>  assume that the _ is also considered a blank space as well, which is why it didn't work either way I tried it.


Never heared about _ as a placeholder for blanks..., you could also use these:
' '

Nice that it works now! :D

---

