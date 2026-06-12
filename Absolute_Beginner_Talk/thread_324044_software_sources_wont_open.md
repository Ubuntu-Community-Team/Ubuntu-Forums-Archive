---
title: "software sources wont open"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by question_chick on 2006-12-23
Hi there, I am a complete newbie to ubuntu. I have just installed edge and I was about to try to add a repository to my synaptic package manager.

This si where i strike my problem however, it wont let me in to either the software sources or synaptic. I know it should ask me for a password but it doesn't, i click on it and it does absolutly nothing.

I don't recall playing with anything that would break that, though I can't be 100% sure

any help would be much appreciated

---

### Post by Ecthelion on 2006-12-23
You could try this:
```
gksudo synaptic
```
If you get an error here that might give light on the problem

If the above didn't work, try this:
```
sudo synaptic
```

---

### Post by randiroo76073 on 2006-12-23
The file you want to add to is called :sources.lst, located at /etc/apt .  Open a terminal and type:
 Code:
sudo gedit /etc/apt/sources.list 
 Add your entry to bottom.  If still having problem with synaptic use the terminal to open: 
Code:
 sudo synaptic

---

### Post by question_chick on 2007-01-15
Ok thanks for the answer guys but unfortunatley anytime I type in sudo synaptic I get the following:

>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in etc/sudoers near line 0

I am more than a little confused by this. Any help would be gratefully appreciated

---

### Post by Ecthelion on 2007-01-15
> >>> sudoers file: syntax error, line 0 <<<
...
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in etc/sudoers near line 0

Does this error only occur when you do "sudo synaptic"? Or does it occur every time you use "sudo" ?

---

### Post by jordanmthomas on 2007-01-15
Also, post the output of 
```
cat /etc/sudoers
```
because it appears to be malformed

---

### Post by question_chick on 2007-01-15
Every time I use sudo,

this is a new install and I hadn't done a lot to it, I am guessing something is corrupt so I am going to try a fresh install.

Thanks for the help guys, no doubt I will be back with more questions ;)

---

