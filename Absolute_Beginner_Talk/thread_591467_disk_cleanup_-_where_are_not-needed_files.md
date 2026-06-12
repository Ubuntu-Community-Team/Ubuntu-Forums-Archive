---
title: "disk cleanup - where are not-needed files"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by broshe on 2007-10-25
I upgraded my Xubuntu to 7.10. it now seems to work fine.
However, I lost about 1.2 GByte of disk space.
How can I find non-needed files that were not cleaned after the installation ?
I already emptied the trash, but this does not help.
How can I free the lost disk space  ?

Thanks
Eli

---

### Post by dannyboy79 on 2007-10-25
sudo aptitude autoclean
and
sudo aptitude clean

will clean out unneeded files from your apt directory I am pretty sure. You can do man aptitude to be sure, read the clean and autoclean. Often times, there's much you can delete from the /var/log/ folder if you want. Isn't it also possible the xubuntu just grew in size compared to feisty xubuntu? I know 1.2gb seems like a lot but the old days of fitting linux within 1gb are gone. especially with all the gui driven apps and running X.

---

### Post by broshe on 2007-10-25
[QUOTE=dannyboy79;3631076]

sudo aptitude autoclean

Miraculously,  this freed 0.6 Gb.
Thanks !

Eli

---

### Post by Niniel on 2007-10-25
Why is so much space... spent on these files anyway? There's probably a reason, but what is it? For possible rollbacks?
If that's the case, how would I roll back something?

---

