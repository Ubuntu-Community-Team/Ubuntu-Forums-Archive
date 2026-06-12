---
title: "linux question..help"
date: 2005-09-03
forum: Apple PPC Users
---

### Post by yhcheong on 2005-09-03
im a newbie in linux . i had installed ubuntu on my pc. here some of my questions 
1. LINUX file system had evolved from Minix to EXT2 and then to the current Virtual File System.why there was a change from Minix to EXT2 and then to the current Virtual File System. 

2. What packages should  get and what are the setting needed to start  C codes excutions.. 


  can anyone answer my quest ions?  will appreaciate...

---

### Post by osxus3r on 2005-09-03
I am not a linux expert, but I think I can answer you questions

1) ext2 is better than minix
2) what do you mean by 'start C codes excutions' ? if you want to compile c programs you need a compiler, like gcc which comes with pretty much every distribution, so for example, to compile a c program you could just type:

```
gcc filename.c
```

the default output file is 'a.out'

---

### Post by yhcheong on 2005-09-03
the gcc command, by default , i mean when i install the ubuntu, it already install? do i need to download the packages for gcc?

---

### Post by stuporglue on 2005-09-24
Gcc isn't installed by default. Use Synaptic to install it, or just run "sudo apt-get install gcc"

---

