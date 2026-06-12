---
title: "finding commands of installed softwares"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-07-30
how to launch a newly installed software when man <software name> gives no result

for example i installed wamerican dictionary and now i can't understand how to start it . i also tried  " dpkg -L wamerican-huge|grep /usr/share/dict"
 command and it returned following result

/usr/share/dict
/usr/share/dict/american-english-huge

then i entered

"american-english-huge "

it resulted 

"bash: american-english-huge: command not found"

---

### Post by Tomosaur on 2006-07-30
Try this in a terminal. It's somewhat crude but it should point you in the right direction:

```

ls /usr/bin/ | grep wamerican

```

If the command is indeed 'wamerican', that will be the output of the command. Failing that, just try this:

```

ls /usr/bin

```

and look through the results for a likely candidate.

Most programs will install to /usr/bin/ unless you specify somewhere different.

EDIT: On second thoughts, since in this case you've installed dictionary words, then all you'll have to do is just start your dictionary program. Ubuntu (Dapper Drake) comes with one installed already, under Applications > Accessories.

Alternatively, try typing 'gnome-dictionary' in a terminal.

---

### Post by Anduu on 2006-07-30
Here is what I do to find those pesky program names....

Assuming you installed thru Synaptic or a .deb file...fire up Synaptic and go to Settings>Preferences and check the first box labelled "Show package properties in the main window" and Apply.

Now when you highlight an installed package it will give you all kinds of details on it in the bottom/right pane...select the "Installed Files" tab.The executable command for the program will usually reside in /usr/bin or /usr/sbin.

---

### Post by u04f061 on 2006-07-30
> **Anduu said:**
> Here is what I do to find those pesky program names....

Assuming you installed thru Synaptic or a .deb file...fire up Synaptic and go to Settings>Preferences and check the first box labelled "Show package properties in the main window" and Apply.

Now when you highlight an installed package it will give you all kinds of details on it in the bottom/right pane...select the "Installed Files" tab.The executable command for the program will usually reside in /usr/bin or /usr/sbin.

but i don't install using synaptic. i use command line .
i also tried to to use synaptic but it failed perhaps because i am using proxy server and it is not configured for it

---

### Post by Anduu on 2006-07-30
Just a tip...rather than using sudo make install after ./configure and make at the command line use sudo checkinstall...it will generate a .deb file and install it that way thus letting you view/remove it thru synaptic.

---

### Post by 5-HT on 2006-07-30
The *which*, *whereis*, *find, *and* apropos* commands may be of some help for tracking down executables, installed files for a package, and man pages.

---

