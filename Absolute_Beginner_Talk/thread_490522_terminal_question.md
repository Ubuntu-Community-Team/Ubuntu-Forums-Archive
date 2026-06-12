---
title: "terminal question"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-02
I am currently have wireless issues in another[ [COLOR="RoyalBlue"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=488287").

As i am working those out, i have a terminal question.  I have downloaded the necessary driver for my belkin wireless card and is residing on my Gnome desktop.  Correct me if i am wrong but isnt the file path for the desktop:  /home/username/Desktop?

I tried running the driver from the terminal but it would always say that the path was not found or the directory doesnt exist.  Any Suggestions?

---

### Post by eljalill on 2007-07-02
What about you go to /home, look for the username (use ls), go to that, look for the Desktop (ls) and then look for the file (ls) again. remember that spaces in file names are treacherous and have to be marked with a backslash. Also using the autocompletion (tab) helps.

---

### Post by Raineer on 2007-07-02
I would agree, do the following in this order and see if you fall out at any point
```
cd /home
cd username (no slash)
cd Desktop (case sensitive!)
ls

```
At this point you should be able to "run" the program you downloaded. 'ls' should list every file on your desktop.

---

### Post by ITdrummer on 2007-07-02
Ok so once i navigate, and are able to see the file on my desktop, i can type: 
```
run *filename*
```

and it SHOULD work?

---

### Post by Bachstelze on 2007-07-02
> **ITdrummer said:**
> Ok so once i navigate, and are able to see the file on my desktop, i can type: 
```
run *filename*
```

and it SHOULD work?

No. What kind of file is it ?

---

### Post by trak87 on 2007-07-02
Don't work blindly. Use "ls" or "ls -l" liberally to see what files you actually have in those directories. "ls" *lists* the contents of the directory and is one of the most important commands you can use at the command line.

---

### Post by Raineer on 2007-07-02
Not exactly, it will depend on the file type. If it ends with .sh or .exe then that means it's a script (or exec) file that you can run.
This takes 2 steps to "run".  First you get to the Desktop directory in console where you can see the file with 'ls', then:
```
chmod +x filename.sh
./filename.sh
```

The first line makes it executable, the second runs the script.  Now if it *doesn't* end with .sh or .exe, we need to know the whole filename so we can tell you how to handle it. You definitely don't want to try to "run" a .tar or similar compressed file.

---

### Post by mpeters on 2007-07-02
If you are in the same directory as the file you need to type:

[INDENT]./filename[/INDENT]

to run it. However that will only work if the file is executable. To see if the file is executable type:

[INDENT]ls -l filename[/INDENT]

You should see something like:

[INDENT]-rwxr-x--- 1 username group   125 2007-01-01 14:49 filename[/INDENT]

Where the x's mean that the file is executable by "username" and members of "group".

If the file isn't executable, ie there are no x's, you can make the file executable by running:

[INDENT]chmod +x filename[/INDENT]

Now you should be able to run it:

[INDENT]./filename[/INDENT]

All the above assume you are in the same directory as "filename". ie if the file is in /home/username/Desktop, run:

[INDENT]cd /home/username/Desktop[/INDENT]

to change directory to /home/username/Desktop first.

---

### Post by ITdrummer on 2007-07-02
Well the file i am trying to open is a compressed file. I believe the name is BelkinDriver.tar.gz

I also have that file already decompressed (BelkinDriver)

All of the how-tos on how to get a wireless connection working, describe downloading the driver then running it from the terminal.  I just could never get the file path correct.  Damn Broadcom chipsets!

---

### Post by ncappel1 on 2007-07-02
you could also use the shortcut for your home directory desktop: ~/Desktop

---

### Post by ITdrummer on 2007-07-02
and just to clarify........EVERYTHING IN LINUX IS CASE SENSITIVE.  correct?

---

### Post by annda on 2007-07-02
always use **autocompletion** in the terminal. type the beginning of the command or filename and hit the <TAB> key. it should tell you what is available. if there are more possibilities, hit TAB twice to get them listed.

for example, if you have uncompressed the driver file to a folder Belkinsomething on your desktop, go:

cd De<TAB> 

this will give you Desktop/

type Belk and hit <TAB> again

you will get the directory or the file. 

as to what to do with the file you need to consult the howtos or tell us exactly what you are following and which step you are stuck at.

---

### Post by annda on 2007-07-02
> **ITdrummer said:**
> and just to clarify........EVERYTHING IN LINUX IS CASE SENSITIVE.  correct?

YES.

---

