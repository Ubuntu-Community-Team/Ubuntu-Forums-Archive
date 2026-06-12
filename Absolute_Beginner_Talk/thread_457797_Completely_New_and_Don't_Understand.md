---
title: "Completely New and Don't Understand"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Wifey93 on 2007-05-29
Hi I just got ubuntu and am trying to add some programs from add/remove programs, I get as far as applying the program and then this shows up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I search the forum and found an answer of:

Either in a root shell or else you can do this in a regular terminal:
sudo dpkg --configure -a
(enter user password when prompted, it will NOT echo to screen)

What is a root shell or a regular terminal and how do I enter the commands where it asks?? I'm so lost, can anyone explain this to me??  Pleaze help me. 

THANX!:(

---

### Post by SoulinEther on 2007-05-29
Terminal is in Applications > Accessories > Terminal. It's a command-line interface where you type things in to get results.

A root shell is a terminal mode where you can modify all files on your system. In Ubuntu you really don't need a root shell; if you want to run any program or do anything to modify your entire system, instead of entering a root shell you simply type "**sudo programname**" in a terminal and it'll run the program as the root "superuser".....

That might be a lot to swallow...

What program are you trying to install?

---

### Post by Wifey93 on 2007-05-29
I did what you said applications-accessories-terminal and entered the above advice, entered my password, 3 lines showed up and went back to the starting line.  I then continued to try and install abiword and a game and it's telling me to: please insert disk or fiesty fawn cd rom

---

### Post by Inxsible on 2007-05-29
So did AbiWord get installed successfully ?

---

### Post by SoulinEther on 2007-05-29
Ah... here's an idea:

Go to Sytem > Administration > Software Sources. See where it says "Installable from CD-ROM/DVD"? If you see "Feisty Fawn 7.04" or the like, uncheck it.

And you're sayin the "Password:" "Sorry, try again" appeared three times even after you entered your password correctly?

---

### Post by kevinlyfellow on 2007-05-29
Oops, already said...

---

### Post by mikewhatever on 2007-05-29
The same issue got solved a few days ago. Check the link [http://ubuntuforums.org/showthread.php?t=454546&highlight=dpkg+was+interrupted%2C+you+must+manually+run+%27dpkg+to+correct+the+problem](http://ubuntuforums.org/showthread.php?t=454546&highlight=dpkg+was+interrupted%2C+you+must+manually+run+%27dpkg+to+correct+the+problem)

---

### Post by southernman on 2007-05-29
> **SoulinEther said:**
> 

And you're sayin the "Password:" "Sorry, try again" appeared three times even after you entered your password correctly?
I think what she said was three lines went along... as in running the command, and dumped her back at the normal prompt.

That is how I read it at least ;)

---

