---
title: "terminal does not read ubuntu cd to install packages"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2008-03-29
the terminall for the past 2-3 days does not read my ubuntu cd to install packages...

when i make ```
sudo apt-get install postfix
``` for insance everything gos well untill the time that terminal ask me to put the cd and press enter...

i put the cd press enter but it does not read it...i tried 4 cds but nothing..while in the desktop it shows the cd..so its not a cd  or the cdplayer problem..



any thoughts??

---

### Post by wormser on 2008-03-29
> **psychobeauty said:**
>  ```
sudo apt-get it postfix
```

I have never seen apt-get it.  Have you tried apt-get install?  Are you sure the command is right or is this something I was unaware of?  Educate me if it is the latter.  Either way, you should check System> Administration> Software Sources and make sure the CD-rom is checked.  Why are you installing off a CD.  Does this computer have internet access?

---

### Post by TeoBigusGeekus on 2008-03-29
As a first measure, go to System->Administration->Software Sources 
Ubuntu Software tab and uncheck the Ubuntu cd. This way everything will be downloaded from the internet (I hope you have a connection, don't you?).
Now, insert a data cd or a music cd. Is Ubuntu still not recognizing it?

---

### Post by psychobeauty on 2008-03-29
ok i will uncheck cd resource...

no it always read cds..the error is on terminal i think

---

### Post by TeoBigusGeekus on 2008-03-29
Don't use the terminal for this specific application. Go to synaptic package manager and install it from there.

---

