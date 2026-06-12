---
title: "accidently chmod everything to me? sudo doesn't work."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by puccaso on 2007-03-10
ok
so i was moving some old files from an old directory to my new user directory

and i accentally did ```
chmod mahir:mahir / 
```

ok
so now things dont work well
how do i fix this?

i mean the most important thing right now seems to be sudo

sudo doesnt work

this is what i get

```
mahir@jt-laptop:~$ sudo -s
sudo: must be setuid root
mahir@jt-laptop:~$ su
Password: 
setgid: Operation not permitted
mahir@jt-laptop:~$ sudo su
sudo: must be setuid root
mahir@jt-laptop:~$ sudo -s su
sudo: must be setuid root
mahir@jt-laptop:~$ 
```


how do i fix this?

---

### Post by igknighted on 2007-03-10
you could log in recovery mode, you are root there.  Once there I'm not sure what you could do however.  Why were you messing around w/ chmod commands when moving files?  There shouldn't be any need for that.  Your best bet might be (I'm sorry to say) backing up and doing a reinstall.

---

### Post by chavo on 2007-03-10
Only way to fix this is a reinstall.

---

### Post by puccaso on 2007-03-10
thats what i did
and i messed something up
it would be easy to install
but im having to follow a certain method
in order not to mess up the vista install :@ argh

ne who

i have a question

how do i make ubuntu automagically re-create fstab?

---

