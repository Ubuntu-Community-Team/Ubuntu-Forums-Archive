---
title: "terminal window navigation"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-03-30
can anyone provide instructions on basic navigation of directories under the terminal window?  i am trying to run a specific command but i cannot figure out how to navigate to the folder within the terminal window... i have tried cd /folder, cd folder, and even from the root of the filesystem like cd /home/username/folder, but no luck so far.

is there also a command that can tell you the directory you are currently in under a terminal window?  like dir within DOS.

thanks.

---

### Post by FreewareFan on 2008-03-30
Your command prompt will tell you what directory you are currently in.  If it shows a ~, then that means you are in your home directory. Otherwise, it will have within the prompt where you are, like this from my terminal:
   m@m-laptop:/sys/class/bluetooth$             This shows that I'm in the directory of /sys/class/bluetooth .   The $ means I'm using the terminal as a regular user, not as a root user.  

You are using the proper way to change directories, by using cd  then the path.  The thing to remember, is that the path is case sensitive, so if there are capital letters, you have to use them.  Also, if there are spaces in the directory name, you have to encase the path with single quotes like this:

   '/etc/shared/My Test Directory'

---

### Post by jjgauthi on 2008-03-30
Welcome,

I am new but I shall share my knowledge.

to find out what is in the current directory you are in type *ls* - it is similar to the windows *dir* command.

Now to move between directories its very similar to windows use the *cd* command the directories are case sensitive.

for further help type *man ls* or *man cd* i think those will help you learn about the command line navigation

---

### Post by Michael.Godawski on 2008-03-30
use cd for change the directory
use ls for showing all files and subfolders in a directory
use the tab-key to autocomplete folder and file names

---

### Post by Matt26 on 2008-03-30
thanks i think i was missing the capital letter in the directory i was trying to navigate to... how do you backtrack through directories?  so if i'm in /home/username and i want to get back to /home- is there also a command for getting back to the root of the filesystem?

btw i tried 'man cd ' but i got no listing...

---

### Post by drs305 on 2008-03-30
```
cd ..
```
will take you up one level.

```
cd /
```
will take you to the root directory.

Here's a link to navigating the terminal:
[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands)

---

### Post by FreewareFan on 2008-03-30
And  cd ~ will take you  back to your home directory, which is where the terminal always starts out in when you fire it up.

---

