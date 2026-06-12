---
title: "Folders and killall"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by jamez15 on 2005-10-10
Hey,

I've got two fairly simple questions:

1. What is the command for deleting a folder. I know rm is to delete files but it won't remove the folder itself.

2. Could someone briefly explain how to use the killall command successfully or point me to a informative tutorial. Certain programs spontaneously won't close and when I use the killall command the frozen prgram won't close.

3. Using the terminal, how do you delete a program? Because I don't want to use xine-ui and xmms anymore.

Thanks in advance,
James

---

### Post by Wolki on 2005-10-10
> **jamez15]
I've got two fairly simple questions: [/quote]

I count 3. Don't worry, you can get 3 answers for the price of two.  said:**
> 
1. What is the command for deleting a folder. I know rm is to delete files but it won't remove the folder itself.

rmdir <folder name>
It will only delete empty directories though.
"rm" will delete a folder and all of its contents if you pass it the -r option:
"rm -r <folder name>

> 
2. Could someone briefly explain how to use the killall command successfully or point me to a informative tutorial. Certain programs spontaneously won't close and when I use the killall command the frozen prgram won't close.

Usage is "killall <task name>". Sometimes the task name is not the same as the window or program name, in that case find the correct one using the system monitor or "ps" on the command line.
There is also the gnome force-quit panel applet and "xkill", both will give you a crosshair cursor, left-clicking a window then will kill it.

> 
3. Using the terminal, how do you delete a program? Because I don't want to use xine-ui and xmms anymore.

sudo apt-get remove <package name>

---

### Post by jamez15 on 2005-10-10
Thanks :)

---

### Post by SilentCacophony on 2005-10-10
Hello.

[QUOTE=jamez15]1. What is the command for deleting a folder. I know rm is to delete files but it won't remove the folder itself.[/QUOTE]

**rmdir** will delete an empty folder, while **rm -r <folder>** will delete a folder and all of it's contents, recursively (careful!) You can use **man rm** in a terminal to see a short guide to using it.

> 2. Could someone briefly explain how to use the killall command successfully or point me to a informative tutorial. Certain programs spontaneously won't close and when I use the killall command the frozen prgram won't close.

Similarly, you can use the **man <command>** for more info on any command, including killall. There is also **kill**. To kill a process, I like to use **top**, hit 'k', enter the process id, and select the default sigterm. You can also install htop, which is easier to deal with than top.

> 3. Using the terminal, how do you delete a program? Because I don't want to use xine-ui and xmms anymore.

For uninstalling, you'd want to use whatever package-manager you like. Looks as if you use the commandline, so aptitude would be a good choice if you want a text ui to browse packages. Or you could use:

**sudo apt-get remove <packagename>** from the console.

Here is a link to introduce shell usage: 

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

EDIT - Dang, I'm slow ;)

---

