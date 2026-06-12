---
title: "bash error?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by archeryguru2000 on 2007-09-28
ok, i've checked with most of the forum and only found "slightly" relevant info. i hope i'm not reposting somebody elses question. if so, please let me know. anyway, when i start my command line terminal i'm immediately greeted with the following two lines of code.

bash: setenv: command not found
bash: setenv: command not found

i'm not sure if this is something i've done... or if i can even fix this, but i'm trying to install python (among other programs) and i am repeatedly beat down. does anybody know how to remedy this? any help would be greatly appreciated. fyi, i'm using Edubuntu 6.06LTS. thanks, in advance, for any/everything.

~~archery~~

---

### Post by aJayRoo on 2007-09-28
I believe setenv is a command used in the c shell (csh) whereas you are using the bash shell. Bash won't recognise this command. It sounds like one of the files that bash sources for configuration whenever you load a shell contains two setenv commands. Either you have accidentally inserted these into you shell startup script (.bashrc or .bash_profile) or you have got a csh startup script in your home directory that bash is attempting to source. Looking at the bash manual page (type 'man bash' into a terminal) will explain which files do what. My suggestion would be to check the .bashrc and .bash_profile files (these are hidden files in your home directory by the way) to see if they contain a setenv command, if so then something unexpected has happened or you have made a mistake! Let us know how you get on.

---

