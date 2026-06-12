---
title: "need help with hydra"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by JuNk101 on 2006-11-04
hello im new to ubuntu and i need some help how can i install hydra on ubuntu 6.10 i tryed ./configure make make install and it wont work im lookin for a step by step tutorial any help?

---

### Post by po0f on 2006-11-04
JuNk101,
```
$ sudo aptitude install build-essential
```

---

### Post by JuNk101 on 2006-11-05
alright im already confused sudo aptitude install build-essential

type sudo aptitude install [hydra]

---

### Post by po0f on 2006-11-05
JuNk101,

Open up a terminal:
```
$ sudo aptitude install build-essential checkinstall
$ cd /where/you/extracted/hydra
$ ./configure && make && sudo checkinstall -D
```

---

### Post by JuNk101 on 2006-11-05
alright thanks the last step tho did everything but at the end it ses make: *** [hydra-sip.o] Error 1

---

### Post by po0f on 2006-11-05
JuNk101,

Can you post the 4-5 lines above that error as well?

---

### Post by JuNk101 on 2006-11-05
ya
hydra-sip.c:60: error: ‘MD5_DIGEST_LENGTH’ undeclared (first use in this function)
hydra-sip.c:61: warning: unused variable ‘resp’
hydra-sip.c:61: warning: unused variable ‘mu’
hydra-sip.c:60: warning: unused variable ‘urp’
make: *** [hydra-sip.o] Error 1

---

### Post by po0f on 2006-11-05
You might need to install [this](http://packages.ubuntu.com/edgy/libdevel/libssl-dev) package first:
```
$ sudo aptitude install libssl-dev
```

---

### Post by JuNk101 on 2006-11-05
k after that i would redo the the steps you told me above?

---

### Post by po0f on 2006-11-05
JuNk101,

Yes, just to make sure, rerun configure:
```
$ ./configure && make && sudo checkinstall -D
```

---

### Post by JuNk101 on 2006-11-05
alright thanks so much for your help youve been really helpfull with no problems buti gotta nother questoin i cant get it to work it ses to type in terminal ./hydra -h is that right?

---

### Post by po0f on 2006-11-05
JuNk101,

After you install it, you should just be able to run it directly from the terminal:
```
$ hydra
```

I'm not familiar with the program, so I don't know it's options.  Generally, -h lists the help, so that would be a good place to start.  :)

---

### Post by JuNk101 on 2006-11-05
ya its not workin but ill figure it out but thanks alot for your help it was much appriciated

---

