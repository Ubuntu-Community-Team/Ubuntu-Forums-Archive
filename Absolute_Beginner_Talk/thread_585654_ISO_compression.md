---
title: "ISO compression"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2007-10-21
I need a good app take can compress iso to cso. I have have tried ciso which I found in synaptic but cant figure how to run the app. Can some point me in the right direction?

---

### Post by Paul820 on 2007-10-21
From the terminal:
> man ciso

---

### Post by phelixnyc on 2007-10-21
I read the small manual yet cant figure out the command prompts.

---

### Post by Paul820 on 2007-10-21
Well the manual says
> ciso level infile outfile
level: 1-9 compress ISO to CSO (1=fast/large - 9=small/slow

So you put:
> ciso ** level** nameOfFile.iso newNameOfFile.cso

Where it says **level** input the level of compression you want. Experiment with it.

---

### Post by phelixnyc on 2007-10-21
I tried the commands and got this
Compressed ISO9660 converter Ver.1.01 by BOOSTER
Usage: ciso level infile outfile
  level: 1-9 compress ISO to CSO (1=fast/large - 9=small/slow
         0   decompress CSO to ISO

---

### Post by xmoby on 2007-11-02
You have to enter all the options. As an example, if I want to compress Original.iso to NewOne.cso, using the best compression, I'd have to enter.

```
ciso 9 Original.iso NewOne.cso
```

Then, just wait until the prompt comes back. When it does, the compression should be finished (except if there's any error message).

---

### Post by WadiJM on 2008-02-01
I have a cso and I'm trying to decompress it to iso but it throws "cant allocate memory error"...I have 4 gb of ram...what i'mdoing wrong?
Thanks
Wadi

---

