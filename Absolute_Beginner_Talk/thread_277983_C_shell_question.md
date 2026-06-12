---
title: "C shell question"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-15
How do you make the C shell echo utility recognize the tab (\t) from within a script?  If I enter
```
echo $mystring \t
```
I end up with
whatever my string was t
](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Rui Pais on 2006-10-15
hi, try:
```
echo -e "$mystring \t"
```

---

### Post by opticsnake on 2006-10-15
Sadly, that didn't work either.
](*,) and again](*,)

---

### Post by elettronicha on 2006-10-15
echo -e "mystring \t"

---

### Post by elettronicha on 2006-10-15
echo -e "mystring \t"

---

### Post by Rui Pais on 2006-10-15
> **opticsnake said:**
> Sadly, that didn't work either.
](*,) and again](*,)

sorry, you are right. That only works for bash (and tclsh) :(

Reading the man pages for csh, it seems that you need to set echo_style variable to 'sysv' (or even 'both'?) to echo read \t, \n and so on... 
I don't really understand csh configuration, hope you know how that is made (probably on some conf file)...

---

### Post by Arndt on 2006-10-16
> **Rui Pais said:**
> sorry, you are right. That only works for bash (and tclsh) :(

Reading the man pages for csh, it seems that you need to set echo_style variable to 'sysv' (or even 'both'?) to echo read \t, \n and so on... 
I don't really understand csh configuration, hope you know how that is made (probably on some conf file)...

But you can call the _command_ 'echo', rather than the shell's built-in 'echo'. Either name it explicitly:

```
% /bin/echo -e "a\tb"
a       b
```

or mark it as not being special in the shell:

```
% \echo -e "a\tb"
a       b
```

You may want to run 'tcsh' instead of 'csh' - it's a superset, and does know about \t in echo.

---

### Post by opticsnake on 2006-10-17
Many thanks Arndt!  Both of those solutions worked!  I chose the second one for my script since it's less to type but, tested both and they each do the job.

---

