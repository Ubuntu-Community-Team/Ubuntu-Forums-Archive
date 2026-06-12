---
title: "new user installing new packages -- how to run the programs?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by qiepenguin on 2008-02-29
I recently set up my fiancee with Gutsy, and she likes it a lot.  She ran into some trouble with installing new software though.

She opened synaptic, and found a couple game packages she wanted to add: ace-of-penguins and 3dchess.  The installation went smoothly, but then "where are my programs?"  They didn't get added to the applications menu, the launcher, or the desktop (none of which is surprising, but it would be nice for her if it did).  Running the probable titles from the terminal didn't help either:

> 
tara@mittens:~$ 3dchess
bash: 3dchess: command not found
tara@mittens:~$ ace-of-penguins
bash: ace-of-penguins: command not found
tara@mittens:~$ man ace-of-penguins
No manual entry for ace-of-penguins


I went and found out in /usr/share/menu/3dchess that the command is "3Dc" and in /usr/share/menu/ace-of-penguins that ace-of-penguins has a suite of commands like "ace_solitaire", which is fine for me, but she is not interested in having to search around for things in the terminal.

Does anyone know of packages or configurations that can make launching newly installed programs more straightforward for gui-oriented new users?

---

### Post by hyper_ch on 2008-02-29
if those are gui programs then they should be auto-linked in your start/programs menu.

---

### Post by neurostu on 2008-02-29
hyper_ch: So i just installed 3dChess via apt-get and it didn't install itself into the GUI, although the program does run a GUI.  

I am not aware of any packages that do what you ask... however you didn't have that hard of time finding them so maybe everytime she installs a package that doesn't great a link in the Application menu you can just create one for her. Or better yet talk her through it so she can learn to do it herself.

The truth is, the command line isn't hard to use, its just intimidating, spend some time with here going over the CLI and how to use it and she will learn how to use it in now time

---

### Post by Oldsoldier2003 on 2008-02-29
> **neurostu said:**
> hyper_ch: So i just installed 3dChess via apt-get and it didn't install itself into the GUI, although the program does run a GUI.  

I am not aware of any packages that do what you ask... however you didn't have that hard of time finding them so maybe everytime she installs a package that doesn't great a link in the Application menu you can just create one for her. Or better yet talk her through it so she can learn to do it herself.

The truth is, the command line isn't hard to use, its just intimidating, spend some time with here going over the CLI and how to use it and she will learn how to use it in now time
I agree! yes it's nice to use the GUI, but the command line is a powerful tool and let's face it... In its current state the GUI just doesn't cut it. There are too many things that simply have to be done by CLI so why not ease people into its usage?

---

### Post by jan quark on 2008-02-29
to run the 3dchess type into the terminal

```

3Dc
```

the installed games should be located in

/usr/games

---

