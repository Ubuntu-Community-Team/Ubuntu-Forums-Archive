---
title: "Setting environment Variables"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by infin?ty on 2007-04-09
Hi,

I am writing the following shell script to set up an environment variable, but its not working.

```

#!/bin/bash

export NAME=$NAME:def

```

the earlier value of name is abc so after the execution of this script it shud be abc:def

but this is not working,

i know i am makin a very basic mistake, but plzz help me out.

Thanks

---

### Post by quux on 2007-04-09
Hi,

Try
```
export NAME=${NAME}:def
```

---

### Post by infin?ty on 2007-04-09
no not working i tried this

i ran the script in bash

and after that typed echo $NAME
i am still gettin the same old variable it hasnt changed.

do i need to log off or sumthing??

---

### Post by quux on 2007-04-09
That's because your shell spawns a new process when executing the script. The "export" is executed in this new process and does not affect the enviroment of its parent process (i.e. the shell where you executed your script).

---

### Post by infin?ty on 2007-04-09
ok...i got that, but i want my variable to be available globally, something like the PATH
variable, which is available everywhere.

---

### Post by infin?ty on 2007-04-09
actually i want to change the PATH variable, and also set
variables like JAVA_HOME, DERBY_HOME etc, which will be
available globally to any process anytime.

---

### Post by quux on 2007-04-09
The correct place to put this info would be either the config of your shell or the config of your login manager. 

If you want to modify $NAME in your current shell, try executing your script via "source <scriptname>"

---

### Post by joshuapurcell on 2007-04-09
> **quux said:**
> That's because your shell spawns a new process when executing the script. The "export" is executed in this new process and does not affect the enviroment of its parent process (i.e. the shell where you executed your script).

This answer is correct. If you want new environment variables in your current environment, you must add these environment variables to a script that is set to be sourced at the beginning of each new environment created. A new shell environment is created whenever you open a terminal, and one of the best places I've found to add or modify environment variables is **/etc/bash.bashrc**. There are other scripts you can add environment variables to, but if you use multiple users or use terminals other than just gnome-terminal you may see that your new variables are there (unless using /etc/bash.bashrc)

---

### Post by Robynsveil on 2007-04-16
> **joshuapurcell said:**
> This answer is correct. If you want new environment variables in your current environment, you must add these environment variables to a script that is set to be sourced at the beginning of each new environment created. A new shell environment is created whenever you open a terminal, and one of the best places I've found to add or modify environment variables is **/etc/bash.bashrc**. There are other scripts you can add environment variables to, but if you use multiple users or use terminals other than just gnome-terminal you may see that your new variables are there (unless using /etc/bash.bashrc)

Hi... I'm a total newbie - to Ubuntu, that is. I want to program in Mono, and have set it all up (correctly, I think, installing all the different packages through Synaptic) and was able to do the hello-world thing in the MonoDevelop GUI. However, to *run* the hello.cs file, I'm meant to do a:
```
mcs hello.cs -pkg:gtk-sharpgdm.conf

```

This generated the following error:

>  Source file `Main.cs' could not be found
Compilation failed: 1 error(s), 0 warnings


...which I attribute to a PATH issue. I've had a look at the /etc/bash.bashrc file - the whole thing looks like a PERL script, which I'm not familiar with at all (there's a number of IF conditional statements towards the bottom - the rest appears to be more appearance, autocompletion and stuff like that) and I don't really want to muck with any of that... anyway, I simply cannot figure out where I would add a path statement.

Or, am I barking up the wrong tree? Is this something I should be doing in some conf file for MonoDevelop?

---

