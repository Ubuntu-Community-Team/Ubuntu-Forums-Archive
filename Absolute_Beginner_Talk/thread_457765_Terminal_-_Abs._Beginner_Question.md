---
title: "Terminal - Abs. Beginner Question"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2007-05-29
Hi Ubuntu users

I guess this has been asked before but..., ok I want the terminal to open in a certain size window (basically I feel it is too small) . So every time I open it, I have to resize it before typing anything and also, it opens with

my-login-id@my-login-id-desktop:~$ 

and takes up a lot of space in the terminal line, I don't want that. 

How can I configure so that it open with a specific size and with the prompt

Desktop:~$ (or something else I want).

Thanks
Ayesha

---

### Post by Inxsible on 2007-05-29
You can have your computer name changed. That way you can remove your "-desktop" which might give you some space
To do that go to 
System -- >Administration --> Network

Click on the General Tab and simply change the computer name to anything you like. 

For eg. Ayesha
You can't lose your login id on it...so it will still be ayesha@Ayesha

I think there is also a way to make sure that the window opens maximized..but i dont recall now :(

But you can try re-sizing it ...and i think it will keep the new size the next time around !!

---

### Post by Ek0nomik on 2007-05-29
You want to look into editing your .bashrc file regarding the line length at terminal.

Regarding a constant terminal window size... I always thought it kept the same window size after you have used it for awhile at a certain size, but I could definitely be wrong, I guess maybe I didn't pay attention.

---

### Post by Limitlesschannels on 2007-05-29
well, per prompt ( i mean, i don't know if this saves for reopening it or not)  but you can use the PS1 variable.

the PS1 variable defines your bash prompt and oyu can modify that, just remember to save your original first.

```

[limitlesschannels@MyComputer]$ SAVE=$PS1
[limitlesschannels@MyComputer]$

```

now when you change it, you set PS1:
```

[limitlesschannels@MyComputer]$ PS1=happy$
happy$ ls
happy$ someothercommand

```
 and to reset:
```

happy$ PS1=$SAVE
[limitlesschannels@MyComputer]$ ls
[limitlesschannels@MyComputer]$

```


for more info:
 [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x157.html](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x157.html)


EDIT:
yeah, it is a current session only fix.
For a permanent fix, i think you can just edit your .bashrc file, like Ek0nomik said.
mine was /etc/bash.bashrc so:
```

limitlesschannels@MyComputer:~$ sudo gedit /etc/bash.bashrc

```
in there is the prompt and current window size, that link i posted above should give you all the info if you search through some of the pages.

---

### Post by sirlancelot on 2007-05-29
Thanks for this! I noticed that many *nix systems have different prompts and was curious if there was a way to customize it. Now I know!

```
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\n\[\033[00m\]\$ '
```

A color prompt for color terminals :)

Thanks again!

---

