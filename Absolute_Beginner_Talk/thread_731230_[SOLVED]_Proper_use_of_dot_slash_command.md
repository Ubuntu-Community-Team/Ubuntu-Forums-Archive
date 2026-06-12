---
title: "[SOLVED] Proper use of dot slash command"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by rtrdom on 2008-03-21
What does the terminal command ./ mean in Ubuntu tutorials? It does nothing for me
yet so many people say to use it for various purposes.

---

### Post by sayakb on 2008-03-21
./filename would execute a file called "filename" in the current directory.

---

### Post by TheLions on 2008-03-21
that means "run" file as executable...

---

### Post by DSn0wMan on 2008-03-21
./ means run the following command from this directory. Example ./myscript.sh will run myscript.sh if it is in the current directory.

---

### Post by rtrdom on 2008-03-21
Thank you all for your responses. Now Maybe I can get something done with it.

---

### Post by dixonstalbert on 2008-03-21
This explanation below is similar but a  little different than what has been posted. The key point is that even if you're in the right directory and type the executable file name out and hit enter, it may not run because you have to explicitly tell the shell that the file is in the current directory by typing "./" before the file name. 

I cannot remember where I got this from, but I had a heck of a time finding it because I kept googgling  "./ "  and not the words " dot slash "
Anyways here is the definition I found:

The dot slash command:


dot slash or './' : set current path to current directory



 './' precedes a script file name to tell the command interpreter the file is in the current directory; Unlike DOS, in unix systems, the directory you are currently in, is not automatically in the PATH, so you have to tell BASH where the file is by using ./filename

NOTE: by default only /usr/bin  and /usr/sbin are in the PATH; even you're home directory in NOT in the PATH and you need to put ./ in front for the shell to find the file.

---

