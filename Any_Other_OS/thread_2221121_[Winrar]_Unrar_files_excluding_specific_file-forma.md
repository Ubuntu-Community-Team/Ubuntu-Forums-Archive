---
title: "[Winrar] Unrar files excluding specific file-formats"
date: 2014-04-30
forum: Any Other OS
---

### Post by daga2 on 2014-04-30
Hello Everybody, 

i am still pretty new to Ubuntu and i have got a question about unraring some archives using Winrar (or "RAR archiver" / Standard installed unrar software on Linux Mint Cinnamon).

My Archive "Archive1" has a path like this:

A (#containing .jpg, .txt)
B (#containing .jpg, .txt)
C (#containing .jpg, .txt)

Now i want to extract the files in the same directory with the same path A,B,C but without all the .jpg's.

**man unrar **

shows me the following commands:
[http://pastebin.com/KAK6ifKL](http://pastebin.com/KAK6ifKL)

I already tried some combinations of synthax, but none of it worked for me.

The things i tried are the following:

[LIST=1]
[*]cd /filepath
[/LIST]

Then i think i need some of the following synthax:

       -x<file>
              Exclude specified file.

       -x@<list>
              Exclude files in specified list file.

       -x@    Read file names to exclude from stdin.

But how do i write the correct synthax to exclude all .jpgs while unraring the archives?

unrar x -x<.jpg> 

does not work. How do i need to write it correctly?


Info: I am using Linux Mint Cinnamon

---

### Post by oldos2er on 2014-04-30
Moved to Other OS/Distro Support.

---

### Post by steeldriver on 2014-04-30
If it's the same unrar as in the standard Ubuntu repository, then it appears to accept a * wildcard i.e.

```
unrar x *archive.rar* **-x'*.jpg'**
```

It doesn't seem to work if there is any space between the -x and the '*.jpg' (in fact it appears to treat *that* as a list of files to *include* in the extraction).

For example, if
```

$ unrar t archive.rar 

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal


Testing archive archive.rar

Testing     mydir/fileB.mp4                                           OK 
Testing     mydir/file3.jpg                                           OK 
Testing     mydir/file1.txt                                           OK 
Testing     mydir/fileA.mp4                                           OK 
Testing     mydir/file2.jpg                                           OK 
Testing     mydir/file2.txt                                           OK 
Testing     mydir/fileC.mp4                                           OK 
Testing     mydir/file3.txt                                           OK 
Testing     mydir/file1.jpg                                           OK 
All OK

```
then
```

$ unrar x archive.rar -x'*.jpg'

UNRAR 4.00 beta 3 freeware      Copyright (c) 1993-2010 Alexander Roshal


Extracting from archive.rar

Creating    mydir                                                     OK
Extracting  mydir/fileB.mp4                                           OK 
Extracting  mydir/file1.txt                                           OK 
Extracting  mydir/fileA.mp4                                           OK 
Extracting  mydir/file2.txt                                           OK 
Extracting  mydir/fileC.mp4                                           OK 
Extracting  mydir/file3.txt                                           OK 
All OK

```

---

### Post by daga2 on 2014-05-01
@Steeldriver:

Thank you very very much, it works perfectly =)

But what if there are .jpg's and .png's that i want to exclude at the same time?

Or can i simply write a command that unrars the archive with the same path/directory contruction while only keeping some specific kind of file format like .mp3, .txt etc.?

Thank you in advance =)

**Edit:** I found out how to type the syntax to exclude .jpg and .png at the same time:

unrar x archive.rar -x'*.jpg' -x'*.png'

Now theres only the question how to write a command to extract only a specific file format. When i type unrar l archive.rar then i get a list that is too long to chose the files that i want to keep. It would be much more easier just to tell the program to unrar a specific filetype.
Excluding files with -x'*.jpg' -x'*.png' does the trick. But sometimes i have some formats i have never heard about. So i simply want to extract only one file format.

**Edit2: **

Now ive tried many other syntax and one of it worked for me =)

unrar x archive.rar '*.mp3'

made the job

But still thank you for helping me =)
Sometimes Linux gets a little bit tricky but i still love it more than Win****

The Thread can be marked as **solved **

---

### Post by steeldriver on 2014-05-01
Glad you figured it out - for the record, if you want to extract multiple types the following should also work

```
unrar x archive.rar '*.mp3' '*.txt'
```

and so on.

You can mark the thread as [SOLVED] yourself using the 'Thread Tools' drop down menu at the top of the thread.

---

