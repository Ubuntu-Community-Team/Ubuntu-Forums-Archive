---
title: "Operative System Login problem"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by juancruz on 2007-01-20
It seems that my ubuntu doesnt recognize my Login, User and/ or password or I forgot them...how do I change them??

---

### Post by ComplexNumber on 2007-01-20
> **juancruz said:**
> It seems that my ubuntu doesnt recognize my Login, User and/ or password or I forgot them...how do I change them??
what exactly happens when you try to login? 

also, i know it sounds all too obvious, but have you got your caps lock on?

---

### Post by bodhi.zazen on 2007-01-20
Boot to recovery mode

To see users:

```
less /etc/shadow
```

To set new PW:

```
passwd <user_name>
```Where <user_name> is the user password you want to set :p

Reboot

---

### Post by juancruz on 2007-01-20
It says: wrong user name or password....and Im sure both were my name, I didnt chose a hard to remember user password , cause no one else around me likes Linux.
Sure....I know about the caps lock item...

---

### Post by bodhi.zazen on 2007-01-20
Look up ...

---

### Post by juancruz on 2007-01-25
Bodhi ZaZen
It doesnt work the commands you tell me to use.

---

### Post by bodhi.zazen on 2007-01-25
Odd ...

1. Did you boot to the recovery mode ? You should then be root.

2. You can try cat:```
cat /etc/shadow
```That should list all users.

3. Then passwd <username> where <username> is the name of the user whose password you want to change, like this:```
passwd juancruz
```Or what have you as far as user name.

Otherwise, can you give any more information? what happens when you enter those commands ? Error message ?

---

### Post by juancruz on 2007-01-25
I boot to recovery mode : 
Kernnel Ubuntu 6 10 5 386 (recovery mode)

then when i get :
Root@Ubuntupc12: 
I type:

less/etc/shadow  or cat/etc/shadow

I get: No such file or directory

And if I type : 
passwd juancruz or whatsoever i get:

Bash:Syntax error near unexpected token "Newline"

---

### Post by bodhi.zazen on 2007-01-25
You need a space between less or cat and /etc/shadow

What do you get when you : ```
ls /etc
```

---

### Post by juancruz on 2007-01-25
Problem solved!...Thanks a lot...I was missing the space....

---

