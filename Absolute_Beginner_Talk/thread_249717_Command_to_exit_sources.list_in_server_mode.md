---
title: "Command to exit sources.list in server mode"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sef on 2006-09-02
I have a Dell 4000 Inspiron with a PIII and 128 mb ram.  Xubuntu is giving me a problem with sounds popping up, so I thought I would try icewm.  The server install is no problem, and I can get into the sources.list.  However, how do you exit and save the changes?

I am following the [Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems"), and here is where I run into the problem:

> sudo vim /etc/apt/sources.list

Uncoment all official repositories by removing # at the beginning of the line. Return to the command line and type:

How do I return to the command line?

---

### Post by deanlinkous on 2006-09-02
I would suggest using nano or nano-tiny they are about the simplest editors to use since the main commands are listed at the bottom. I honestly do not use vi unless I have a cheat sheet handy. :)

sudo nano /etc/apt/sources.list
sudo nano-tiny /etc/apt/sources.list

Hopefully one of those is already installed. If not...
[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

---

### Post by catlett on 2006-09-02
Hi SEf,

I had a page bookmarked before, [http://vimdoc.sourceforge.net/vimum.html](http://vimdoc.sourceforge.net/vimum.html) I never got through it. Sorry I am not posting an answer but it should be in there, if noone replies with the answer it may be worth browsing.

I'll try and find the command but I wanted to post the url to you before I started searching.

P.S. Found this 
> *02.7*  Getting out

To exit, use the "ZZ" command.  This command writes the file and exits.

        Note:
        Unlike many other editors, Vim does not automatically make a backup
        file.  If you type "ZZ", your changes are committed and there's no
        turning back.  You can configure the Vim editor to produce backup
        files, see |07.4|.
Alright I have the uncomment figured out. First move the cursor with the arrow keys until the cursor is over whjat you want to remove, in this case #. Type ```
x
```That deletes the character. After you delte what you want to, enter ```
ZZ
```That closes the doc and puts you back at the command line.

---

### Post by Sef on 2006-09-03
Deanlinkous: Thank you for you suggestion.  I used nano and had no problems.

Catlett: Thank you for suggestion too.

---

