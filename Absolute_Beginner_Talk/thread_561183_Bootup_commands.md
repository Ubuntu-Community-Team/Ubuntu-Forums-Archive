---
title: "Bootup commands??"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jazpearson on 2007-09-27
Ok, this is my problem.

I have a program i want to run, from the terminal...... and i can get it to work, but i have to enter these commands to set it up first.

csh
% setenv SSW /usr/local/ssw
% setenv SSW_INSTR "secchi eis xrt"
% source $SSW/gen/setup/setup.ssw

and then, still in the c shell.......

% sswidl

which loads the program.

what i'd like to be able to do...... is to just be able to type in sswidl in the normal bash terminal, rather than going into csh and typing them all in. I'm sure this is possible, but of course i'm not too sure how!!

---

### Post by rax_m on 2007-09-27
Hi there, 

I think what you want to do is setup those environment variables in your profile. 
In your home directory there is a file called .bash_profile (notice the . ). If you add these to your profile then whenever you open a terminal window they should be setup already and you'll just have to enter in the command that you need. 

Edit the file using your favorite editor and just add those setup lines into it. You may have to logout and back in for the changes to take place. 


Cheers
Rax

---

### Post by jazpearson on 2007-09-27
Thanks,

I can see where you're coming from. But i think the problem lies in that these commands need to be run in a c shell, when my terminal is bash.

If i put the following in to the .bash_profile file:

-------

csh
setenv SSW /usr/local/ssw
source $SSW/gen/setup/setup.ssw

--------

then all i get when i open a terminal is a % sign....... indicating of course that you are in csh, but the other commands, ie. the setenv and source lines have not been loaded.

there's prob something really simple about what i'm doing/asking, but i'm fairly new to ubuntu, so please bear with me!! 

thanks

---

### Post by dreadlord_chris on 2007-09-27
first line of your script should be:
```

#!/bin/csh

```
this tell the interpreter what shell to run the script in...
which also means you don't need to **csh** from within the script...

---

