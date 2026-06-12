---
title: "ls color scheme"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by slikwill on 2007-10-15
In Terminal, what is the significance of the colors in the filenames in the ls command output?

---

### Post by kellemes on 2007-10-15
Every filetype may have it's own color, makes reading a little easier.
ls takes its colors from the environmental variable LS_COLORS.
The command *dircolors* will show the colorcodes for the filetypes.

---

### Post by erginemr on 2007-10-15
Color   File type 
blue     directories 
red       compressed archives 
white   text files 
pink     images 
cyan    links 
yellow devices 
green executables 
flashing red broken links

---

### Post by erginemr on 2007-10-15
By the way, it is the line:
alias ls='ls --color=auto'
in your .bashrc file in your home directory, that makes the colorization of the "ls" command. Alias is a way to shortcut a long command to a lesser form. Here, the command 'ls --color=auto' has been aliased (bound) to 'ls'.

If you edit this file and change the above line as:
alias ls='ls -F --color=auto'

then you will also have some handy symbols as suffixes to the names, which designate:

Character File type 
nothing regular file 
/ directory 
* executable file 
@ link 
= socket 
| named pipe

---

### Post by slikwill on 2007-10-15
Many thanks.

---

### Post by daniel6 on 2007-10-20
Any one have any idea where these environment variables come from when a terminal session is started? My old eyes would be happier with a couple of color changes.

---

### Post by bodhi.zazen on 2007-10-20
> **daniel6 said:**
> Any one have any idea where these environment variables come from when a terminal session is started? My old eyes would be happier with a couple of color changes.

[http://forums.macosxhints.com/showthread.php?t=46719](http://forums.macosxhints.com/showthread.php?t=46719)

---

### Post by crimesaucer on 2007-10-20
I like to change a few of the colors so that my files are "ubuntu orange" and my executable launchers are the "launcher blue".

Then I make my .tag.gz packages "brown" like the boxes, and the permission denied a "red and white".

I also turn the .mp3 and .png to the "green"  color of the music notes....


I find it helps me know what is what in the terminal.

---

### Post by erginemr on 2007-10-29
I would recommned you not to touch the original colors but rather get used to them, because those colors are somewhat standard among different Linux distributions. Therefore it will be difficult for you to get used to it when you start using another distro / version later on.

If you really like young at heart, then I would suggest you to follow the steps explained in the following web page:
[http://www.systhread.net/texts/200703bashish.php](http://www.systhread.net/texts/200703bashish.php)

---

### Post by nuir on 2007-10-30
It would be nice to have the --color=auto option by default... 

But what do I do if I have no .bashrc file in my home directory? Where else can I change **ls** options?

---

### Post by erginemr on 2007-10-31
> **nuir said:**
> It would be nice to have the --color=auto option by default... 

But what do I do if I have no .bashrc file in my home directory? Where else can I change **ls** options?

That is strange. You should have had a .bashrc in your home directory already. 

Anyway, system-wide bash settings are kept in "/etc/bash.bashrc" file. You can add the colorization with an "alias" command there as given above.

---

### Post by nuir on 2007-10-31
> **erginemr said:**
> That is strange. You should have had a .bashrc in your home directory already. 

Anyway, system-wide bash settings are kept in "/etc/bash.bashrc" file. You can add the colorization with an "alias" command there as given above.

Yeah... I thought it was strange too. Anyways, I just created it and it worked fine. This is may be a bug of some kind, because I'm using a fresh gutsy install. Well, I have my home directory in a separate partition, maybe some things from my previous installation clashed with the new one. At least nothing seems to be broken...

Thanks for the info on system-wide settings!

---

### Post by erginemr on 2007-11-01
You are welcome nuir.

Happy 'bunting...

---

