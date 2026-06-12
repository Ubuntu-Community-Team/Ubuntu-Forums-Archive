---
title: "My commands are executing in console but I can not use them in .sh files?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-15
Hi
Thank you for reading my post
I have some commands like maven and asadmin (I defined alias in .bashrc file for these commands) which I can invoke them from any console window, but I made a .sh file and give all permission to it, when I execute the .sh file using a command like:
```

./runall.sh 

```

It returns errors like:

```

./runall.sh: line 1: asadmin: command not found
./runall.sh: line 2: maven: command not found

```

Is there anything that I am missing? some final tip?

Thanks

---

### Post by Joeb454 on 2008-04-15
try putting the aliases in a file called .bash_aliases in your home directory :)

---

### Post by Cypher on 2008-04-15
Did you add something like "#!/bin/sh" on the top of your "runall.sh" file? If so, that creates a new shell instance to execute those commands and that shell instance is not going to pull the aliases you might have defined in .bashrc or .bash_aliases. You'll have to define them explicitely in that shell program. Additionally, you'll note that your path might be truncated too..

---

### Post by legolas_w on 2008-04-15
> **Joeb454 said:**
> try putting the aliases in a file called .bash_aliases in your home directory :)

Thank you for reply.
It does not works yet.
I put some other commands in the shell file something like:

```


ls .
maven	
wc ./me.sh


```

And two other commands works fine but maven command does not works :-(
I have not seen any path key in the .bashrc file, should I add a path entry? Is it PATH or path?

Thanks.

---

### Post by lswest on 2008-04-15
you can define the aliases at the start of the script, and then it should work fine.

---

### Post by legolas_w on 2008-04-15
Hi
I define them as follow:

```

alias maven=/usr/bin/mvn
alias asadmin=/home/legolas/glassfish-v2ur1/bin/asadmin

ls .
maven	
wc ./me.sh

```


and it does not work yet, it return the same error.

Thanks.

---

### Post by The Cog on 2008-04-15
I would be inclined to put the full path in the script.
```
#!/bin/bash
ls .
/usr/bin/mvn
/home/legolas/glassfish-v2ur1/bin/asadmin

```

---

