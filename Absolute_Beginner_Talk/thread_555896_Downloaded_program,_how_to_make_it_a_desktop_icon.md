---
title: "Downloaded program, how to make it a desktop icon?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by monty22 on 2007-09-20
I did a sudo apt-get install for GNUBG, but I can only run it by typing "GNUBG" in the terminal.  I'd like to make it a desktop icon, but when I search for GNUBG, it can't find it.  Any suggestions?  

Also, is there a way of hiding that bar on top of the screen, the one with Applications, Places, System, etc.?

Thanks.

---

### Post by Het Irv on 2007-09-20
Not sure about the first part but for the second right click on the bar and go to properties.

---

### Post by Lord Illidan on 2007-09-20
Regarding the first part, it's pretty easy. Just rightclick on the Desktop, chose Create Launcher.

Type-> Application
Name - Whatever you want..let's make it GnuBG
Command -> gnubg
Comment -> Whatever you want..

The command must be in lower case.

I couldn't find any icon for GnuBG...but I don't think it's such a big deal..

---

### Post by monty22 on 2007-09-20
I did that and it looked like everything went fine, but when I tried to open it, a screen flashed on for a second or so (couldn't read what it said), and then nothing else happened.  Any ideas?  I typed in "gnubg" (no quotation marks) for the command, and it was set as an application.

Thanks again.

---

### Post by Maestro23 on 2007-09-20
> **monty22 said:**
> I did that and it looked like everything went fine, but when I tried to open it, a screen flashed on for a second or so (couldn't read what it said), and then nothing else happened.  Any ideas?  I typed in "gnubg" (no quotation marks) for the command, and it was set as an application.

Thanks again.

Try the full path to the program.  Don't know what it is, open a terminal and type:

> locate gnubg or which gnubg

---

### Post by monty22 on 2007-09-20
Okay, when I typed "locate gnubg or which gnubg" I got a huge list that just kept going, so I had to shut it down.  When I reopened the terminal and just typed "locate gnubg" I got about 20 lines.  For example, one was:  /usr/bin/gnubg
 
Any idea of what I should look for?

Thanks.

---

### Post by Maestro23 on 2007-09-20
> **monty22 said:**
> Okay, when I typed "locate gnubg or which gnubg" I got a huge list that just kept going, so I had to shut it down.  When I reopened the terminal and just typed "locate gnubg" I got about 20 lines.  For example, one was:  /usr/bin/gnubg
 
Any idea of what I should look for?

Thanks.

That's it. Try that path in your icon window.

---

### Post by monty22 on 2007-09-20
Okay, I had to check the run in terminal box in order to get the launcher to work.  First the terminal comes up, then the program.  If I then exit the terminal window, the program also closes.  Is this the way it is supposed to work?

When I replaced gnubg with /usr/bin/gnubg, it did not work.  It did the same thing as before, which is that a window flashed quickly and nothing happened.

---

### Post by Maestro23 on 2007-09-20
> **monty22 said:**
> Okay, I had to check the run in terminal box in order to get the launcher to work.  First the terminal comes up, then the program.  If I then exit the terminal window, the program also closes.  Is this the way it is supposed to work?

When I replaced gnubg with /usr/bin/gnubg, it did not work.  It did the same thing as before, which is that a window flashed quickly and nothing happened.

Hold on, I'm going to install on my system and see what the deal is. 

Someone might beat me back with an answer though. :smile:

---

### Post by fjf314 on 2007-09-20
> **monty22 said:**
> Okay, I had to check the run in terminal box in order to get the launcher to work.  First the terminal comes up, then the program.  If I then exit the terminal window, the program also closes.  Is this the way it is supposed to work?

I believe if you put an ampersand (&) after the command, it should set the program to run in the background, thus allowing you to close the terminal. So your command would be:

```
/usr/bin/gnubg &
```

That's only really a temporary solution, though, since I'm sure you don't want to have to close the terminal every time you launch the application.

---

### Post by Lord Illidan on 2007-09-21
I'm on gutsy atm, and I am going to try out making a launcher, too.

---

### Post by Lord Illidan on 2007-09-21
Ok, I got a fix.

Instead of just gnubg, edit the command to read :

```
gnubg -w
```

And you don't need to launch in terminal, neither.

I got this from the man page of gnubg, which you can access by typing :
```
man gnubg
```

The -w switch will : Ignore tty input when using window system.

---

