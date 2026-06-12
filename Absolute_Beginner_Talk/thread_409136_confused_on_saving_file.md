---
title: "confused on saving file"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by nixgod on 2007-04-14
hello, 

 I am trying to edit and save my sshd_config file. I am in it thru the terminal and made the changes that i want. How to i save the file. 

Thanks

---

### Post by mhansen on 2007-04-14
which editor are you using?

---

### Post by nixgod on 2007-04-14
i am not sure i just used the vi /etc/ssh/sshd_config command from the terminal. it looks just like the terminal window

---

### Post by Maestro23 on 2007-04-14
> **nixgod said:**
> i am not sure i just used the vi /etc/ssh/sshd_config command from the terminal. it looks just like the terminal window

Vi can be a pain for a new user.  Try gedit or nano.

> gksudo gedit filename

or 

sudo nano filename

*Must use sudo in front of your command because the files you are trying to edit are owned by root "/".

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nixgod on 2007-04-14
thanks alot that helped.

---

### Post by BaffledMollusc on 2007-04-14
vi is a pretty horrible editor to use unless you've spent a lot of time getting used to it. Anyway, to save you have to know that it has two modes - a command mode and an editing mode. To switch into the command mode, where you can save, you have to press ESCAPE. 

Then, press ":wq" without the quotes, and then press ENTER, which means get ready for a command ( : ), write the file (w) and then quit (q).

However, if you try this you'll probably get a message saying you don't have permission to write the file, since you're in the /etc directory, and not your home directory. If this happens, you have to start vi with extra permissions, i.e. type

sudo vi /etc/ssh/sshd_config

"sudo" is something you type before a command if you want to execute that command with administrator privileges. 

Finally, in future, unless you're masochistic (or want more geek cred), I'd recommend using a more friendly text editor like gedit. To do the same as above, you'd type

gksudo gedit /etc/ssh/sshd_config

to get into the gedit editor with that file. "gksudo" is the version of sudo for programs with a graphical interface rather than the terminal.

---

