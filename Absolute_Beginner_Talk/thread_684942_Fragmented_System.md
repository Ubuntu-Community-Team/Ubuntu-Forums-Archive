---
title: "Fragmented System?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Aoud on 2008-02-01
Hi, I just upgraded my Windows to Ubuntu/Kubuntu and was wondering what happens when I start to delete large files here and there. Is there some tool I can use to unfragment my drive?

Thanks.

---

### Post by misfitpierce on 2008-02-01
linux file systems maintain themselves and dont require defragmenting tools like windows.

---

### Post by jan quark on 2008-02-01
please be very cautious with deleting anything 

be sure you know what are doing and ask the forum before removing some files with which  you have this feeling they might be important

to remove safely use either the synaptic package manager

or these terminal commands

for packages  got from synaptic,  use

```
sudo apt-get remove --purge packagename
```

for downloaded packages   use 

```
sudo dpkg -r packagename
```

---

### Post by PinkFloyd102489 on 2008-02-01
Unless you have a ReiserFS filesystem mounted with the notail option. Those tend to fragment just a bit but can be fixed by running a reiserfsck in a LiveCD.

---

### Post by bodhi.zazen on 2008-02-01
The classic link :

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

If you are asking about defragmenting your NTFS partiton from Linux, I would use the Windows tools.

---

