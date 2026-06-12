---
title: "How do I install this?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Axis on 2006-12-22
I was wondering as how to install things that pretty much do not standardly show up in the add/remove programs list thing. I downloaded a game called Cube I do belive. Well I downloaded the files anyways and right now they are in a folder off of my desktop called games. But now that I have downloaded the files what do I actually do to install the game and play it?

Thanks,
Axis

(Game link below)
[http://sauerbraten.org/](http://sauerbraten.org/)

---

### Post by po0f on 2006-12-22
Axis,

[quote=http://sauerbraten.org/docs/config.html]For GNU/Linux: gunzip, chmod +x sauerbraten_unix and then ./sauerbraten_unix. Needs a decent and compliant OpenGL implementation.[/quote]

---

### Post by Axis on 2006-12-22
Ok I am not completley sure If I understand what you are saying but I belive I need to have gunzip installed. Where can I find it? I found the website for it but nowhere to download it. Is it already on my computer? And if so I don't completley understand what I need to do after I have gunzip installed (if I don't already have it installed)

---

### Post by po0f on 2006-12-22
Axis,

What's the name of the file that you downloaded?

---

### Post by Axis on 2006-12-22
I just renamed it so it is now,

star.gz

---

### Post by po0f on 2006-12-22
Axis,

From the terminal:
```
[FONT="Courier New"]$ cd /path/to/download
$ gunzip star.gz
$ chmod +x star
$ ./star[/FONT]
```
The first command takes you to the directory you downloaded it to (if it was your Desktop, type in `cd ~/Desktop`).  The second command unpacks the archive.  The third one gives the files execute permission, and the fourth one runs it.  You will have to cd to the directory and `./star` everytime you want to play it.

---

### Post by PrairieShaman on 2006-12-22
Oh my.

Im downloading it as I type this. It looks like a cool game, so if I get it installed I will make sure I post how I did it in this thread. ;)

---

### Post by Axis on 2006-12-22
ok i am having problems with the first part, i have the file on my desktop, what exaclty do i need to put in to the terminal?

---

### Post by po0f on 2006-12-22
Axis,

I posted the *exact* commands you need above.

[quote=po0f]Axis,

From the terminal:
```
$ cd /path/to/download
$ gunzip star.gz
$ chmod +x star
$ ./star
```

The first command takes you to the directory you downloaded it to (if it was your Desktop, type in `cd ~/Desktop`). The second command unpacks the archive. The third one gives the files execute permission, and the fourth one runs it. You will have to cd to the directory and `./star` everytime you want to play it.[/quote]

Just change `cd /path/to/download` to `cd ~/Desktop` or `cd Desktop`.  The dollar sign ($) is not a command, it represents your terminal prompt.

---

### Post by Axis on 2006-12-22
owner@owner-desktop:~$ cd~/Desktop
bash: cd~/Desktop: No such file or directory


What am I doing wrong?

---

### Post by po0f on 2006-12-22
Axis,

There's a space between them.
```
[FONT="Courier New"]$ cd    ~/Desktop[/FONT]
```

---

### Post by Axis on 2006-12-22
Thanks alot for helping me through this. 

The file seems to have somwhow switched to .tar format and when I try and gunzip it that way (or in .gz format) it no longer works. How do I solve this problem?

---

### Post by po0f on 2006-12-22
Axis,

So it goes from star.gz to star.tar?
```
[FONT="Courier New"]$ cd Desktop
$ tar xvf star.tar[/FONT]
```

After that, please post the output of:
```
[FONT="Courier New"]$ ls  -l  ~/Desktop[/FONT]
```

---

### Post by Axis on 2006-12-22
owner@owner-desktop:~/Desktop$ cd ~/Desktop
owner@owner-desktop:~/Desktop$ tar vxf star.tar
tar: star.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


Should I possibly just redownload the file, renaming it only once (I renamed this one several times) or possibly just keeping the same longer name. I noticed it wasnt untill I tried extracting the files that it changed. (I actually completley understand why it did what it did, just not how to fix it) I will try and redownload the file and post my results if I still don't get it.

---

### Post by po0f on 2006-12-22
Axis,

You already gunzip'ed the file right?  Just post the output of ls then:
```
[FONT="Courier New"]$ ls  -l  ~/Desktop[/FONT]
```

---

### Post by po0f on 2006-12-22
Axis,

Renaming the file did not help.  ;)  You should have just kept whatever name it was when you downloaded it.  Redownload it to your desktop and do what I posted above.

---

### Post by Axis on 2006-12-22
No, it wont gunzip the file that is my point. It says it isn't there and that may be because the file is no longer in .gz format (Just a guess is that is gunzip format??)

---

### Post by jordanmthomas on 2006-12-22
Also, please post the output of
```
file * | grep star
``` once you're in your Desktop directory.
I have a feeling you still have a .tar.gz but renamed.

(The easiest way to extract it, by the way, is to just right click on the file and go to extract here)
Then, from there, you can go into the terminal to get to the files inside.

---

### Post by PrairieShaman on 2006-12-22
this was easy.

download the file. 

unzip it. I located the file in my browser "places - home folder" and found where the file was, I right clicked on it and clicked "Extract Here"

It extracted the game folder. inside the folder i found:

bin_unix
CVS
data
docs
packages
src
config.cfg
README.html
sauerbraten_unix
servers.cfg

I double clicked on "sauerbraten_unix" it asked if i wanted to run, or run int the terminal. I clicked run. 

The game loaded up. I adjusted my settings (maximum) and away I went playing the game online within about 2 minutes of the download finishing. 

Great!!!! Thanks a lot for the hookup for a sweet linux game!

---

