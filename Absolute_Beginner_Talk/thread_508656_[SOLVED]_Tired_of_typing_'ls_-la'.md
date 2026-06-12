---
title: "[SOLVED] Tired of typing 'ls -la'"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by threadhead on 2007-07-24
When I am in the terminal (usually remotely via ssh), I do a lot of directory listings (ala 'ls -la'), and I need to see all the files, in logn format. But I am tired to typing the whole 'ls -la'.

Is there a way I can set 'ls' so that it defaults to using the '-la' options?

Karl

---

### Post by saiz66 on 2007-07-24
Try this: 

alias ls='ls -la'

---

### Post by diggity on 2007-07-24
You can create an alias in your .bashrc file located in your home directory.

alias ls='ls -la'

Once you add the line, you will need to reload by typing: source .bashrc

---

### Post by threadhead on 2007-07-24
> **saiz66 said:**
> Try this: 

alias ls='ls -la'

Cool. But it does not 'stick' when I logout/login.

Also, can I just alias 'ls' instead of 'list'?

Thx!

---

### Post by Koybe on 2007-07-24
Open up your bashrc file :
```
sudo gedit /home/jerome/.bashrc
```

@ line 59, replace
```
alias ls='ls --color=auto'
```
with
```
alias ls='ls -la --color=auto'
```

Restart your terminal, it should do the trick.

---

### Post by asmoore82 on 2007-07-24
you are looking for aliases...

```
~ $ alias la='ls -la'
~ $ la

```

some nice aliases are already created but disabled, if you feel comfortable doing so, edit the file .bashrc in your home directory and uncomment the aliases you want to use or add your own :P

---

### Post by dca on 2007-07-24
alias ls="ls -la"

---

### Post by dca on 2007-07-24
...wait a minute, six of us were too late on that one...:)

---

### Post by threadhead on 2007-07-24
Beautiful! Thank you very much.

---

