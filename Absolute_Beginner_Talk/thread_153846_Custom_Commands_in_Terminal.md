---
title: "Custom Commands in Terminal"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by xXx 0wn3d xXx on 2006-04-01
Is there a way I can "bookmark" a command in terminal ? So that I can go to a menu and select it ?

---

### Post by Pragmatist on 2006-04-01
Not sure I understand.  In a terminal you type commands.  You can make a custom command launcher, or a custom menu entry on the GNOME menu.  You can make an alias, if your main problem is to save time typing a long command with lots of parameters.  You can also make a shell script so that you can run a series of commands, and, like an alias, just write one command to fire all of them.  You could, of course, then take this alias or bash script and fire it from a launcher or menu.  But I'm not sure how you'd put it on a terminal's menu.  I don't think those are editable--although there probably is some terminal emulator out there that has that feature.

---

### Post by taurus on 2006-04-01
Are you talking about the history of your commands?  They should be in ~/.history...

---

### Post by IYY on 2006-04-01
A shell script, by definition is a sequence of terminal commands that can be executed as though they are a program.

Basically, it's a text file where the first line indicate which shell will be used to execute the command. Most commonly, this first line will be:

#!/bin/bash

or

#!/bin/sh

If you're just thinking of one line commands, it doesn't matter which shell you use. The rest of the lines in the file will be commands to be executed. If you just want to add the script to your menu, you can save it anywhere. However, if you want to run it from the terminal just by typing its name, you should save it in a directory in your path (for example, **/usr/bin**. echo $PATH to see all folders in your path)To make this text file executable: chmod +x *filename.*

---

