---
title: "My C Compiler"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Flyingroof on 2007-07-23
Apparently my C Compiler cannot create executables, or atleast, thats what the terminal tells me every time I try to ./configure something. What should I do to fix this?

---

### Post by Paerez on 2007-07-23
Welcome to the forums, flyingroof.

Could you please post all the output? Thanks.

---

### Post by aks44 on 2007-07-23
Did you install the build-essential package? If yes, please post the exact error message as we can hardly guess from your post what is wrong with your install.

---

### Post by Darklighter137 on 2007-07-23
If I understand your problem, create your progam like so:  gcc filename -o outputname
Then, from the directory that you compiled your program, type ./outputname to run the program (where outputname is of course the name you chose for your program).  Is that helpful at all?

---

### Post by Flyingroof on 2007-07-23
I believe I looked at the build essentials package when I first got linux, I'm not sure if I installed it. Is there a check to see if I did. Also heres the message:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

```

---

### Post by asmoore82 on 2007-07-23
I think you are missing the *'build-essential'* package

Also, you will probably need the '<blank>-dev' packages for whatever dependencies your source package has.

---

