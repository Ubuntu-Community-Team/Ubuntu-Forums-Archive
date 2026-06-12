---
title: "Advice needed"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-11-17
Hi All,

Can anyone point me in the right direction. I am looking to create a shortcut on my desktop. I want to be able to double click an Icon on my desktop which will open up a terminal window and run a particular file. I want it then to be able to close the terminal window once the file has run and closed.

I think that what i am after is a script but to be blunt i know ansilutely nothing about how to create one. Is there a good how to somewhere? is the above possible? also i would really also like it to have another one which would shut the pc down by double clicking the icon on the desktop I know there is already something similar in the applets but this would be used for a specific reason.

cheers for reading
niteblind

---

### Post by gareththegeek on 2006-11-17
Hi,

You could make a shell script file
The file begins with
#!/bin/bash

then here you can just write commands as if you were entering them into the terminal...

Once finished you need to add execute permissions to the script file you've just made..
chmod +x myscript.sh

and put the script somewhere where it can be seen...
if you type env at command prompt you can see your environment variables...if you put the script in one of the folders listed in the PATH variable then you can run it by just typing its name at the command prompt.

Now you can create a custom application launcher shortcut and for the command enter the name of your script..

Here's a link:
[http://www.linuxcommand.org/wss0010.php]("http://www.linuxcommand.org/wss0010.php")

HTH
G!

---

### Post by niteblind on 2006-11-17
cheers for the reply really helps
niteblind

---

