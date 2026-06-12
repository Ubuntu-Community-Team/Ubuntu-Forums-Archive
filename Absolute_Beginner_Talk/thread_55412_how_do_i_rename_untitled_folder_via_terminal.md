---
title: "how do i rename untitled folder via terminal?"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by brian g on 2005-08-08
theres a folder in my home directory that is titled untitled folder and i believe it is preventing my home directory from being viewed via Nautilus
(I open home and the window freezes.. creating the folder was the alst thing i did before this started happening)

so i need to rename this folder to see if that is the problem.

i've tried the following..
```
brian@bertha:~$ rename untitled folder
Bareword "untitled" not allowed while "strict subs" in use at (eval 1) line 1.
brian@bertha:~$ rename untitled\ folder /newstuff
Can't locate object method "untitled" via package "folder" (perhaps you forgot to load "folder"?) at (eval 1) line 1.
brian@bertha:~$ rename untitledfolder newstuff
Bareword "untitledfolder" not allowed while "strict subs" in use at (eval 1) line 1.
brian@bertha:~$ rename un* blah
Can't locate object method "untitled" via package "folder" (perhaps you forgot to load "folder"?) at (eval 1) line 1.
brian@bertha:~$

```

---

### Post by xmastree on 2005-08-08
```
 mv untitled\ folder/ newname
```

---

### Post by brian g on 2005-08-08
[QUOTE=xmastree]```
 mv untitled\ folder/ newname
```[/QUOTE]
thank you.
so simple.. i guess i just paniced.

everything is back to normal.  :cool:

---

### Post by Sam on 2005-08-08
There is a space, so you have to escape it with a backslash.

---

### Post by xmastree on 2005-08-08
The easy way is to tyme mv un<TAB> and it automatically puts the correct syntax there for the name. Assuming there's only one...

---

### Post by brian g on 2005-08-08
[QUOTE=Sam]There is a space, so you have to escape it with a backslash.[/QUOTE]thanks.
I'm still new to so much of this terminal stuff.
[QUOTE=xmastree]The easy way is to type mv un<TAB> and it automatically puts the correct syntax there for the name. Assuming there's only one...[/QUOTE]excellent. i never even thought about tab-completion

---

### Post by xmastree on 2005-08-08
Glad you fixed it, although I can't help wondering why a folder called untitled folder would cause problems with nautilus. I just made a new folder on my desktop (to test that command...) and nautilus was fine.

---

### Post by dejvor on 2008-05-20
Hi...
might be related (at least I hope so). I've had the same problem with a folder. I accidentaly created an untitled folder and afterwards Nautilus wouldn't display the folder, it would just grey out and hang untill I forced it to quit. Could access the folder in the terminla no problem. So I deleted the untitled folder and Nautilus was working fine again untill I rebooted. After that the same problem, but there was no untitled folder anymore. Still cannot access the folder in nautilus. Any suggestions?
BTW: its an ext3 FS, no special data, just documents, fsck reports no problems

Any help would be much apriciated!
tNX

---

### Post by PmDematagoda on 2008-05-20
dejvor:- Please understand that you are replying to a thread that is about 3 years old, if you really do need to get help on this issue then please create a new thread in the new support sections instead of in the archive.

This thread is closed.

---

