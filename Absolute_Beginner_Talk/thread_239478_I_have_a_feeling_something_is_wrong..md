---
title: "I have a feeling something is wrong."
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-08-19
Hi, I've been on vacation for a week and during that time was the dist upgrade to 6.06.1. I don't think I upgraded, but I'm not sure. I did sudo apt-get update sudo apt-get dist upgrade and nothing.  Is there I way I can find the dist version of Ubuntu

---

### Post by matthew on 2006-08-19
Open a terminal and type```
lsb_release -a
```if your output looks like mine you are all set (and I believe it will look like mine)```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

```

---

### Post by Klaidas on 2006-08-19
Are you trying to upgrade to edgy eft?

---

### Post by zxcvbnm on 2006-08-19
Thanks mine is the same as yours.


And Klaidas, Nah I wanted to make sure I had upgraded to 6.06.1 because of the bugfixes. Thanks though

---

### Post by taurus on 2006-08-19
If you run "sudo apt-get update && sudo apt-get upgrade," you should be fine...

---

