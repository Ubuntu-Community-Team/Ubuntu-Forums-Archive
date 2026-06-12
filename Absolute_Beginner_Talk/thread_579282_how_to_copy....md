---
title: "how to copy..."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-10-18
i have a file in the computer called fzb.rar and his size is 250mb but he is incomplete because he should be 700 mb
and i have cd that this file in there and he is 700mb
now when i try to copy the file from the cd to the same file on the computer i have 2 options , replace and skip
but i need an option that will continue copying that file because in the computer he is incomplete
is there a program that gives such option for copying files?
it is simillar to the option of pause and resume in firefox that you can resume files that are incomplete(in pause mode)

---

### Post by kazamx on 2007-10-18
Is there a reason you can not just replace the current version?

In your situation I would just replace the incomplete file currently on your disk with the new one from the CD. The end result should be a full replica of the CD file on your computer. getting rid of the file currently on your computer wouldn't be a problem if you have a full copy on the CD. Am I missing something important?

---

### Post by Cannaregio on 2007-10-18
Use console
[COLOR="#0000ff"]accessories -- > terminal[/COLOR]
now navigate to your cd (somewhere in [COLOR="Blue"]/media[/COLOR]) 

copy your targetfile to your home directory, assuming it is "snake", copy from your cd folder:
```
sudo cp fzb.rar /home/snake
```

change back to your home directory
```
cd
```
list files there, size matters in your case
```
ls -larS
```
check if it is there in all its integrity and dimension.

---

### Post by snake444 on 2007-10-18
it didnt helped what you said.. i just need to continue the copy process of file that has been stopeed
and not with replace but with resuming... so is there any solution?

---

### Post by Lord_Dicranius on 2007-10-18
I'm with kazamx on this one.  Why can't you just overwrite the incomplete file with the complete file?  How would the outcome differ from "unpausing" it?

---

### Post by snake444 on 2007-10-18
because in the cd the first part of the file  is corrupt but the second part that i need and i dont have on the computer is ok and i need only that part
so is there a way?

---

### Post by Cannaregio on 2007-10-20
Let's "replace and resume" your own words, coz you'r far from being clear.

You [presume? know from certain?]  you have a corrupt file on a CD.
You think you know this file is divisible in two "parts", and you think you know which one is the first corrupt part, and where it ends, and which one is the second NOT corrupt part, and where it starts (how did you check that?)

You [presume? know from certain?] that the first part of the CD file is corrupt.
You [presume? know from certain?] that the second part of the CD file is NOT corrupt.
You [presume? know from certain?] that the first part of the file you have copied on your disk (how did you copy a corrupt part?) is NOT corrupt on the harddisk.
You now want to copy only the second part of the file on the CD on the hard disk.

The above situation seems to me quite confuse. 
I doubt you really know what you have and you have not.

However, if you really need to copy an exact part of a file, you better get into the nitty-gritty coding approaches: for instance starting from a basic

```
Dim a as string
open "myfile.dat" for binary as #1
open "yourfile.dat" for binary as #2
a=space(512)
Do while Not EOF(1)
       get #1,,a
       put #2,, a
Loop
Close #1
Close #2
```

and/or in python:

```
in_file = open( source, 'rb' )
  out_file = open( dest, 'wb' )
```

and then, of course, adding the necessary code, start and end addresses included, to circumvent your 'corruption'.

Good luck.

---

