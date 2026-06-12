---
title: "Path"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Stuperfied on 2006-04-11
Hi, i added a program to the internet menu under the Applications panel and now wish to add the directory to the path so i dont have to include the full path in the internet menu shortcut. Can anyone tell me how to do this?

---

### Post by taurus on 2006-04-11
You can modify your ~/.bashrc to include an additional path to it.  Open a terminal with Applications -> Accessories -> Terminal and type
```

gedit ~/.bashrc

```
If you see any line that starts with PATH, then scroll down to the bottom of the file and add these two lines to it, assuming the new path you want to add is /home/Stuperfied/program_a...
```

PATH=$PATH:/home/Stuperfied/program_a
export PATH

```
Save the change and at the prompt, type
```

source ~/.bashrc

```
Now, just type the name of the program in /home/Stuperfied/program_a in a terminal and it will be executed without including the whole path...

---

### Post by trent dillman on 2006-04-11
Or, you could symlink it to somewhere in your path

```
sudo ln -s /path/to/program /usr/bin
```

Or you could add ~/bin to your path, make a bin directory in your Home folder, and symlink it there

```
ln -s /path/to/program ~/bin
```

---

### Post by Stuperfied on 2006-04-12
I noticed that most programs when they are installed, place a link or script etc in the /usr/bin directory so that they do not need to be in the path to run. Hence, since this seems to be the way things are done, it made sense to follow trent dillman's advice. I have added a link to the program in the /usr/bin directory. Doesnt sit right with me but when in rome, you know...

Thank you both once again.

---

### Post by trent dillman on 2006-04-12
No problem.

For the benefit of others, here's another hint: if symlinking to /usr/bin doesn't work for the application (like LimeWire), instead try placing a script in /usr/bin that changes to the directory that app is installed, then runs it:

```
#!/bin/bash
cd /path/to/program
./programName
```

---

