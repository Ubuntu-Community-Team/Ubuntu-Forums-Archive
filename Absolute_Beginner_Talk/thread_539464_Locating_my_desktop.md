---
title: "Locating my desktop"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-08-31
Hi group,
I downloaded a copy of Opera....it's sitting on my desktop.

Now, I thought I hed to open terminal and tell terminal to locate my desktop file by doing this.

cd ~/desktop


Then I'd be able to put in the code to install the software.....complicated because I've got an AMD64.

Sadly, cd ~/desktop

now says 
bash: cd: /home/philip/desktop: No such file or directory

I know what I'd like to bash.

All the best,
Phil

---

### Post by benhall on 2007-08-31
Try "Desktop" with an uppercase "D"

---

### Post by tszanon on 2007-08-31
GNU/Linux, unlike Windows and DOS, is case-sensitive. Since the name of the folder is Desktop, then you must use:
```
cd ~/Desktop
```
Hope it helps.

---

