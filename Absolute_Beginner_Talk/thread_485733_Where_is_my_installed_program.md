---
title: "Where is my installed program?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by sanderella on 2007-06-27
I installed ace-of-penguins using synaptic. Now I can't find it. No icon or link to it. Where will it be?

---

### Post by aeiah on 2007-06-27
if it isnt in your games directory then you may need to add it. can you run ace-of-penguins from the terminal? (just to make sure it has indeed installed properly)

im not on ubuntu right now but you can add things to the menu by right clicking and editing the menu i believe.

---

### Post by sanderella on 2007-06-27
Hmmm... terminal says there is no such file or directory, but according to synaptic it is installed.:confused:

---

### Post by aeiah on 2007-06-27
in the terminal type 'ace' and then press tab a few times to get a list of everything you have installed that begins with ace, maybe it's un-hyphenated or something. that does seem odd though...

---

### Post by 3rdalbum on 2007-06-27
Ace Of Penguins is actually three different programs.

Go into Synaptic and search for the aceofpenguins package that you installed. Right-click it, select Properties, then go into the "Installed Files" tab. You will see the three programs listed in a directory which contains "/bin/" in it (i.e. /usr/bin, or /usr/local/bin") or possibly "/usr/games/".

Once you know the actual names of each program, you can just type that name into the terminal to run the program (or set up a launcher or menu item with the name as the command).

---

### Post by sanderella on 2007-06-27
terminal says bash: ace: command not found...

---

### Post by sanderella on 2007-06-27
thanks 3rd, will try that

---

### Post by sanderella on 2007-06-27
thanks 3rd, that worked!:popcorn:

---

