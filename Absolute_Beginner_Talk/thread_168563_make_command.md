---
title: "make command"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-04-30
I'm trying to run make but get this error at the end and my executebale disappears?? any ideas?

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


Thanks

---

### Post by ComplexNumber on 2006-04-30
[quote=neelabhro]I'm trying to run make but get this error at the end and my executebale disappears?? any ideas?

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


Thanks[/quote]
have you got the rest of the output beginning from when you run './configure'? that would also give people a clue as to what program you're trying to compile. nobody can help you given the amount of information that you've given there :)

---

### Post by AndyCooll on 2006-04-30
Have you installed the "make" utility?

```
sudo apt-get install build-essential
```

:cool:

---

### Post by Sef on 2006-04-30
> 
Code:

sudo apt-get install build-essential



Before installing build-essential, you should update your computer to the repositories:

sudo apt-get update

sudo apt-get install build-essential

---

### Post by Bloch on 2006-05-01
This is the Absolute Beginner forum. Compiling code (which is what you are doing using make) is not expected off beginners, or even an experienced systems administrator at all for that matter.
Are you sure that the software you are trying to compile does not already exist as a debian package?

I'm all for people jumping in at the deep end. But you should know it is the deep end, and so don't be frustrated if nothing works out.

The packages to use 'make' are not in the default installation of ubuntu because ubuntu is designed for a non-technical user.

---

### Post by nanotube on 2006-05-01
[QUOTE=Bloch]
The packages to use 'make' are not in the default installation of ubuntu because ubuntu is designed for a non-technical user.[/QUOTE]
maybe so, but this seems to be one of the most frequently asked question on these forums  - "i am trying to compile such and such, and get make command not found error, and gcc not found, etc". i mean, this is a linux system - it should frign have make and gcc and friends. 

so this is one of my "gripes" with ubuntu, basically just due to seeing this on the forums all the time - i have installed build-essential a long time ago and have no personal cause to complain. ;)

also, ubuntu is not actually made for the non-technical user. it is very technical-user-friendly. compared to what i heard of linspire and xandros, for example. 

well, anyway, just wanted to air this out. :)

---

