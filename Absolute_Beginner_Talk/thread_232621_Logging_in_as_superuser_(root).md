---
title: "Logging in as superuser (root)"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-08-09
I am trying to install a package which requires that I be logged in as superuser (root). So I use the following:
```
sudo su -
```

Then I get the following prompt

```
root@username: ~#
```

Does that look okay, or am I making some mistake?

---

### Post by mozkaynak on 2006-08-09
it is ok but try to use 

sudo [your command]


option.

so just add sudo in front of your installation command.

you will be asked your own password (I assume you installed the system).

---

### Post by Sef on 2006-08-09
For installing packages, [read this.]("http://monkeyblog.org/ubuntu/installing/")

For information on sudo/root, [read this.]("https://help.ubuntu.com/community/RootSudo")

---

### Post by aam-aadmi on 2006-08-09
I have tried using sudo; it does not work. I get an error message saying "permission denied". That is why I was trying to follow the install instructions to the letter and log in as the root instead of using sudo. But even that does not work! 

Maybe someone who has installed this before in Ubuntu can help; the package is called STATA. It is a statistical package.

Thanks in advance.

---

### Post by arngrim on 2006-08-11
Hi,

I had the same problem as you. I solved it by copying the installation cd to a temp dir: ~/stata-org/

Then I moved to /usr/local/stata/ typed sudo ~/stata-org/install and the installation started.

I guess there is a more elegant way of doing this, but I'm just started to work with Ubuntu :) 

Best,

arngrim

---

