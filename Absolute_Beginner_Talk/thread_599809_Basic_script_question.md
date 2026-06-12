---
title: "Basic script question"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-11-01
Could someone tell me where I'm going wrong. I'm starting out trying to learn how to write scripts. I'm trying to get an alias working.

I've added the code:
[COLOR="Navy"]alias l='ls -l'[/COLOR]
to the end of the .bashrc file.

The script file is:
[COLOR="Navy"]
#!/bin/bash
# My first script

echo "Hello World!"

l[/COLOR]

When i run the script "Helllo World!" comes out fine but I get the message "command not found" for "l".

Where am i going wrong?

---

### Post by llamakc on 2007-11-01
When you edit the .bashrc file you either need to logout and in so it's reread or just run:

```


source ~/.bashrc


```

And try your test script again.

---

### Post by Padraig1 on 2007-11-01
thanks for the reply.

I've tried both you're suggestions but it's still giving me the same error. To clarify, it comes up as:

[COLOR="DarkSlateBlue"]padraig@padraig-laptop:~$ script1
Hello World!
/home/padraig/bin/script1: line 6: l: command not found
padraig@padraig-laptop:~$ [/COLOR]

---

### Post by llamakc on 2007-11-01
My bad. I never try to use aliases in scripts. Somebody else will have to illuminate you on that. 

I place stuff like that in ~/bin and it would be called something.sh and look like:

#!/bin/sh
ls -l

Then, if ~/bin is in your $PATH you can call it in any scripts you create.

---

### Post by nick_h on 2007-11-01
By default aliases are not expanded in shell scripts.

From the man page of bash:
> Aliases are not expanded when the shell is not interactive, unless the expand_aliases shell option is set using shopt.

---

