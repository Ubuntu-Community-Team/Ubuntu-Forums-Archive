---
title: "Frostwire shell script issue"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by RobsterUK on 2006-11-08
I can't get frostwire to run since installing U6.10

command line output is:
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

any ideas?

I tried reinstalling Frostwire in case the shell script had got changed somehow but no joy.

---

### Post by RobsterUK on 2006-11-08
bump

---

### Post by taurus on 2006-11-08
Look at line 44 of runFrost.sh to see if that's the case...

```
sudo nano +44 runFrost.sh
```

---

### Post by bsussman on 2006-11-08
> **taurus said:**
> Look at line 44 of runFrost.sh to see if that's the case...

```
sudo nano +44 runFrost.sh
```

If you intend to inspect something rather than change it, nano without the sudo is a much better idea.  Then you will not accidentally change something .

---

### Post by ThrobbingBrain66 on 2006-11-08
```
sudo gedit /usr/bin/frostwire
```
and change 'sh runFrost.sh' to 'bash runFrost.sh'

this will solve your problem

---

### Post by taurus on 2006-11-08
> **ThrobbingBrain66 said:**
> ```
sudo gedit /usr/bin/frostwire
```
and change 'sh runFrost.sh' to 'bash runFrost.sh'

this will solve your problem
Except you need to run it as root...

```
gksudo gedit /usr/bin/frostwire
```

---

### Post by bluenova on 2006-11-08
```
sudo gedit /usr/bin/frostwire
```
Does run it as root, it just asks for the password in the terminal, rather than gksudo which asks for the password graphically.

---

### Post by taurus on 2006-11-08
> **bluenova said:**
> ```
sudo gedit /usr/bin/frostwire
```
Does run it as root, it just asks for the password in the terminal, rather than gksudo which asks for the password graphically.
With gedit, it's a good idea to run it with gksudo instead of sudo...

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by bsussman on 2006-11-08
> **taurus said:**
> With gedit, it's a good idea to run it with gksudo instead of sudo...

Why?

if one is at the commandline, sudo is more convenient - it is less typing and avoids the extra step of using yet another separate window to actually type your password.

Except for the use of the extra window, as the following shows, gksudo, kdesu and sudo produce the same results with regard to the desired result which is to acquire root identity for the space of the command.

```
bos@Dillon:~$ sudo id
uid=0(root) gid=0(root) groups=0(root)
bos@Dillon:~$ gksudo id
uid=0(root) gid=0(root) groups=0(root)
bos@Dillon:~$ kdesu id
uid=0(root) gid=0(root) groups=0(root)
bos@Dillon:~$
```

---

### Post by RobsterUK on 2006-11-13
> **ThrobbingBrain66 said:**
> ```
sudo gedit /usr/bin/frostwire
```
and change 'sh runFrost.sh' to 'bash runFrost.sh'

this will solve your problem

I made this edit and nothing else, and it worked. So what's the issue here?

---

### Post by jeff1968 on 2006-11-13
Can you expand on this, I type in the code but where do I make the other change ........

Newbie Jeff

---

### Post by taurus on 2006-11-13
> **jeff1968 said:**
> Can you expand on this, I type in the code but where do I make the other change ........

Newbie Jeff
What other change?  Can you expand on that a little more?

---

