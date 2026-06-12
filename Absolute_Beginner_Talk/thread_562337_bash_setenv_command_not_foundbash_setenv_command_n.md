---
title: "bash: setenv: command not found
bash: setenv: command not found"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by archeryguru2000 on 2007-09-28
ok, i've checked with most of the forum and only found "slightly" relevant info.  i hope i'm not reposting somebody elses question.  if so, please let me know.  anyway, when i start my command line terminal i'm immediately greeted with the following two lines of code.

bash: setenv: command not found
bash: setenv: command not found

i'm not sure if this is something i've done... or if i can even fix this, but i'm trying to install python (among other programs) and i am repeatedly beat down.  does anybody know how to remedy this?  any help would be greatly appreciated.  fyi, i'm using Edubuntu 6.06LTS.  thanks, in advance, for any/everything.

~~archery~~

---

### Post by ddrichardson on 2007-09-28
Check in .bash_profile and .bash_login. Looks like a bad attempt to set an environment variable.

---

### Post by dwhitney67 on 2007-09-28
> **archeryguru2000 said:**
> ok, i've checked with most of the forum and only found "slightly" relevant info.  i hope i'm not reposting somebody elses question.  if so, please let me know.  anyway, when i start my command line terminal i'm immediately greeted with the following two lines of code.

bash: setenv: command not found
bash: setenv: command not found

i'm not sure if this is something i've done... or if i can even fix this, but i'm trying to install python (among other programs) and i am repeatedly beat down.  does anybody know how to remedy this?  any help would be greatly appreciated.  fyi, i'm using Edubuntu 6.06LTS.  thanks, in advance, for any/everything.

~~archery~~

AFAIK, setenv is not part of the bash shell.  It is part of the csh, or tcsh.

The syntax for csh or tcsh is:

$ setenv *SOMEVAR* *somevalue*

The equivalent under bash is:

$ export *SOMEVAR*=*somevalue*

---

