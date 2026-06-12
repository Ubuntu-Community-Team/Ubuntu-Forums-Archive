---
title: "[SOLVED] about shell"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-14
i dont know if this is the right place to ask this question but maybe someone can help me

i am new to linux and i have been trying to figure everything out,
i have found a website wich i have been reading and and i have come to the part where it talks about the basics of shell.
here
[http://rute.2038bug.com/node10.html.gz]("http://rute.2038bug.com/node10.html.gz")

my problem is that i cannot get this stuff to work right for instance if i do this part

echo "I will work out X*Y"
echo "Enter X"
read X
echo "Enter Y"
read Y
echo "X*Y = $X*$Y = $[X*Y]"

it come out like this

tj@tj-laptop:~/Desktop$ ./My_first.sh
I will work out X*Y
Enter X
**2**
Enter Y
**12**
X*Y = 2*12 = $[X*Y]
tj@tj-laptop:~/Desktop$ 

however if i type something like echo $[2*12] it works and gives me the answer

can somebody please help

---

### Post by jan quark on 2008-02-14
programming talk would be better for such  questions I suppose
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
:)

---

### Post by amingv on 2008-02-14
Try

```
echo $[$X*$Y]
```

---

### Post by y-lee on 2008-02-14
oddly enough it works for me

```
starhawk@home:~$ echo "I will work out X*Y"
I will work out X*Y
starhawk@home:~$ echo "Enter X"
Enter X
starhawk@home:~$ read X
2
starhawk@home:~$ echo "Enter Y"
Enter Y
starhawk@home:~$ read Y
12
starhawk@home:~$ echo "X*Y = $X*$Y = $[X*Y]"
X*Y = 2*12 = 24
```

That was in Gnome terminal 2.14.2 in dapper, :confused:

What terminal program you using?

---

### Post by tjwoosta on 2008-02-14
i tried echo $[$X*$Y]

this is what i got

X*Y = 2*12 = $[2*12]

---

### Post by tjwoosta on 2008-02-14
im using  Gnome Terminal 2.18.2 in gutsy

---

### Post by amingv on 2008-02-14
> **y-lee said:**
> oddly enough it works for me

```
starhawk@home:~$ echo "I will work out X*Y"
I will work out X*Y
starhawk@home:~$ echo "Enter X"
Enter X
starhawk@home:~$ read X
2
starhawk@home:~$ echo "Enter Y"
Enter Y
starhawk@home:~$ read Y
12
starhawk@home:~$ echo "X*Y = $X*$Y = $[X*Y]"
X*Y = 2*12 = 24
```

That was in Gnome terminal 2.14.2 in dapper, :confused:

What terminal program you using?

Oddly enough, it works for me in shell mode, but not in script mode. I guess this one is above me.

---

### Post by amingv on 2008-02-14
Hmmm... Interesting, put this line atop your script:

```
#!/bin/bash
```

Once more bash proves all-powerful...

---

### Post by Dr Small on 2008-02-14
Is this mathematical?
If so, it needs to be done like this:
```
answer=$((2+2))
echo $answer
```

---

### Post by tjwoosta on 2008-02-15
ahhh it works when i put the 
#!/bin/bash 
instead of 
#!/bin/sh

what exactly does this do?  Im just trying to learn the basics of this stuff, i have been following this guide from the start. [http://rute.2038bug.com/index.html.gz]("http://rute.2038bug.com/index.html.gz")

---

