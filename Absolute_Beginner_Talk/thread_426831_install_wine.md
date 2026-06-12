---
title: "install wine?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-04-28
how do i install wine on an amd64, while i understand there are instructions for this on the website, i do not understand them, for i am a noob....damn me

---

### Post by Happy_Man on 2007-04-28
Ok, first you need to open up Synaptic and enable the Universe repos. After you've done that, put the following code into a terminal:
```
sudo apt-get install ia32-libs lib32asound2
```

Once, you've done that, download the .deb from [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Done? Okay, good. 

Then open up a terminal and input the following code ONE LINE AT A TIME:
```
cd Desktop
sudo dpkg --force-architecture -i wine_0.9.36~winehq0~ubuntu~*insert ubuntu version here*-1_i386
```

and you should be good! 
**NOTE** To get to the terminal, go to Applications --> Accessories --> Terminal

---

### Post by thelegionnaire on 2007-04-29
what do i put in enter version here? 7.04? that doesnt work

---

### Post by Happy_Man on 2007-04-29
What error does it give?

---

### Post by thelegionnaire on 2007-04-29
m@m-laptop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.36~winehq0~ubuntu~7.04-1_i386
dpkg: error processing wine_0.9.36~winehq0~ubuntu~7.04-1_i386 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine_0.9.36~winehq0~ubuntu~7.04-1_i386

---

### Post by thelegionnaire on 2007-04-30
i'd really like to install wine....please help me out homeys

---

### Post by thelegionnaire on 2007-05-01
can anybody just tell me what to write there?

---

### Post by zvacet on 2007-05-01
Just copy/paste what you find here

[http://wiki.winehq.org/UbuntuAMD64]("http://wiki.winehq.org/UbuntuAMD64")

and instead of wine_*_i386.deb  put the name of version you downloaded.It is seems to be wine_0.9.36 but I don´t know wich version you downloaded.

---

