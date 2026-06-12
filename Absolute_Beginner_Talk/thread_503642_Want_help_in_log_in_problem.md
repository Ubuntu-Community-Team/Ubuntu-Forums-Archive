---
title: "Want help in log in problem ?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Edmund Loong on 2007-07-18
Hi !

I am  using Ubuntu 7.10, but don,t know what happen the Log In Problem !

Yesterday,  when I finish type the username & password correctly want to log in as before, after Enter it take a few secound , the screen return back to the original Login request ?

I have try reboot the computer again & again , still the same problem !

Can anyone tell me what is going on and how to due with it back to normal ?

Best rgds.


Edmund Loong

---

### Post by FunkyJack on 2007-07-18
Does it shows you error messages like: wrong username or wrong password?

---

### Post by Edmund Loong on 2007-07-18
Hi Jack,

I am sure input the right username & password !


Edmund

---

### Post by Edmund Loong on 2007-07-18
Sorry Jack !

It dose not shows any error messages  !

best rgds.


Edmund

---

### Post by Wim Sturkenboom on 2007-07-18
The partition / or /home is probably full. Press <ctrl><alt><Fx> (where x is 1..6) and you should be able to login in a console. Check what is full with the command *df -h* and cleanup. If in doubt, post the output of previous command here.

```

wim@desktop1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda7              25G  2.2G   22G  10% /**
varrun                506M   92K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  112K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-28-386/volatile
**/dev/sda9              99G  134M   94G   1% /home**
/dev/sda1              26G  3.0G   23G  12% /media/sda1

```No worry if you don't have a /home partition.

Commands to read up on:
cd to change directory
rm to remove file
rmdir to remove directory

Use man commandname to find info about exact syntax.

---

### Post by Edmund Loong on 2007-07-21
Thank you for your help !

It work!

Rgds

Edmund

---

### Post by Wim Sturkenboom on 2007-07-21
Pleasure; please consider editing the title of your opening post and adding the word 'solved'.

edit post-> go advanced

---

