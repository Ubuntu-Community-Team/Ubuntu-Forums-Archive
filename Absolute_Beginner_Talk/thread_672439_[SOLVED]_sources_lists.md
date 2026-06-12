---
title: "[SOLVED] sources lists"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by astathios on 2008-01-19
i am new user and i dont know much,
after a fresh install of 7.10 i was playing with synaptic manager ,
but i made a mistake and i install a package which was change my sources lists but this was from a previus version of ubuntu.thanx god it kept a backup of my previous list i use a code 
sudo gedit /etc/apt/sources.list
and i found my backup lists .
so my question is how can i make the backup lists enable again and to delete the new false?
thank you very much and excuse me for my bad english

---

### Post by jcwmoore on 2008-01-19
maybe i'm not understanding every thing correctly, but if you have a back up of you sources list, just open the back up in gedit, copy all the text, and then open you current sources.list and delete all the text in it and paste the copied text from the back up into your sources.list.

---

### Post by melopsittacus on 2008-01-19
Hi, Astathios! If you are really sure that the backup you had made is the right one, then you have to type the following commands in a terminal:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.OLD
sudo cp path/to/backupfile /etc/apt/sources.list
```

The first command creates a backup of the wrong list, the second one overwrites the wrong list with the backup you had made before.

I repeat though, you should do this only if you are absolutely sure, that your backup file has the right repo lists. I am not sure of that, because you mentioned that it was from a previous version of Ubuntu, and there are different repositories for different versions.

Should you want to restore the wrong list you started from, type:
```
sudo cp /etc/apt/sources.list.OLD /etc/apt/sources.list
```

---

### Post by forestpixie on 2008-01-19
first find name of backup in a terminal

ls /etc/apt/sourc*

then move the backup to replace the original

sudo mv nameofbackup /etc/apt/sources.list

Edit - if your not sure - post the output of the ls /etc/apt/sourc* command here - someone will help

---

### Post by astathios on 2008-01-19
ok
i think it solved .
you see the mistake lists was for feisty.
so i am sure for the back up lists as it says is for gutsy
thanks for all guys

---

### Post by Majorix on 2008-01-19
For the next time, if you want to enable a repo, do it via Synaptic or Software Sources. That way you can just remove the entry for it should you no longer need it.

---

