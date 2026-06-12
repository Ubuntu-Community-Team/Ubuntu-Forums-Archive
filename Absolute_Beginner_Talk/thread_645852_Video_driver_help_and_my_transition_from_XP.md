---
title: "Video driver help and my transition from XP"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by perrylearns on 2007-12-20
Hello all,

Windows XP ran slowly on my laptop, so I recently installed Xubuntu.  However, I am unable to get the display drivers to properly work on my computer. I am certainly eager and enthusiastic to learn, so any helpful advice regarding my problem would be excellent.  I have located the Linux (And Ubuntu, specifically) compatible drivers for my hardware, but I do not know how to apply them: 

http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID>=163

Despite coming with installation instructions, I do not know where to begin once I am at the Terminal.  Being a noob to Linux all together, I am not at all experienced in the use of the Terminal; but I am very interested in learning.  If someone would walk me through it as though I were mentally handicapped, I would greatly appreciate it.  In return I will promise to do my best to not ask such naive questions in the future.  :)

My screen resolution in XP was 1280 x 768, and the readme in the zip referenced above indicated that the refresh rate for said resolution is 60 Hz.  

Thanks in advance for the help.

---

### Post by kindafunnylookin on 2007-12-20
What happens when you put into the terminal
> startxwithout the quotes?

---

### Post by perrylearns on 2007-12-20
Quote:

xauth:  creating new authority file /home/perry/.serverauth.5097

X: user not authorized to run the X server, aborting.
Couldn't get a file descriptor referring to the console

---

### Post by Papa-san on 2007-12-20
Run: sudo startx 

Then put password in..

---

### Post by perrylearns on 2007-12-20
**Quote:**

[INDENT]xauth:  creating new authority file /home/perry/.serverauth.6467

X: warning: process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
      If this server is no longer running, remove /tmp/.XO-lock and start again.[/INDENT]



**Wireless internet currently works on my computer, but I am not near a wireless connection at present.  I am not sure if that is relevant to the steps.**

---

### Post by Papa-san on 2007-12-20
I don't know what you're running into, but I saw the 'user not authorized" and any time you get that, you need to do it as superuser (sudo)

You might want to do a search on your graphics card to find some specific instructions.

---

