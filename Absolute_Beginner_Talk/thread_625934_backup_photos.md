---
title: "backup photos"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-11-28
Is there a program or script where i can choose a folder and any time I make alterations to that folder it will make the alterations in another folder with the same stuff in it on my external HD? 

I mainly want this because when i put pictures in a folder i have several backups on my external HD and jump drive and i dont want to go to each folder and change the stuff...

---

### Post by Inxsible on 2007-11-28
you can create aliases for the rsync command and then simply run them.

for eg, I create an alias to backup my photos like so
```
alias rsyncpics = rsync -rvW /src /destination
```you can create multiple aliases and give them different destination paths depending on where you have your backup pictures. You can add additional flags to the alias depending on what you want to do. For further information on what flags can be used, type in ```
man rsync
```Then it's just a matter of typing the alias name in the terminal and hitting enter :D

Additionally, if you have more than 2 or 3 backups and you dont feel like typing 3 command, you can create another alias like```
alias backupAllPics = rsyncpics && rsyncpics1 && rsyncpics2
``` of course you need to use the alias names that you first created. Then simply run ```
backupAllPics
``` in the terminal

---

