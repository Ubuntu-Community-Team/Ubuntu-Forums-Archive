---
title: "Self extracting .sh file"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by davidjd on 2007-03-14
I think I messed something up.  I'm trying to install crossover, I downloaded a .sh file that according to the instructions should just run.  It doesn't. For some reason when I click on the file it loads in editer.  (Bye some reason I mean I messed it up)

Thanks in advance,
DD

---

### Post by annda on 2007-03-14
is the file executable? if not, right-click on it and change permissions, or the simple way in the terminal:
chmod +x file_name
or
sudo chmod +x file_name
and:
./file_name.sh

---

### Post by carusoswi on 2007-03-18
I don't get it.  I downloaded crossover last night, clicked on the open button, the installer front end appeared and I clicked the appropriate buttons and it was done.

Had to reinstall ubuntu this morning, downloaded crossover again, this time, it won't load.  I followed your advice to change permission in terminal - file name turned to green (is that good?).

Now, what do I do to make the file run?

I tried sudo and typed the file name, no good.  Command not found.

If you can help me, I'd be most appreciative.

Caruso

---

### Post by taurus on 2007-03-18
Are you sure you were in the right directory when you tried to install it?  What's the output of this command from a terminal then?

```
ls -la ~/Desktop
```

---

### Post by carusoswi on 2007-03-18
I was in the right directory.  I have solved my problem - but am bothered that I don't have a better handle on what to do when things don't work properly for me.  Perhaps you can help me better my understanding.

First - what worked to solve my problem:  I opened Firefox, downloaded a fresh copy of Crossover, then, Tools-->Downloads.  I right clicked on the new file and selected "Open containing folder".  That brought up a window that displayed icons representing both downloaded files, the first had a padlock icon over it. I right-clicked the other one and that opened a dialog box where there was a box to click to allow the file to be opened as an executable file.  Then, I just double clicked the file name, and another box came up where I was offered the opportunity to open the file or run it.  I clicked run and the install proceeded without a problem.

As mentioned above, the file that I had Chmod'ed per your instructions had a padlock icon over it - I guess what I did corrupted it somehow - I don't know, so I just deleted it.

Struggling hard to learn this ubuntu OS.  I know that part of my problem is 20 some years of WinIndoctrination.  OTOH, ubuntu isn't all that intuitive, either.

Thanks for your help.

Caruso

---

