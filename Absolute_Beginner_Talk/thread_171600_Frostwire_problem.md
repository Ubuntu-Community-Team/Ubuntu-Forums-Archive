---
title: "Frostwire problem"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Trocisp on 2006-05-07
When I try to run frostwire I get this error....
```
marc@laptop:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
```

Edit: Resolved, thank you Qrk.
[QUOTE=Qrk]I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

```
sudo apt-get install sysutils 
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```


It worked for me[/QUOTE]

---

### Post by Qrk on 2006-05-07
I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

```
sudo apt-get install sysutils 
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```


It worked for me

---

### Post by nelson2006 on 2006-05-07
[SIZE="3"]Do you have java installed?[/SIZE]

---

### Post by Trocisp on 2006-05-07
[QUOTE=nelson2006][SIZE="3"]Do you have java installed?[/SIZE][/QUOTE]
Yes.

Note:  FANTASTIC tip Qrk! Worked like a charm!

---

### Post by akiro.yamamoto on 2006-05-07
If you have correctly installed java, you can alien the .rpm Limewire and convert it to .deb and install it with :

sudo dpkg -i lime*.deb

---

### Post by nelson2006 on 2006-05-07
[SIZE="2"]Before running the first time you have to do a couple of steps:

sudo nano /usr/lib/frostwire/runFrost.sh

and then      Hit the following keys: 

CTRL+O
ALT+D
Enter
CTRL+X[/SIZE]

---

### Post by joshrobinson on 2006-05-07
yeah whoever packaged frostwire messed up and saved it as a windows format file instead of a linux format file.. pretty funny when you think about it. you would think the linux version would have been created on a linux computer and made right

---

### Post by Trocisp on 2006-05-07
[QUOTE=nelson2006][SIZE="2"]Before running the first time you have to do a couple of steps:

sudo nano /usr/lib/frostwire/runFrost.sh

and then      Hit the following keys: 

CTRL+O
ALT+D
Enter
CTRL+X[/SIZE][/QUOTE]I didn't need to do that.  I just followed Qrk's little guide, and it worked like a charm.

---

### Post by imdeemvp on 2006-05-08
[QUOTE=Qrk]I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

```
sudo apt-get install sysutils 
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```


It worked for me[/QUOTE]
This solved the issue for me after l install frostwire.  Some one has how to make it work but I did see this posted.  I found it somewhere else and worked

---

### Post by itazuki on 2006-05-30
Wow, thank you guys for talking about this. I'd never heard of Frostwire 'til I stumbled upon this thread a few minutes ago. I installed it on my AMD 64 system and it's working great! I've had so much trouble trying to get a P2P program installed on my system and now I can finally cross that off of my "To-Do List". Thanks a lot for this info. :)

---

