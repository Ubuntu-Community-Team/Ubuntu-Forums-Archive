---
title: "compiling"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-08-19
hi

i'm having trouble compling software in the shell.

being a previous windows user i've never had to compile before so this is totally new to me.  i think i'm doing it right but i keep getting "error 1" and "error 2". does anybody know what these errors are?

i have tried researching for myself but all i can find is people slagging off noobs for not being born with this knowledge. 

if anyone can link me to  a walkthrough that would be great also.

cheers.

---

### Post by taurus on 2007-08-19
It would be real helpful if you include the command that you ran and the whole error message.  That way, people would know what's wrong with it instead of playing a guessing game here.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by RomeReactor on 2007-08-19
Hi. What are you trying to compile? Have you searched [GetDeb]("http://www.getdeb.net/") or the [Ubuntu Packages]("http://packages.ubuntu.com/") site to see if there's a precompiled version of your program? Did you install **build-essential** and your program's dependencies before attempting to compile?

---

### Post by rob1984 on 2007-08-19
i've had a crack at it and now i'm getting:
configure: error: C compiler cannot create executables.

trying to compile xine 1.1.7
full message is in the attached .txt.

cheers

---

### Post by taurus on 2007-08-19
You know you can install xine-lib & xine-ui from synaptic or apt-get/aptitude.  Otherwise, you need to install the build-essential package first before you can compile anything from source.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by rob1984 on 2007-08-20
i already have the build essential but i'll get the aptitude update and try again.

---

