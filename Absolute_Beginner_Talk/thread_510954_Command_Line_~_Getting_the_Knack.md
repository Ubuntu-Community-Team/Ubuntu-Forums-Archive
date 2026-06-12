---
title: "Command Line ~ Getting the Knack"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-27
Greetings
I come to Ubuntu more in the Autumn than than in The Spring of my life.
It's all very interesting --however it does take a bit of time to learn.
Now I am coming to the "Command Line" and would like to learn and get to know this properly, so I am asking if there any simple guided exercises one can follow, steps to take which train one in getting used to it.
If there was a little hand book of essential commands I could buy, this would be great, as I find I learn much better from having a book in hand than from constantly viewing a screen.

I am currently studying about the "Command Line" on:

[http://www.prism.gatech.edu/~mflaschen3/UbuntuBook/AppA_Ubuntu_Book.html]("http://www.prism.gatech.edu/~mflaschen3/UbuntuBook/AppA_Ubuntu_Book.html")

Regards

John

---

### Post by Mornedhel on 2007-07-27
The link you gave looks like it has everything you need to learn all about the command line, particularly the man pages part. I don't know about a handbook of commands, but I think there should be at least one for the GNU core tools.

As for simple guided exercises, most of the time the larger books on bash provide an incremental approach so you begin with simple stuff (redirections, etc.) and move on to more complex ones (scripts, etc.). I remember the O'Reilly bash book being an excellent one, but I only read an old version (maybe 10 years old) which is probably still up to date as far as the basic mechanics are concerned.

---

### Post by Bachstelze on 2007-07-27
[http://linuxcommand.org/](http://linuxcommand.org/)

Has pretty much everything you'll need, and a lot more. Happy reading ;)

---

### Post by rich.bradshaw on 2007-07-27
The main thing to realise is that you don't need to know every command, you need to generally understand the concepts behind it all, then you can just string things together when you need something.

The main thing to me is the pipe, or | . This lets you put the results of one command through another. Most of my scripting uses this to get complex results from simple things. 

For instance:

ls | grep cheese

will find any files in the folder with cheese in the name, this works by putting the results of ls through grep which finds things.

Useful building blocks are

Command : Description

ls : list a directory
cat : read a file out to screen
sort : sort whatever comes in
grep : finds things
awk : seperates data and many other things
sed : text replacement

etc.

Other useful things are 

> 

which writes the command to a file, e.g.

ls > filelist.txt

if you now

cat filelist.txt

you can read it out.

rm filelist.txt

to delete it.

You can string all these together like so

cat romeoandjuliet.txt | grep -c juliet

to find the amount of juliets in the script of romeoandjuliet, grep -c counts the occurances.

That's basically all there is to it.

Think of somehting you would like to do, then try and build up to it is my advice!

---

### Post by yorkie on 2007-07-27
two pcket sized books
1,O`Reily   Linux pocket guide by Daniel J Barrett
2, Linux Phrasebook by Scott Granneman
both are good books if I had to pick one it would be number 2
best place to buy Amazon

---

### Post by Andavane on 2007-07-28
thank you for the succinct summary, rich.bradshaw,
and thanks for the book suggestion, yorkie.
I see that I already have the "Linux Pocket Guide";
I guess because I saw the stripe across it saying:
"Covers Fedora Linux", I thought it might not cover Ubuntu,
so I take it it is OK. I trust the "Fedora" thing will not confuse.
It says it based on "Fedora Core 1"... that's why I avoided it.
Regarding the "Linux Phrasebook", I see from Amazon that it is 400 pages,
so that is a big pocket to have!
Regards
John

---

### Post by ReaderRat on 2007-07-28
[**[color=red]Linux In A Nutshell[/color]**](http://www.linuxdevcenter.com/linux/cmd/)

---

### Post by MQMike on 2007-07-28
Tuxfiles:   [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

You'll like this one  :)

---

### Post by Andavane on 2007-07-29
> **ReaderRat said:**
> [**[color=red]Linux In A Nutshell[/color]**](http://www.linuxdevcenter.com/linux/cmd/)

Well yes... errr. but I seem to remember that "In a nutshell" means essential knowledge crammed into the tiniest of spaces... an acorn or something... At over 900 pages, this book seems to be a coconut !  :-k

>> Tuxfiles: [http://www.tuxfiles.org/](http://www.tuxfiles.org/)

You'll like this one 
...Thank you

kind regards

John

---

### Post by xavier_r on 2007-08-01
Hey besides knowing commands, you might also wanna try out various applications that are available from command line...
I made this software for UBUNTU users to do the same...

You might wanna give it a try
[http://screenface.66ghz.com](http://screenface.66ghz.com)

---

### Post by Andavane on 2007-08-02
> **xavier_r said:**
> Hey besides knowing commands, you might also wanna try out various applications that are available from command line...
I made this software for UBUNTU users to do the same...

You might wanna give it a try
[http://screenface.66ghz.com](http://screenface.66ghz.com)

Thank you.
Can you explain a little more about what this does, and how to proceed?
The site says: Screenface-1.0. ~1.1 etc.
I like to understand it first.
You mean, that these are ready-to-use commands that even *I* could use?
A few more words about what this is exactly, would be appreciated.
Regards
John

---

### Post by xavier_r on 2007-08-03
> **Andavane said:**
> Thank you.
Can you explain a little more about what this does, and how to proceed?
The site says: Screenface-1.0. ~1.1 etc.
I like to understand it first.
You mean, that these are ready-to-use commands that even *I* could use?
A few more words about what this is exactly, would be appreciated.
Regards
John

Download version 1.3
And then extract it....
Read the README file to install...

Even though the file is a 10-12kb download...
The installation will download many MBs of software, and set up an appropriate environment for you...

Its actually called a GNU Screen Interface... which means, it handles and manages various app windows, on a single terminal using GNU Screen.

---

### Post by Alterax on 2007-08-03
Two books I have found indispensible:

Linux in a Nutshell
and Unix Power Tools

Both are from O'Reilly press.  The first is okay, the second is a bug-killer of a book but it's packed with all kinds of specialized scripts, commands, et cetera that will save a lot of time on more complicated tasks.

---

### Post by Andavane on 2007-08-04
> **xavier_r said:**
> Download version 1.3
And then extract it....
Read the README file to install...

Even though the file is a 10-12kb download...
The installation will download many MBs of software, and set up an appropriate environment for you...

Its actually called a GNU Screen Interface... which means, it handles and manages various app windows, on a single terminal using GNU Screen.

Thank you.
This looks interesting.
Is there something I can go and read first before installing it, so I can familiarize myself
with its capabilities beforehand?
Forgive me, I am from a decade of Windows and have a bit of a "Windows Mind",
which I am trying to shift, but it is taking some time ;)

Regards

John

---

### Post by xavier_r on 2007-08-04
> **Andavane said:**
> Thank you.
This looks interesting.
Is there something I can go and read first before installing it, so I can familiarize myself
with its capabilities beforehand?
Forgive me, I am from a decade of Windows and have a bit of a "Windows Mind",
which I am trying to shift, but it is taking some time ;)

Regards

John
Just install it with defaults... You will need administrative rights to install it... You dont need to know anything extra...
After Installation is done... If you have trouble using the environment you can press H for help in ScreenFace
Also you can read the screen manual
You can type:[B]
man screen[/B]
in the terminal to read the manual...

Also you can copy-paste these two lines in the end of your /etc/screenrc file
Type 
**sudo gedit /etc/screenrc**
to edit
```
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{= kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B} %d/%m%{W}%c %{g}]'
```
This modification allows you to view open windows in the bottom...

---

### Post by Andavane on 2007-08-06
> **rich.bradshaw said:**
> The main thing to realise is that you don't need to know every command, you need to generally understand the concepts behind it all, then you can just string things together when you need something.

The main thing to me is the pipe, or | . This lets you put the results of one command through another. Most of my scripting uses this to get complex results from simple things. 

For instance:

ls | grep cheese

will find any files in the folder with cheese in the name, this works by putting the results of ls through grep which finds things.

Useful building blocks are

Command : Description

ls : list a directory
cat : read a file out to screen
sort : sort whatever comes in
grep : finds things
awk : seperates data and many other things
sed : text replacement

etc.

Other useful things are 

> 

which writes the command to a file, e.g.

ls > filelist.txt

if you now

cat filelist.txt

you can read it out.

rm filelist.txt

to delete it.

You can string all these together like so

cat romeoandjuliet.txt | grep -c juliet

to find the amount of juliets in the script of romeoandjuliet, grep -c counts the occurances.

That's basically all there is to it.

Think of somehting you would like to do, then try and build up to it is my advice!

Thank you for taking the trouble to type out this list.
John

---

