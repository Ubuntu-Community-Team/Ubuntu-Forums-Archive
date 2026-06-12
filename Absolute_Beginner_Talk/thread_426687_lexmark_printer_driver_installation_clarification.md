---
title: "lexmark printer driver installation clarification?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by gpilkay on 2007-04-28
Hello, I had a question about how to proceed in my printer driver installation.  There are instructions here:
[http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printers](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printers)
But I'm not sure I understand them, or what exactly I should be typing, with the # marks, etc.  I'm very new at this...

Right now, on my desktop, after I just double-clicked it, I have a folder called lexmark, and a file in it called (copied dirctly)

z600cups-1.0-1.gz.sh

So...now what should I do?

Sorry for the dumb question...

---

### Post by Austin_KW on 2007-04-29
For those command '$' is the prompt if you open a terminal you will see this at the end of your prompt. The prompt is usually set to show who and where you are but dont worry about it.

The '#' is a shell comment, The shell is the program running in the terminal and it interprets and executes the commands. The comment '#' and everything after it is ignored.

Open a terminal (applications->accessories->terminal)

The actual command are everything between the '$' and the '#'. Just cut and paste them (one line at a time) into your terminal and hit return to execute them. Make sure you don't copy and paste the '$' prompt but obviously copying the comments would be fine as they would be ignored.

---

### Post by gpilkay on 2007-04-29
Thank you!  But how do I tell it where the file is (currently on the desktop in the lexmark folder?)

---

### Post by Austin_KW on 2007-04-29
When you open a terminal is will open in your home directory (folder). Your Desktop is a sub-directory in you home directory. To get to the lexmark directory in your home directory

cd Desktop/lexmark

if you have z600cups-1.0-1.gz.sh in this directory the it looks like you have to do
"tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz" 
and the following commands ...

---

### Post by gpilkay on 2007-04-29
Thank you.  I did it, was told that alien wasn't running as root, and re-did it with the sudo command.  Still isn't working though.

I posted the full list here:
[http://ubuntuforums.org/showthread.php?p=2560266#post2560266](http://ubuntuforums.org/showthread.php?p=2560266#post2560266)

Thank you!  I'm getting there, slowly...

---

