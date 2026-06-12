---
title: "How do i find out which version of Linux i am using"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by daveholt88 on 2007-04-10
I know this is probably pretty simple but im not too familiar with linux yet. I am trying to use amsn but on login it says I need to download TLS files and asks for the version of linux i am using and gives me the several options, how do i find out which one i am using. I know this sounds stupid but a friend installed it for me.

---

### Post by caffienefree on 2007-04-10
In the terminal, type the following:

cat /etc/lsb-release

---

### Post by mac.ryan on 2007-04-10
Basic information can be retrieved by typing:

```
uname -a
```

EDIT: this command gives you info on what version of the kernel you are running, the command proposed by the other user gives you info on what version of ubuntu.

---

### Post by mrpaco on 2007-04-10
Typing "uname -r" (without quotes) will tell you which version of the Linux Kernel you are running.  Hope this helps!

- Tom

---

### Post by daveholt88 on 2007-04-10
Cheers, much appreciated :)

---

### Post by in_flu_ence on 2007-04-10
i think you can try typing "uname -a" at the console/terminal.

if it says 2.6.17, then you are using edgy. if it is 2.6.20 you probably is using feisty and i think 2.6.15 is for dapper.

That's the linux kernal version.

I m surprised that you were asked for the info when you try to login to amsn. Isn't it just ask for either a login name/password or a pre-created profile?

what other options did it give you?

---

### Post by LaurelLynn on 2007-04-10
For the GUI obsesed try:

System->About Ubuntu

---

### Post by in_flu_ence on 2007-04-11
> **LaurelLynn said:**
> For the GUI obsesed try:

System->About Ubuntu

That will be for Gnome (Ubuntu)

---

### Post by Obor on 2007-04-11
```
lsb_release -c

```
will give you name i.e dapper/edgy/feisty

---

