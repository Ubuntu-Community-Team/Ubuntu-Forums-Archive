---
title: "[SOLVED] Linux commands in terminal"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Adaminla on 2007-12-24
I am setting up a machine for my daughter and got this message. *run dpkg  --configure -a. I typed it into a terminal and got this message *command not found*. Did I leave something out? Do I need to type *run* in and if so where? At the beginning of the phrase or at the end? Also where can I find more info on Linux commands?

---

### Post by jeffus_il on 2007-12-24
The command is:
dpkg  --configure -a

* and run are not part of the command

---

### Post by SOULRiDER on 2007-12-24
You will have to add sudo for it to work
```
sudo dpkg --configure -a
```

---

### Post by overdrank on 2007-12-24
> **Adaminla said:**
> I am setting up a machine for my daughter and got this message. *run dpkg  --configure -a. I typed it into a terminal and got this message *command not found*. Did I leave something out? Do I need to type *run* in and if so where? At the beginning of the phrase or at the end? Also where can I find more info on Linux commands?

Hi and welcome, I believe the command would be ```
sudo dpkg --configure -a
```
And for Linux commands
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by kaiju on 2007-12-24
command not found should mean that you don't have the program you're trying to run.
as dpkg is a default for debian and hence ubuntu, this should not apply here.

in the terminal, after the prompt ($), you type the name of the program (dpkg) and the options you need ("--configure" and "-a" are two separate options).

also, you can get information about commands with "man *command*", in this case: "man dpkg", where you hit "/" to search in the manual page ("n" is used to get to the next result).

finally, are you sure you typed it right?
(also note that dpkg needs sudo for executing it with root rights: "sudo dpkg...")

---

### Post by jeffus_il on 2007-12-24
When you open a terminal window, you get a little program which interacts with you called a"shell", this guy gives you the "$" sign which you can type commands at, and then run by hitting enter.
The shell has its own built-in commands and can run anything that you have installed on the computer, if you type firefox and hit enter it will run the firefox browser, if you type ls , it will show you the files in you current directory. there are many many more commands ...

"dpkg" is part of a group of maintenance programs from the Debian distribution which Ubuntu is based on.

---

### Post by erginemr on 2007-12-25
> **Adaminla said:**
> I am setting up a machine for my daughter and got this message. *run dpkg  --configure -a. I typed it into a terminal and got this message *command not found*. Did I leave something out? Do I need to type *run* in and if so where? At the beginning of the phrase or at the end? Also where can I find more info on Linux commands?

To your second question, you can learn more about the powerful Linux command Line Interface (CLI) from the following tutorial site:

[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

---

