---
title: "some commands could not be found"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by cobweb on 2006-02-25
hi,

when i try to execute some commands from a terminal, i get "command not found" error! how do i get all the essential commands? apt-get install does not work for that. and i really do not have some very common commands, such as fork or exec.

thanks for any help.

---

### Post by xhie on 2006-02-25
what commands in particular?

---

### Post by Xian on 2006-02-25
Place 'sudo' in front of the command....?
What are the commands???

---

### Post by cobweb on 2006-02-25
[QUOTE=Xian]Place 'sudo' in front of the command. Example:

$ sudo apt-get install <packagename>[/QUOTE]

thanks but i am already in the root mode,

and the commands in particular are fork, exec, or such very common commands, you know...

---

### Post by bluevoodoo1 on 2006-02-25
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

All have info about terminal commands. What error messages are you getting exactly? The 'apt-get install' command you mentioned should be preceded by sudo like "sudo apt-get install nameofapplicationyouwanttoget"

you can also type 
```

man gedit 
``` (gedit for example) for help. Type q to quit.

or

```

gedit --help
```

or
```

help
``` for some other commands (exec is in there).

---

### Post by Xian on 2006-02-25
[QUOTE=cobweb]and the commands in particular are fork, exec, or such very common commands, you know...[/QUOTE]

In a terminal?? Why not just execute the script that has those commands?

---

### Post by cobweb on 2006-02-25
i am telling again that i am already in the root mode and i know how to use apt-get command, thanks for the very useful help by saying type sudo apt-get install xxx!!!!!

the error i get is that command not found when i type man fork for instance, or could not find package fork when i type apt-get install fork .. 

this is the problem i have, other than that i know how to call commands from the shell!

---

### Post by xhie on 2006-02-25
#include <sys/types.h> 
#include <unistd.h>

---

### Post by cobweb on 2006-02-25
[QUOTE=xhie]#include <sys/types.h> 
#include <unistd.h>[/QUOTE]
how am i supposed to include these files while trying to execute a command from the terminal??? 

ok, i think i am in the wrong place..

---

### Post by heimo on 2006-02-25
```
sudo apt-get install manpages-dev
man fork
man exec

```

---

### Post by cobweb on 2006-02-25
[QUOTE=heimo]```
sudo apt-get install manpages-dev
man fork
man exec

```[/QUOTE]
that is great, thanks for the help heimo.

---

### Post by Gustav on 2006-02-25
EDIT: nevermind

---

