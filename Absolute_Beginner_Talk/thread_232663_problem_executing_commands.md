---
title: "problem executing commands"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by sanamana on 2006-08-09
Hello Folks,
I have installed ubuntu 3 days ago, so that I have dual boot now.

I didn't install any other software or packages, but I cannot get simple commands to work.

For example.. vi doesn't work

vi ~/.bashrc
bash: vi: command not found 

I am absolutely new to the unix environment. Can I get some help.

Thanks

---

### Post by louis_nichols on 2006-08-09
Well... for each program to work, it has to be installed. :) Try this:

```
sudo apt-get install vi
```
and then run vi. ;)

---

