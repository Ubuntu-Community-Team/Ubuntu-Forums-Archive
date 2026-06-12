---
title: "Su Authentication Failure"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by griff01 on 2006-07-31
... and on the second day...(two days since XP!) ..still battling...****

When I try and use sudo it gives me:

su: Authentication failure
Sorry.

Yet I'm typing in the password I use to login to Ubuntu (the only one I'm aware I've set).

Any suggestions?

Oh and I don't see any numerals or * when I type in the password is this normal?

Cheers

Griff

---

### Post by cstudent on 2006-07-31
You're entering sudo followed by a command or just su?

EDIT:
After some quick checking, you are just entering su. You need to use the sudo command. That would be immediately followed by some instruction to perform. For example:

```

sudo chmod +x test.sh

```

You'll be prompted for your password (your user password like you are trying) and then the action would be executed.

---

### Post by griff01 on 2006-07-31
just su

it then asks for my password

---

### Post by griff01 on 2006-07-31
ok here goes...

---

### Post by Kilz on 2006-07-31
> **griff01 said:**
> ok here goes...

You use sudo instead of su in Ubuntu

---

### Post by griff01 on 2006-07-31
Thanks - getting a little further but still doing soemthing wrong.

What I'm trying to do is check the 915Resolution 

Obviously going wrong somewhere....

griff@griff-laptop:~$ sudo #915resolution -l
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
griff@griff-laptop:~$

???

Griff

---

### Post by griff01 on 2006-07-31
Sorted!

Doh! Starting to get it now! I just type sudo + command

sudo 915Resolution -l

All is there to see

Cheers guys

Griff

---

### Post by cstudent on 2006-07-31
I've never used 915resolution, so I can't offer much help there. I did find this website which may help you.

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Good luck
cstudent

---

