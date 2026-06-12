---
title: "I'd love to know what this command does ?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-03
Its part of the psychocats instructions on creating a home partittion  

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

Any body like to translate this to english? Just curious

---

### Post by jordanmthomas on 2007-10-03
the first part 
```
find . -depth -print0
```
will find every file in your current directory and print it on the screen.
But, it's piped into the cpio command so you won't see it.
cpio basically copies files.  the --null option tells it that the end of the list of files you're giving it is not finished up with an end-of-line character, but a null character.
the --sparse option has something to do with putting largely empty files into what's called a [sparse]("http://en.wikipedia.org/wiki/Sparse_file") file (not sure I understand it myself, but I believe it has to do with saving space on the disk and keeping files close together  :) ).
-p :  man page says this:   Run in copy-pass mode  (I'm not sure I understand that 100%)
-v :  be verbose, basically just tell you what's going on
-d :  when encountering a directory from the input, create it if necessary in the output.

the /new/ says where you want to copy the input to.

So **basically, this command makes a copy of your current directory to /new/ and tells you each file it is copying**.  You can test it by making a test directory somewhere and cd-ing into it.  Then, populate your test directory with a few files and try this command:
(same thing but no sudo needed and just copies into a different directory)
```
find . -depth -print0 | cpio --null --sparse -pvd ~/THISISACOPY
```
Hopefully that will help you make some sense of it.

In the future, you may find the man command handy so you don't have to wait on an answer:
```
man find
man cpio
```

---

### Post by philinux on 2007-10-03
wow cheers.

How come they dont just use cp -R dir1 dir2

Suppose there is a good reason?

---

### Post by jordanmthomas on 2007-10-03
I'm not sure about that one, but I do know that cpio is more related to tar than cp and it's usually just used for making archives
The -p option makes it copy files though.  I'm not sure what the reason for using cpio over cp is though (it may be something as simple as it ignores errors or something)

Short answer:  I have no idea why you'd use it over cp in this case.
Maybe aysiu will pop his head in or something since I believe he writes the pyschocats stuff

---

### Post by philinux on 2007-10-03
Could be it is a very clever copying system

---

