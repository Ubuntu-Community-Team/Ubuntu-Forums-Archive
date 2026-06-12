---
title: "[SOLVED] Crazy Terminal Prompt"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Robert Ashley on 2007-08-19
As a new Linux user, I have some questions about the terminal prompt.
I have read that the prompt can be changed by issuing the command "PS1=..."
while using the terminal (where ... is the desired type of prompt.
I tried this and it does work IF terminal is already in use.
There appears to be two files that initialize the prompt when terminal is started, ie. /etc/bash.bashrc and /etc/profile.
I have tried to change each of these two files, but without any change in the prompt.
If I do either a "testparm /etc/bash.bashrc" , or "testparm /etc/profile"
the response is a series of lines complaining about "Ignoring badly formed line ...". A small example follows:

Processing section "[-z "$PS1"]"
params.c:Parameter() - Ignoring badly formed line in configuration file: shopt -s checkwinsize
params.c:Parameter() - Ignoring badly formed line in configuration file: if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
Unknown parameter encountered: "debian_chroot"
Ignoring unknown parameter "debian_chroot"
params.c:Parameter() - Ignoring badly formed line in configuration file: fi
Unknown parameter encountered: "PS1"
Ignoring unknown parameter "PS1"

First question; Is "testparm" incompatible with the "bash.bashrc" and "profile" type of file?
I must be the first to confess that I am not experienced with Linux programming, but examining other setup files., I don't see any syntax problems here.

Second question; Is there another setup or default procedure that controls the initial prompt for terminal?
It seems that the two files, "bash.bashrc" and "profile" are ignored when starting terminal.

This is not a serious problem, but my personal choice would show a different prompt.

I will certainly appreciate any educational help anyone can send my way about this situation.

---

### Post by llamakc on 2007-08-19
If you want to edit the prompt for an individual user the file is in that user's home directory at ~/.bashrc (for starters).

---

### Post by nitro_n2o on 2007-08-19
so if you want to only change the prompt and customize your bash shell have a look at this 
[http://tldp.org/LDP/abs/html/sample-bashrc.html](http://tldp.org/LDP/abs/html/sample-bashrc.html) it's a sample .bashrc copy it to your directory and play with it as you wish... 
but if you want to change the shell itself to another shell... then you need to know which shell suites you! check this out [http://docs.rinet.ru/UNIXs/ch13.htm](http://docs.rinet.ru/UNIXs/ch13.htm) a comparison between unix shells... 
have fun

---

### Post by Robert Ashley on 2007-08-20
Many thanks for your response to my request for help, however neither of you answered my questions, I still don't know why "testparm" works the way it did; also why does editing the existing bash.bashrc and/or profile, NOT effect the prompt? 
These two files are apparently just ignored when starting terminal.
Thanks again.

---

### Post by schorsch on 2007-08-20
As far as I know the command "testparm" belongs to the samba package and cannot be used to check your environment ....
```
~$ dpkg -S /usr/bin/testparm
samba-common: /usr/bin/testparm
```

---

### Post by Robert Ashley on 2007-08-21
OK, Thanks very much for that information. I now have learned not to use "testparm" for anything else.

---

### Post by mcduck on 2007-08-21
> **Robert Ashley said:**
> also why does editing the existing bash.bashrc and/or profile, NOT effect the prompt? 
These two files are apparently just ignored when starting terminal.
Thanks again.

Because Bash will first look if you have a personal .bashrc in your home, and only if that doesn't exist it reads the system-wide setting files. And most likely you do have that file, so that's where Bash reads your settings.

Just make your changes in ~/.bashrc and it should work.

---

