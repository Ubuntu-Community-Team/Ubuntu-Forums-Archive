---
title: "PDFtk Help"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-05-04
I would LOVE to find a noob-friendly guide to using pdftk. I get the idea. I totally see that i need to be using the terminal to invoke the pdf magic. However, I've tried fifty million (exaggeration, of course) different ways to do it but can't get it to merge two little pdfs in my home folder. i guess i'm directionally challenged in the terminal. 

i went to their website[ http://www.accesspdf.com/article.php/20041129175231241]("http://www.accesspdf.com/article.php/20041129175231241") and I understand the idea, the words that my fingers should type, however, that's a different matter.

Anyone who's used it before willing to give me the primer?

---

### Post by rsambuca on 2007-05-04
If you just want to add two files into one (ie. add the second file to the end of a first file), it is a simple command:

```
pdftk file1.pdf file2.pdf cat output outputfile.pdf
```

You will have to have the entire file directories indicated.  ie. pdftk /home/yourusername/Desktop/file1.pdf, etc.

One of the easiest ways is to move the input files into one directory, then in the terminal, change to that directory and then execute the pdftk command and you can leave out all of the directories.

You can obviously name the outputfile anything you want.

You can type in "man pdftk" in a terminal for more convoluted instructions!

EDIT:  let me know if this works, as it has been a while since I have used it.

Another EDIT:  I just checked and the instructions work.  Let me know if you need further assistance.

---

### Post by noynac on 2007-05-04
You can also use wildcards. Just move all the PDF files that you want to combine into an empty directory (e.g. temp) and issue the following command:

pdftk *.pdf cat output combined.pdf

If you do this a lot, it's best to create a script file. 

There are lots of examples on the author's site, and they are all pretty simple. If you still can't get things to work right, you may want to post what you are typing.

---

### Post by mlhudson on 2007-05-04
so what i guess i've discover is this:

i have no idea how to get around the terminal... i'm a mean cut&paster on these forums, but on my own I flop.

So, how do I "change directories", and can I change directories to the desktop?

stop laughing. thanks.

---

### Post by rsambuca on 2007-05-04
Hey, I definitely am not laughing here.  We have all gone through the same thing as you at one point or another (OK, I did smile, though;) )

First open a terminal:  Applications -> Accessories -> Terminal

You should see the regular prompt:  yourname@yourcomputer:~$

To change directories, use the 'cd' command.  Therefore, to change to the Desktop, enter```
cd /home/yourname/Desktop/
```
You should then see:  yourname@yourcomputer:~/Desktop$

If you are changing to a folder in your own /home directory, you can also just enter:  cd ~/Desktop

Things to keep in mind:  Linux is case sensitive, so Desktop is different from desktop, etc.  That one really caused me all kinds of problems when I started.

Then once you are at your Desktop, you can enter the pdftk command I listed earlier.

---

### Post by mlhudson on 2007-05-04
thank you thank you thank you

that's all it took. i really do appreciate you walking through it slowly. that did the trick for me.
the CAPS thing was an error i was committing, as well, i kept leaving the last / off of the directory name.
but, once i wrote it like you did, i picked up the trail from pdftk, gave the EXACT file names, and PRESTO: MERGED PDF

i love this!

on a side note, i guess i begin to understand why command line can be so appealing (though incredibly intimidating). All we did was type a sentce and the computer opened a program, completed a request and there was narry a CLICK of the mouse. 

Thanks again, you're great to have poking around the noobie forums, don't go anywhere. I'm sure i'll mess up my system sooner or later and i'll want someone with your patience around.

blessings!

---

### Post by rsambuca on 2007-05-04
I must admit, that capital letter thing really screwed me up for a while.  I couldn't for the life of me figure out why things would work when I copy&pasted, but when I typed the commands myself they wouldn't work.

Anyways, always glad to help.  Pass on the knowledge!

---

### Post by lostandcold on 2008-01-18
Good advice I managed to join 7 different pdf files together this way despite being so computer illiterate it took me over a hour to navigate to the appropriate folder.

---

