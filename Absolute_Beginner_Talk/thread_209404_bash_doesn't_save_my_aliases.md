---
title: "bash doesn't save my aliases"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by smegmaster on 2006-07-05
When I set an alias, after I close the terminal, it disappears. Does anyone know how to fix that?

Thanks!

---

### Post by mlind on 2006-07-05
[QUOTE=smegmaster]When I set an alias, after I close the terminal, it disappears. Does anyone know how to fix that?

Thanks![/QUOTE]

Put your aliases on ~/.bashrc or on ~/.bash_aliases, so they will be available on
next terminal session.

---

### Post by passonno on 2006-07-05
That does not work for me anymore.

I have a seperate bash_aliases file, and it does not load at login.

Any ideas?

---

### Post by tonyr on 2006-07-05
**passonno**:  I thought you fixed this.  What hat happened after your last
post [here]("http://www.ubuntuforums.org/showthread.php?t=209007")?

---

### Post by mlind on 2006-07-05
[QUOTE=passonno]That does not work for me anymore.

I have a seperate bash_aliases file, and it does not load at login.

Any ideas?[/QUOTE]

on .bashrc, make sure that this part isn't commented out.
```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```

---

### Post by rccharles on 2006-07-05
[QUOTE=mlind]Put your aliases on ~/.bashrc or on ~/.bash_aliases, so they will be available on
next terminal session.[/QUOTE]
.profile_bash makes a call to .bashrc when you login.  Make sure .profile_bash calls .bashrc

.profile_bash is called when you login.
.bashrc is called direcly when you invoke bash subsequent to the login. When you type bash on the command line.

Robert

---

### Post by steve.horsley on 2006-07-05
I keep my aliases in ~/.bashrc, and I have had teh impression that after editing this file, gnome-terminal will not  show the changes - you need to log out and back in again.

---

### Post by mlind on 2006-07-05
[QUOTE=rccharles].profile_bash makes a call to .bashrc when you login.  Make sure .profile_bash calls .bashrc

.profile_bash is called when you login.
.bashrc is called direcly when you invoke bash subsequent to the login. When you type bash on the command line.

Robert[/QUOTE]

It's .bash_profile, and it's only invoked for interactive login shells. .bash_profile sources .bashrc as default. .bashrc is invoked for non-login shells.

---

