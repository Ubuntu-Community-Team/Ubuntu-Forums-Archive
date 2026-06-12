---
title: "finding/setting environment variable"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by gatoruss on 2007-03-31
Hi.  I installed xboard to play chess.  I have been reading thru the sparse documentation, and have a few questions I am hoping someone can help with.

Q1 -

The documentation says that game and position files are stored as followed:

>  Game and position files are found in a directory named by the ‘CHESSDIR’ environment variable. If this variable is
       not  set,  the current working directory is used. If ‘CHESSDIR’ is set, XBoard actually changes its working direc&#8208;
       tory to ‘$CHESSDIR’, so any files written by the chess engine will be placed there too.

How do I set the *'CHESSDIR' environment variable*?

Q2 - 

There are various optiuons that you can set.  The documentation says:

> Each  option  corresponds  to an X resource with the same name, so if you like, you can set options in your ‘.Xde&#8208;
       faults’ file or in a file named ‘XBoard’ in your home directory.  For options that have two names, the longer  one
       is the name of the corresponding X resource; the short name is not recognized.  To turn a boolean option on or off
       as an X resource, give its long name followed by the value true or false (‘XBoard*longOptionName: true’).

How do I edit '.Xdefaults' so that I can set some of these options.  Alternatively, how can I make a file named "XBoard" in my home directory.  I assume that I use the text editor to enter the various options, what type of file do I save it as?

Thanks for any help.

---

### Post by dstew on 2007-03-31
Hi gatoruss. To set an environmental variable, just enter the variable name, an equals sign, and the value you want it to have. First, make the directory. If you are in your home directory, and that is where you want to put your chess directory, type the following on the terminal command line:

mkdir chessgames

Then, set the environmental variable to this directory:

CHESSDIR=/home/gatoruss/chessgames

I am assuming your user name is gatoruss, but use whatever your real user name is for your home directory. If you want other users to have access to this environmental variable, use the export command:

export CHESSDIR=/home/gatoruss/chessgames

To check the value of an environmental variable, use:

echo $CHESSDIR

I am not sure about the file .xdefaults, I could not find it on my system. To create a text file named Xboard in your home directory, make sure you are in it first of all:

pwd

This tells you what your current directory is. If it is not your home directory, use cd to get to it. After you are there, open a text-editing program and create the file. Xubuntu uses mousepad, and Ubuntu uses gedit. Just save it, and it should be in your home directory.

I hope you enjoy Xboard. I use it to play chess on the Internet Chess Club.

---

### Post by gatoruss on 2007-03-31
Thank you dstew.  I must be misunderstanding how xboard works.  Maybe you don't mind some more questions?

I did what you said to do, and the echo command confirmed that the CHESSDIR was the directory I set it to (chessgames), but when I saved a game per the xboard manual (language in the first quote in my post above), the game was not saved in the designated CHESSDIR (chessgames); rather it was saved in my home directory - as was the case before I set the CHESSDIR to chessgames?

Also, I wanted to customize some stuff (like color of squares, etc.).  I interpreted the xboard manual (including the language in the second quote in post above) as indicating that if I created a file in my home directory named "XBoard" I could set some options in that file that xboard would invoke the options when xboard was run.  But when I set up the file and added options for square colors (using the option from the xboard manual) it did not change the default settings?

Do you know of any links that explain how all of this works for xboard?

Thanks, again.

---

### Post by dstew on 2007-04-01
Is seems that the CHESSDIR variable becomes the working directory of XBoard if it is defined when XBoard is started. So, you would have to set the variable first, then start XBoard. If you want to make CHESSDIR variable a permanent part of your system, create the variable, then issue the command export CHESSDIR. Thats about as much as I can figure out at present. If you do not export the variable, it disappears when you shut down.
 
You can create the .Xdefaults file in your home directory with a text editor. The dot in the file name just hides it during a normal directory list. You should be able to create the XBoard file in the same way. Be sure to use both the capital X and B in XBoard, since file names are case sensitive.

I think the lines in the .Xdefaults file to change options are supposed to look like this (the example is to make white squares white):

XBoard*lightSquareColor: #FFFFFF

I haven't tried these yet, but that is what it seems to want.
EDIT: I just tried it using an XBoard file in my home directory, and it worked perfect. I can change the color of the white squares by changing the color in the above line in the XBoard file.

---

### Post by gatoruss on 2007-04-01
> **dstew said:**
> 

I think the lines in the .Xdefaults file to change options are supposed to look like this (the example is to make white squares white):

XBoard*lightSquareColor: #FFFFFF

I haven't tried these yet, but that is what it seems to want.
EDIT: I just tried it using an XBoard file in my home directory, and it worked perfect. I can change the color of the white squares by changing the color in the above line in the XBoard file.

Yes...that's the ticket!

I found a site on the Internet where someone had an example of their "XBoard" file...here it is if you are interested...[http://vico.kleinplanet.de/xboard/xboard.ad.html](http://vico.kleinplanet.de/xboard/xboard.ad.html)

Thanks for your help!

---

### Post by andrew.46 on 2007-07-09
Hi,

 I see most of your questions have been answered. If you wish to see all of your environment variables you can type:

```
printenv
```

 Just a little extra snippet :-)

                 Andrew

---

### Post by rajausman on 2007-07-16
Hi,

Does anyone know how to set an environment variable permanently in Ubuntu feisty (Kubuntu). I can set it temporarily, but next time I log in its gone.

Would some one please indicate in which file it should be set and how ----permanemtly.

Thanks

---

### Post by andrew.46 on 2007-07-16
Hi,

 Read your post:

> **rajausman said:**
> Hi,

Does anyone know how to set an environment variable permanently in Ubuntu feisty (Kubuntu). I can set it temporarily, but next time I log in its gone.

Would some one please indicate in which file it should be set and how ----permanemtly.

Thanks

 The easiest way is to place the variable in your ~/.bashrc file.

                     Andrew

---

