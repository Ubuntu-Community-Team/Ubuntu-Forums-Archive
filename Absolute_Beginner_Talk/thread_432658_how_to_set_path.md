---
title: "how to set path?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-05-04
hello,

i've installed a new program, but need to add its directory to my $PATH.  is /etc/environment the right place to do this?  i've heard that doing it here affects all users systemwide, and that's not necessarily what i want to do.

thanks,

-steve

---

### Post by 5-HT on 2007-05-04
For just one user, you can put it in ~/.bash_profile
```
export PATH=$PATH:<NEW DIRECTORY TO ADD>
```

---

### Post by Skrynesaver on 2007-05-04
5-HT is correct, however there is one caveat, .bash_profile is only read for login shells, eg. logging in from a terminal (CTRL-ALT-F(1-6), CTRL-ALT-F7 is the graphical terminal) or sshing in to your machine, to have the PATH set in gnome-terminal (or xterm or konsole ...) put the PATH line above in your .bashrc.

---

### Post by talex on 2007-05-04
Just a bit of clarification (cause it drove me crazy), export PATH= does not work in csh or tcsh shells.  The construct is a little different:

set PATH= for those shells

Assuming you are using the .bash shell, but just wanted to be sure ... I use some software that is only supported in other shells.

---

