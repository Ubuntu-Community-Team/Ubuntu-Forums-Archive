---
title: "Trouble with synaptic package manager"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by neoanduel on 2007-06-02
When trying to install wine ( i have dapper drake)  i got this error. now i cant download anything. its very frustrating. i hardly know how to do anything with this.  Not sure how to go to the repository dialog through the terminal window. but heres the errors, anyways.

E: Type 'sudo' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem. and than this

E: Type 'sudo' is not known on line 33 in source list /etc/apt/sources.list
E: Unable to lock the list directory

after i click reload.  Please help! im desperate. i really want to play diablo 2 without having to use windows.  whew, sorry i know its not polite to beg.

---

### Post by WW on 2007-06-02
It appears that you (or something) has created an invalid sources.list file.  Can you show the contents of /etc/apt/sources.list here?

---

### Post by jonward0690 on 2007-06-02
Can you open the synaptic package manager at all

---

### Post by zvacet on 2007-06-02
```
cat /etc/apt/sources.list
```

and post it here

---

