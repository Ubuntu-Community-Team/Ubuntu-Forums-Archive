---
title: "Ok guys big problem...."
date: 2005-09-25
forum: Absolute Beginner Talk
---

### Post by josebalius on 2005-09-25
Everytime I try to open the root terminal I get this error:

Failed to run /usr/bin/x-terminal-emulator:
Child terminated with 1 status

Any ideas on how to fix it? thanks to anyone who helps me :)

---

### Post by Ampersand on 2005-09-25
Does a prompt come up beforehand asking for your password, and do other programs that require a password (like Synaptic) work?

A workaround for this is to open a terminal, then type "sudo bash"

---

### Post by parktownprawn on 2005-09-26
[QUOTE=josebalius]Everytime I try to open the root terminal I get this error:

Failed to run /usr/bin/x-terminal-emulator:
Child terminated with 1 status

Any ideas on how to fix it? thanks to anyone who helps me :)[/QUOTE]

what happens if you type
```
 ls -l /usr/bin/x-terminal-emulator 
```

---

### Post by josebalius on 2005-09-26
Hi, the prompt appears AFTER the password. However if I run the program likes for example:

sudo /usr/bin/users-admin/

It works perfectly, however if I click on it from the menu it doesn't work.

And if I type the command above I get:

lrwxrwxrwx  1 root root 37 2005-09-22 20:02 /usr/bin/x-terminal-emulator -> /etc/alternatives/x-terminal-emulator

Thanks for the help.....and please tell me there is a fix :(

---

### Post by parktownprawn on 2005-09-27
what happens if you type ```
  gksudo /usr/bin/x-terminal-emulator 
```

also what is the output of
 ```
  ls -l   /etc/alternatives/x-terminal-emulator
```
and
```
  ls -l   /usr/bin/gnome-terminal.wrapper 
```

what happens if you type ```
gnome-terminal.wrapper
```

----------------------------

as a workaround you can type ```
sudo -s
```
which will give you a root shell in the current terminal.

---

