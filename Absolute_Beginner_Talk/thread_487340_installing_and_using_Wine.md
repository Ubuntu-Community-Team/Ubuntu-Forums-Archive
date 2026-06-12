---
title: "installing and using Wine"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Nyxess on 2007-06-28
i want to play world of warcraft on ubuntu 6.06 and im told i should use a program called Wine to do it. I made my way to [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and followed the instruction where it told me to add the WineHQ APT Repository by doing this:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Dapper (6.06): *64-bit packages not available*
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

i ended just typing "sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list" and it worked. from there i opened Synaptic Package Manager and did a search for "Wine" and installed all the files that came up.

my problem is this: the only program i can find that has to do with Wine is Winefish LaText Editor

what did i do wrong, or is that the actuall program i use?

also, further steps to get world of warcraft up and running would be great

---

### Post by speaker219 on 2007-06-28
have you tried running "wine" from terminal?

---

### Post by Nyxess on 2007-06-29
in terminal(is it just"terminal" or "the terminal"?)i typed "wine" and it came up with 
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
so i typed

wine PROGRAM

and i got this

wine: could not load L"c:\\windows\\system32\\PROGRAM.exe": Module not found

???

---

### Post by kakalaky on 2007-06-29
you need to replace PROGRAM with the name of the windows .exe you want to run.

---

