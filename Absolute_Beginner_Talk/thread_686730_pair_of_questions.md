---
title: "pair of questions"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by 2manydrugsago on 2008-02-03
whats the best way to make an iso image  from a cd. in ubuntu 7.10

and 
 since i have  an unsupported sound system on my mobo  i have to buy a sound card.. whats is one that will work with  ubuntu 7.10?

---

### Post by Dr Small on 2008-02-03
For question #1:
```
dd if=/dev/cdrom of=filename.iso
```

---

### Post by mmb1 on 2008-02-03
I use an SBLive! card that works flawlessly, but you may want something a bit more modern depending on your hardware configuration.

---

### Post by giftedwon on 2008-02-03
find a sound card that you like and then do a bit of a research on it and see if it compatible with  ubuntu.

---

### Post by 2manydrugsago on 2008-02-03
I couldn't get the iso command to work.

dd if=/dev/cdrom of=filename.iso

i changed  it to dd if=/dev/cdrom of=office07.iso
 and i get 
dd: opening `/dev/cdrom': No such file or directory

---

### Post by Abu_Dayya on 2008-02-03
try first
```
mount /cdrom 
```

---

### Post by 2manydrugsago on 2008-02-03
mount: special device /dev/hda does not exist
 how do I point it towards my cd rom?>

---

