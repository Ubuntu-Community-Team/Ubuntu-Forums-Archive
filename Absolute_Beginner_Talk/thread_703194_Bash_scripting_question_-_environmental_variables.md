---
title: "Bash scripting question - environmental variables"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by jambalaya on 2008-02-21
Hi. I wrote a script but it doesn't work. After examination, it looks like some of the variables aren't set within the script. Plsease se the code and the output:
```

#!/bin/bash
echo '$PS1='$PS1

```
the output is:
```
$PS1=
```
which means PS1 is not set within the script. Why is that? I thought all variables are inherited by child processes. Maybe I shoould use some switch in the #!/bin/bash line?

Thanks.

---

### Post by jasonkb on 2008-02-21
hmm something doesn't sound quite right here.  The code you have written

echo $PS1 

will only give you a value if $PS1 actually holding anything.  Unless $PS1 is set as a global environment variable, then you will need to set it manually in the script ie.
$PS1 = 3
echo $PS1

Hope this helps.

Jason Barraclough.

---

### Post by ruy_lopez on 2008-02-21
PS1 is not set using export. See: '/etc/profile'. It means the process environment which runs the bash script doesn't inherit the variable.

---

### Post by Kasyx on 2008-02-21
When defining the variable you wouldn't use the "$" sign, you only put that before the variable when you call it.

so:

PS1 = 3

if [ $ps3 -gt 0 ]

etc.

---

### Post by jambalaya on 2008-02-21
Hi.

I added 'export PS1' in /etc/profile, tried the same in ~/.bashrc, but is still doesn't see this variable inside my script :-(

Thanks.

---

### Post by jasonkb on 2008-02-23
Whoops! Apologies for the typo... you are quite right!

---

