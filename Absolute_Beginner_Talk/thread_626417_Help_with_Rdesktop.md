---
title: "Help with Rdesktop"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by newbie79 on 2007-11-29
Hi, I have just installed Ubuntu for the first time and now I need some advise regarding Rdesktop.

I want to create a icon/script on my desktop witch starts up rdesktop and connecting to a Windows Terminal Server (2003). (Not only starting the Terminal Server Client where i have to push connect)
I'm familiar with the -u and -p switches.

Someone please able to advise me?

Need to know:
How to script this?
What file extention should the script be saved as (im not familiar with linux...)? 
How to give correct permissions?

Thanks! :)

---

### Post by gigaferz on 2007-11-30
can you log in from terminal already?

i mean the command you would use to connect like tsclient ipaddress -x -y -z ...???

anyway i just did this

open a  text editor, 

type 

#!/bin/bash
rdesktop ip.add.re.ss

and save the file  on the desktop 

then right click it and go to properties, then permissions tab, all the way down check the box so it can run as a program.

or since you like the terminal better just type

sudo chmod a+x nameofyourfile

you dont need a file extension

---

