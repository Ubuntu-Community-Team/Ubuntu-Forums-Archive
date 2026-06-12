---
title: "YASQ..(Yet Another Scripting Question)?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by matey3 on 2008-02-26
Hello All;

I am trying to learn a little bit about scripts in Unix and was wondering why when I write a command on the command prompt, it works but if I put that same command in a script file it does Not work??
OK I did make it executable by chmod 755 Xfile
I also tried ./Xfile and sh Xfile to no avail?

Is there something that I am doing wrong?

OK it is a very simple command to change my prompt at this server which only shows # as its prompt but I want to change the prompt to show path name etc like this;

PS1="[\u@\h:\w] " 

but then I want to change the prompt back to what it was ( #) when I get thru with the server.(I dont want to change the .profile or whatever startups the server).

Thanks for your help in advance!

med

---

### Post by matey3 on 2008-02-26
Oh I just found out something...

When I do a sh it takes me into another shell ? I guess the PS1 command only works in ksh? (not sure) but when I do a ksh it lets me change the prompt but I still cannot do it via a file/script?

I guess when I tried sh myfile  (before) it took the sh (part of the command) and gave me another shell? 

Can some one also Please explain these different shells?(I only remember korn right now)...

Thanks Very Much!

---

### Post by wirelessmonkey on 2008-02-26
does your script have an interpreter line? i.e. #!/bin/bash

---

