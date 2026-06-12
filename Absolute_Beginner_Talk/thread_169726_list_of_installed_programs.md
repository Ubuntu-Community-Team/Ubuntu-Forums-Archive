---
title: "list of installed programs ?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by medya on 2006-05-03
yesterday I had marked many programs in my synpatic package manager to be installed ,
I dont remember many of them  ... but they have not been added to my application menu.

is there any way to have a list of installed programs ? 

in synpatic I can see list of installed packages , but they are too many many to see what is what .

for example I had installed a program to Read Whatever on the Screen for me (text to speech) where is that program?

I wish there was something to see the list of installed programs.

I tried to install debian menu with automatix, but I cant find debian menu in my appliaction list either.

---

### Post by hw-tph on 2006-05-03
To view the currently installed packages, use **dpkg -l**.


Håkan

---

### Post by funkenstein on 2006-05-03
```
dpkg -l | less
``` will let you scroll up/down by 1 line, using the up/down arrow keys, by a page using the pageup/pagedown keys. use q to quit out of less... this way you can scroll up and down the list, rather than just having a gigantic list of doom....

also, look in some of the .desktop files in /usr/share/applications/ to see the syntax used to make shortcuts in your applications menu, or the alacarte menu editor (previously known as smeg) to add them by GUI methods.

hope this helps.
me.

---

### Post by medya on 2006-05-03
using dpkg -l 
I foudn the program that I had installed

ii  festival                               1.4.3-17ubuntu1                      general multi-lingual speech synthesis syste
ii  festlex-cmu                            1.4.0-6                              CMU dictionary for Festival
ii  festlex-poslex                         1.4.0-5                              Part of speech lexicons and ngram from Engli
ii  festvox-kallpc16k                      1.4.0-5                              American English male speaker for festival,
ii  festvox-kdlpc16k                       1.4.0-5                              American English male speaker for festival,

but how I can run it ?

---

### Post by Solver on 2006-05-03
Simply trying to execute festival in the command-line should do. If not, you can try another command, ```
whereis festival
```. It will let you know where the executable you need to run is.

---

### Post by ComplexNumber on 2006-05-03
> It will let you know where the executable you need to run is. they should already be in his PATH, so just typing the name of the application should suffice. a useful tip here: install a package called 'bash-completion' because it allows the user to type in the first few letters of an applications (eg 'korg') on the commandline, then press the TAB button twice(quickly in succession) to see the list of applications installed that begin with 'korg'. this will then bring up 'korganizer' and others.  i have always found it useful.

---

### Post by medya on 2006-05-03
I cant find any package in the synpatic named "bash-completetion"

---

### Post by ComplexNumber on 2006-05-03
[quote=medya]I cant find any package in the synpatic named "bash-completetion"[/quote]
it is there. try one of the other repositories.

---

### Post by medya on 2006-05-03
how I can try Other Respos ?
I have always had it with repos, never learnt using them.

---

### Post by nanotube on 2006-05-03
ehrm, you dont need no bash-completion or anything like that. tab-completion feature is available in bash by default.  just try it with "gno" for example (cuz lots of programs begin with "gnome".). type "gno<tab><tab>" and you should see a list of a bunch of programs that begin with "gno". 

another thing - you can also use dpkg to list all the files that were installed with a package - type 
```
dpkg -L packagename
```
then see what files are located in /usr/bin - those are most likely the executable.
you can also do the same thing with synaptic - right click on package, select properties, and look at the "installed files" tab. 

that should help you find the executable. :)

---

### Post by 99bluefoxx on 2007-12-19
how can i use this to show only non-standard[ones that dont come pre-installed] installed packages?

---

