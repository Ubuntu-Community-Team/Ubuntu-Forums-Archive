---
title: "Running programs with the command line"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by 56seeker on 2007-05-17
I'm trying to "get better at Linux"; and do more stuff from the command line. However, one of the problems I'm facing is how to start programs from the command line, and even more how to identify the program I need.

For instance, to navigate to my home folder, create a subfolder and move a pdf into the subfolder; all this I can find man or info pages for and I can accomplish (though can any one tell me how to deal with spaces in file and folder names elegantly?).

However, how do I open the pdf?

In a Windows command line I'd just type the file name to open the file in the registered program. However in Ubuntu that gives command not found. 
This puzzles me; as gnome seems to have "document viewer" as the registered program to open pdf files if I inspect the file properties with Nautilus.

I imagine the trick is probably to issue the program name first and then the file name?

This brings me to the second problem. In XP I could find the program name by right clicking on the program's short cut and inspecting it's properties; but  Gnome doesn't show properties on start menu short cuts and I can't see one for "document viewer" anyway.

How would I find the appropriate command name to open a pdf?

Thanks :)

---

### Post by lazyart on 2007-05-17
It's called evince.

---

### Post by earobinson on 2007-05-17
> **56seeker said:**
> (though can any one tell me how to deal with spaces in file and folder names elegantly?)
```
cat "name with spaces.txt"
``` you can replace cat with any command

> **56seeker said:**
> However, how do I open the pdf?
```
gnome-open <filename>
``` will open any file with the gnome default


> **56seeker said:**
> I imagine the trick is probably to issue the program name first and then the file name? yup you could also do this when I opened a pdf in gnome I went to help about and saw that the program name was evince so in the terminal I tried ```
evince <pdf name>
``` and it works



> **56seeker said:**
> This brings me to the second problem. In XP I could find the program name by right clicking on the program's short cut and inspecting it's properties; but  Gnome doesn't show properties on start menu short cuts and I can't see one for "document viewer" anyway.

How would I find the appropriate command name to open a pdf? This is annoying I tend to right click on the program in the start bar I want to know the command for then add it to the panal then from there you can right click it to get the command used to run it.

One of the best commands I find in the terminal is apropos this lets you search all the man pages for something eg ```
apropos pdf
``` finds all the man pages that mention pdf

Hope this helps.

---

### Post by lazyart on 2007-05-17
Wow, that was a great answer.

/me takes notes.

---

### Post by aktiwers on 2007-05-17
Just type the name of your pdf viewer and then the pdf file.. like this:
```
epdfview /your/path/tothe/pdffile.pdf
```

In my case my pdfviewer program is called ePDFview.

---

### Post by heimo on 2007-05-17
> **lazyart said:**
> Wow, that was a great answer.

/me takes notes.

I must agree. earobinson, your answer is excellent and I learned new things. :KS

---

### Post by earobinson on 2007-05-17
> **heimo said:**
> I must agree. earobinson, your answer is excellent and I learned new things. :KS
ya I some times go a bit over kill, Thanks.

---

### Post by 56seeker on 2007-05-20
Thank you very much!

---

### Post by earobinson on 2007-05-20
np

---

