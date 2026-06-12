---
title: "Software problem"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by anksi4u on 2008-02-20
i am using ubuntu 7.10 32 bit version on my 64 bit amd athlon machine..
i cant download vlc player because is says that my architecture is not supported..
so will shifting to 64-bit ubuntu solve my problem

---

### Post by Crooksey on 2008-02-20
```

$ sudo apt-get install vlc
```

Does that work?

---

### Post by anksi4u on 2008-02-20
no that doesnt work...it gets stuck at [99%]....connecting to ftp.videolan.org

---

### Post by oedha on 2008-02-20
what if you change the repo server ?

---

### Post by bharadwaj on 2008-02-20
not sure if the problem is with the environment but certainly yes it may fix your problem...

---

### Post by anksi4u on 2008-02-20
what is repo server??

---

### Post by oedha on 2008-02-20
go to system - administration - software source
you can choose repository server there......
previously you said -- ftp.videolan.org
after choosing the repo server...close it...click reload
try sudo apt-get install vlc again from terminal

---

