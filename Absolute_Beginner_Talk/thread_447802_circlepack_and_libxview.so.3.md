---
title: "circlepack and libxview.so.3"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by adil_mughal on 2007-05-18
Hi everyone,

I am trying to instal a programme called circlepack. However, one I run it I get the following error message

>circlepack: error while loading shared libraries: libxview.so.3: cannot open shared object file: >No such file or directory

Although I ran a search for libxview.so.3 and find it located at the following address

/usr/bin/libxview.so.3

Any idea what the solution is.

Thanks.

Adil

---

### Post by Najand on 2007-05-18
Use:
```

sudo apt-get install circlepack

```

---

### Post by adil_mughal on 2007-05-18
Yes I already used the synaptic manager to install circlepack. But I followed through with you suggestion to use 

sudo apt-get install circlepack

but upon trying to run the package it results in the same error message again

---

### Post by sessine on 2007-05-18
you need the xview libraries, try 

sudo aptitude install xviewg

---

### Post by adil_mughal on 2007-05-18
ok I did as you said and typed

sudo aptitude install xviewg

however I still get the same error message :-(

---

### Post by sessine on 2007-05-18
sorry, missed the bit in your first post showing it was already installed.

I had a similar problem when I tried to install the xview clients, turned out the be an environment variable issue.

Try adding
```
setenv LD_LIBRARY_PATH /usr/bin
```
to your .bashrc file and start a new shell.

---

### Post by adil_mughal on 2007-05-18
When I start a terminal I now get the message

bash: setenv: command not found

Sorry I really am a total beginner! Have I correctly modified the .bashrc file?

---

### Post by sessine on 2007-05-18
Sorry, my fault, the line I gave you was from my .cshrc file.  The bashrc should read
```
LD_LIBRARY_PATH=/usr/bin
export LD_LIBRARY_PATH
```

(I think thats right, I 'm working from memory atm)

---

### Post by Najand on 2007-05-18
Run this command in the terminal:
```

echo export LD_LIBRARY_PATH=/usr/bin >> ~/.bashrc

```
Then close the terminal, open a new one and try to open your application.

---

### Post by adil_mughal on 2007-05-18
That did it!!

Thank you very much :-)

Yours

Adil

---

