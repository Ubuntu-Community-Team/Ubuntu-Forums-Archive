---
title: "[SOLVED] nothing works because of medibuntu.list"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by 2jack3jack on 2008-02-22
Ok here is the problem i was playing around and i added some source to ubuntu now every time i put a sudo or open sypatic it wont work because of medibuntu so i go to delete that list and i come to find out that i have two sources list so i try to delete  my second one sources list d and it says i do not have permision to delete

---

### Post by angry_johnnie on 2008-02-22
you can't delete it because you need root privileges.  Anyway, I'd say don't erase it unless you're absolutely sure.  Just move it somewhere else instead.
open a terminal and type:

sudo mv /path/to/file    /new/path/to/file

that'll do it.

---

### Post by forestpixie on 2008-02-22
alternatively - what errors do you get and we could help to sort the list so it works for you, medibuntu is good for things they can't put on ubuntu

do an update and see what the errors are

sudo apt-get update

---

### Post by 2jack3jack on 2008-02-22
sorry for the bother

---

### Post by 2jack3jack on 2008-02-22
> **forestpixie said:**
> alternatively - what errors do you get and we could help to sort the list so it works for you, medibuntu is good for things they can't put on ubuntu

do an update and see what the errors are

sudo apt-get update

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
heres wahat its says
__________________

---

### Post by forestpixie on 2008-02-22
ok easily sorted - we can rename the file and then redo the medibuntu addition, do these in a terminal

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.bak
```

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

I have assumed that you are still using feisty, as shown in your panel

that should move the old list and get you a new one, if you get problems post back

---

### Post by Anicka on 2008-02-22
Could you post the file?```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by forestpixie on 2008-02-22
it'll be full of rubbish - seen it before, many many times ](*,)

---

### Post by 2jack3jack on 2008-02-22
thank you so much im so glade now that i switch to linux and mac :lolflag:

---

### Post by forestpixie on 2008-02-22
cracking - can you mark thread as solved

and I just seen the 'sorry for the bother' post - it isn't a bother, if I wasn't helping you I'd be doing coursework, you'd think at 40 I'd have got past the any excuse thing :D

---

### Post by 2jack3jack on 2008-02-22
thank you so much im so glade now that i switch to linux and mac :lolflag:

---

