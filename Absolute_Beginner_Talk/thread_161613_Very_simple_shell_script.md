---
title: "Very simple shell script"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by BrownieMan on 2006-04-17
I just need a shell script to do the commands I would normally type in, like the commands people give you in the howto sections that are 20 lines long. So how do I write a very simple script like that?

---

### Post by htinn on 2006-04-17
Here's an example of a bash script:

```
#!/bin/sh
RESULT=$(zenity --entry --text 'Search for what package:')
apt-cache search $RESULT | less
```

Just save that into a file in any text editor, then make it executable and run it.

---

### Post by aysiu on 2006-04-17
Step by step...

Go to a terminal and type ```
gedit nameofscript
``` (or *kwrite nameofscript* if you're using KDE.
Type ```
#!/bin/sh
``` Then copy and paste all the lines of code you want in there--one line per command. Save the document. ```
chmod +x nameofscript
``` To run the script, type ```
./nameofscript
```

---

### Post by BrownieMan on 2006-04-17
so if i wanted to have a script named "commands" to, for example, update ubuntu I would have the file have the follwing lines:
> 
#!/bin/sh
sudo apt-get update
sudo apt-get upgrade
chmod +x commands

and then I just go to the directory the shell script is and run the command

> chmod +x commands

Is that correct? It's partly for my benefit and anyone else in the future.

---

### Post by ds[de] on 2006-04-17
This is correct, but you don't need the 
```
chmod +x commands
```
within the commands file, since this command will only be executed if the file is already marked as executable.

So you can remove this last line, but you'll still have to type it in the console once.

Regards,
ds[de]

---

