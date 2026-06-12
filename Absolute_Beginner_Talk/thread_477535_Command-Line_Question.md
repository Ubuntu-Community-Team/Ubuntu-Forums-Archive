---
title: "Command-Line Question"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Jyncus on 2007-06-18
Alright, day #2 using Ubuntu or any other form of *nix.  

I have a very simple question about using the terminal to open a file.  I'm having trouble doing just that - opening a file.  Say I navigated within a terminal to a dir where a *.pdf file was located - and then I wanted to open that PDF file using whatever application is associated with that extention..  Adobe Reader in this case..  Simply typing in the name of the file returns a "command not found".  I googled it and came up with nothing..  =/

Appreciate the help

---

### Post by codypumper on 2007-06-18
To open a file, you have to tell which program to use, for example:
acroread /dir/of/pdf

---

### Post by phr0ze on 2007-06-18
There is probably a way to have linux locate the right program and open the file, but typically you have to specify a program as stated above. For text files use GEdit. PDFs are defined above. 

Even in windows you can't just type the file name. You have to specify some command for it.

---

### Post by kevdog on 2007-06-18
Just to add to the post above you might want to do the following

evince filename.pdf &

Adding the & makes the program run in the background so you can keep using the command prompt if you want.  If you are debugging a program, I would not run the program in the background because the error messages are written to the command screen ... usually however you just want to use the program, so that is why adding the & is a good idea

---

### Post by Jyncus on 2007-06-18
So you would put in the filename of the app. executable first, followed by the path to the file?  Would I need to be in the same dir as "acrobat" or whatever..or can I, like with "firefox" for example, just type in the name of the application?

---

### Post by phr0ze on 2007-06-18
For the app you can just type in the name. For the file, you need to specify the full path if you aren't already in there.

---

### Post by WW on 2007-06-18
People who have been using Linux and the command line for a while usually know which application they want to use. Both **evince** and **acroread** can be used to view a pdf file.  If you want to use evince, you give the command as:
```

$ evince file.pdf &

```
To use acroread instead:
```

$ acroread file.pdf &

```
If you are using Ubuntu (as opposed to Kubuntu or Xubuntu), then you are using Gnome, and you can use the command **gnome-open** to open a file.  It will use the default Gnome application to open the file.  For example,
```

$ gnome-open file.pdf

```
will use evince to open the file.

---

