---
title: "Using Alias?"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-25
Im using gedit to open the file .bash_profile in my home directory and then i add this line to the end of the file

alias l='ls -l'

Then i save and log off and on again.

But when i type l into the command line it returns: command not found

What am i doing wrong?

---

### Post by po0f on 2006-09-25
Try putting your aliases in ~/.bashrc instead.  Here are some of mine:
```
alias ls='ls --color=auto -hF'
alias ll='ls --color=auto -lhF'
alias la='ls --color=auto -lahF'
alias grep='grep --color=auto'
```

You don't have to logout for your alias to take effect if you are logged into X.  Just close the terminal(s) you have open and open up a new one.

---

### Post by Phurious on 2006-09-28
I am attempting to use aliases as well, but I am unable to edit the .bashrc file.  Let me qualify that; I can edit the .bashrc file, but I cannot save any of the changes made.  I also cannot change the permissions on the file because I am not the owner (root). :confused:

---

### Post by cajunlibra on 2006-10-27
I do not have a ~/.bashrc file.  I have a .bashrc file in my profile folder.  I added the commands to create the aliases but it didn't work.  I have almost 10 that I want to use and I'd like to be able to use them and not enter them constantly.

I have /etc/bash.bashrc file that mentions a profile folder.  i do not have a ~/etc/profile folder.

Thanks for the help

---

### Post by po0f on 2006-10-27
cajunlibra,

~ is just a shortcut for your user's home folder (/home/cajunlibra or whatever your login name is).  So ~/.bashrc is really /home/cajunlibra/.bashrc.  After making changes to that file, you will either have to close the terminal emulator you made the changes in, or just open a new one up if you made the changes in gedit.

[EDIT]
s/editor/emulator/

---

### Post by bodhi.zazen on 2006-10-27
Rather then logout and login:```
source .bashrc
```

---

### Post by cajunlibra on 2006-10-27
I've done that.  Doesn't work.

Does it make a difference that I'm using KDE?

---

### Post by bodhi.zazen on 2006-10-28
Try adding a file in you home directory .bash_profile

```
echo . $HOME/.bashrc >> ~/.bash_profile
```

Or, if you prefer:[list=number][*]open an editor (gedit).[*]put ". $HOME/.bashrc" (without quotes) on the first line.[*]Save the file as /home/your_user_name/.bash_profile[*]exit the editor.[/list]

Now open a terminal and try it out your alises.

---

