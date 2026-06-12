---
title: "vi and gedit don't work properly"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Kryben on 2006-12-30
Hi,

My vi text editor (command line) doesn't work properly in Ubuntu Edgy. I installed Edgy (for scratch, rather than overriding Kubuntu Dapper) a few days ago. I'm used to work with VI in terminal session for editing configuration files etc.
A few problems that occured:
- Insert-button replaces the letter left to the pointer into capital letters or small letters, rather than switching between INSERT and REPLACE mode.
- the arrow-buttons insert a new line and an A, B, C or D, but only when in replace and insert mode, not in command mode. Instead of moving the pointer.
- I cannot move the pointer after the last letter in every row/line.

For information: I have a translated version of ubuntu edgy (dutch) and use a Belgian keyboard setting. I have tested an English (International) keyboard setting, but that didn't help.

Anyhow, because Vi anoies me, I would start using Gedit. But that program won't startup at all.
"gedit textfile" throws an error like 'typ --help for more info'

Does anyone know how to fix those?

Thanks in advance

---

### Post by meng on 2006-12-30
I can solve the vi issue, start running vim (VI iMproved) rather than vi. Actually, I think vi was a symlink to vim under Dapper, so I can't understand the change.
Not sure what the matter is with gedit, works fine for me.

---

### Post by taurus on 2006-12-30
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by Kryben on 2006-12-31
wow thanks for the replies.

vi (vim) works fine now.

---

