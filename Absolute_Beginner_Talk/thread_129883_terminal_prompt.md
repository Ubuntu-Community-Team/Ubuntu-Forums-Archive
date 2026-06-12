---
title: "terminal prompt"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by lmellen on 2006-02-14
:confused: Simple question -- Does anybody know how to shorten or change  the prompt in terminal. I have my user name with about 16 numbers and letters following it. ---- Thanks --Larry

---

### Post by rfruth on 2006-02-14
There is a help (F1) selection in my GNOME Terminal 2.1 (BASH), not sure what file you need to edit to make a permanent change ...

---

### Post by cwaldbieser on 2006-02-14
[QUOTE=lmellen]:confused: Simple question -- Does anybody know how to shorten or change  the prompt in terminal. I have my user name with about 16 numbers and letters following it. ---- Thanks --Larry[/QUOTE]
The $PS1 shell variable holds your primary prompt.  $PS2 is you secondary.

By defaut
```

$ echo $PS1
${debian_chroot:+($debian_chroot)}\u@\h \w \$

```
\u = user name
\h = host name
\w = working directory

To change it
```

$ export PS1=\$

```
put the change in your ~/.bashrc to make it happen for every shell.

---

### Post by lmellen on 2006-02-15
:confused: cwaldbieser -- This is my prompt: lmellen@cpe-72-225-7-234~$. If I go into .bashrc and change h to ubuntu I then get: lmellen@lmellenbuntu ~$. 
I changed   "${debian_chroot:+($debian_chroot)}\u@\h \w \$" to:
"${debian_chroot:+($debian_chroot)}\u@\ubuntu \w \$"
How do you change the value of h??
Export only changes the prompt for one session.
Thanks for the reply -- Larry

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=lmellen]:confused: cwaldbieser -- This is my prompt: lmellen@cpe-72-225-7-234~$. If I go into .bashrc and change h to ubuntu I then get: lmellen@lmellenbuntu ~$. 
I changed   "${debian_chroot:+($debian_chroot)}\u@\h \w \$" to:
"${debian_chroot:+($debian_chroot)}\u@\ubuntu \w \$"
How do you change the value of h??
Export only changes the prompt for one session.
Thanks for the reply -- Larry[/QUOTE]
The backslash (\) should only be used for the special symbols (e.g. \u \h \w).  So you probably want:
```

${debian_chroot:+($debian_chroot)}\u@ubuntu \w \$

```
Did you put the statement in your ~/.bashrc?  If you do, that variable will get exported for every session.

---

