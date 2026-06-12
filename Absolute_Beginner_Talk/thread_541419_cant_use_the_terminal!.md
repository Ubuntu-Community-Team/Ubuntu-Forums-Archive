---
title: "cant use the terminal!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by perversevoodoo on 2007-09-02
Hi. I'm completely new in linux.

I really need some help..! 

I cant use the terminal.. When i write a command (ex: sudo --login -c 'visudo') it asks for "password"..

I enter any password that i can think of it can be.. The one that i use for logging into linux.. and the ones that i use often... and the "toor" password.. But it either gives me the "auth failure sorry" message or this message?? :

" sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
voodoo@voodoo-laptop:~$ "

EDIT: and now it gave me this message:

" ********voodoo@voodoo-laptop:~$ ********* " (the "*"' replacing the password that i entered.)


what am i doing wrong and am i just a complete retard? please help me.. Ive searched google. forum but cant find anything that helps me. 

Would REALLY appreciate some answers, thanks.

-voodoo

---

### Post by meierfra on 2007-09-02
The password you need to use for sudo is your login password.

sudo does not have --login as an option. So  "sudo --login" is not a valid command.   Where did you get that command from?

---

### Post by perversevoodoo on 2007-09-02
Ive tried that password a mill times!! it just gives me the : auth failure sorry... 

Well the 2 other messages i wrote before? what does they mean?

And i really don't know where i got that command.. but ive also tried alot of other commands but steal the "password" and then some message..

---

### Post by IcemanV9 on 2007-09-02
The correct syntax is:

```
sudo visudo
```

Like meierfra said, use your login password for sudo password.

---

### Post by meierfra on 2007-09-02
You will always get an error message if your try command which does not exit. To test whether  your login password works with sudo try this:

Type
```
sudo fdisk -l
```
(( the l is  a lower case L)
Hit enter. Then type your password (you won't see any output  while typing your password) and hit enter again.

This should give you some information about your partitions.

---

### Post by perversevoodoo on 2007-09-02
well i DO use that password. 

if you mean the

Ubuntu loggin

"username"

"password"

And guess thats what you mean.

---

### Post by meierfra on 2007-09-02
Don't do "sudo visudo" yet. You might really screw up things. Lets first figure out what is going on.

---

### Post by meierfra on 2007-09-02
> if you mean the

Ubuntu loggin

"username"

"password"


yes, that is the one you should be using.

---

### Post by perversevoodoo on 2007-09-02
well.. what can i do to figure that out??

back in 5 min. (smoke)

---

### Post by perversevoodoo on 2007-09-02
Ok if thats the one that i should be using i dont understand..

it just wont accept it..

---

### Post by meierfra on 2007-09-02
Did you try my  "sudo fdisk -l" test? Post any output  so that I can see what is going on.

---

### Post by meierfra on 2007-09-02
the "l" in "fdisk -l" is a lower case L" . I left that out in the original post.

---

### Post by PriceChild on 2007-09-03
*moves and bumps*

---

