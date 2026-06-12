---
title: "Bash Environment Question"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Hereford on 2006-02-03
**Ubuntu 5.10:**  The *.bash_profile* in my home directory contains this statement...

          # set PATH so it includes user's private bin if it exists
          if [ -d ~/bin ] ; then
             PATH=~/bin:"${PATH]"
          fi

...The bin directory exists but this statement is evidently not executed at login.  Is *bash_profile* even being executed?  (*.bashrc* is also present but I think is called from *bash_profile*.)  Must I locate the 'global' login script and add this statment there?  (Seems kind of unruly to me.)

Thanks.

---

### Post by kabus on 2006-02-03
~/.bash_profile is only read when bash is started as a login shell.
If you want to make sure that the if-statement is always executed when you start an interactive shell, put it in your ~/.bashrc.

More info on bash startup files here :

[http://www.network-theory.co.uk/docs/bashref/bashref_56.html](http://www.network-theory.co.uk/docs/bashref/bashref_56.html)

---

### Post by Hereford on 2006-02-03
Thanks kabus.  Thats the way it happens.  But the web page you referenced seems to agree with my original misconception about the order in which the various flavors of bash scripts are sought.  This is revealed deep in the bash man page once you know exactly what to look for.

"From Yoda learned grammer and syntax *nix programmers have." ;)

---

