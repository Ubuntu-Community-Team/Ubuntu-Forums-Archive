---
title: "problems with fonts, openoffice and microsoft office under crossover"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-08-01
Hi all

it seems it is a pretty bad week for my computer.
My laptop turned off by itself as the battery finished during shutdown. After that I realized that I can't modify certain fonts in the interface. For example, in KMail I can't change the fonts of the mail folders. They remain far bigger than they are supposed to be. Anti-alisasing and everything else is fine. Just the size is screwed and I can't fix it through the GUI

Also starting today I have two problems:
OpenOffice's open and save commands do not work anymore and they freeze completely the system. From terminal you see nothing.

Also I am using Microsoft Office with Crossover and now it won't even open again

I know guys these are sort of weird problems but I would really appreciate if you could give me some counselling here... 
Of course I have no /home backup since I still have to learn how to do this darn backups in linux

Cheers

Cippa Lippa

---

### Post by Maxtorm on 2007-08-01
Not sure it will help with any of the OOo or CrossOver problems, but have you tried rebuilding your font cache?
```
sudo fc-cache -f -v
```

---

### Post by Cippa Lippa on 2007-08-01
it didn't solve the font problem :-( mmm... I might have to go through the font tuning procedure again... darn... I will let you guys know if reinstalling crossover and office makes a difference. Impressive how microsoft can be unstable even under Linux.

On a lighter note... it seems openoffice has started working again.

---

