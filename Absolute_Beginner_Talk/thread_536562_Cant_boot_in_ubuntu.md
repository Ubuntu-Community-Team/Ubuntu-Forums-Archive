---
title: "Cant boot in ubuntu"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Likenota on 2007-08-27
okay when i boot it gives an error of something being in the file system error so it runs the check then a bunch of numbers display then it says check failed...

Automatic file system check failed the root file system is mounted in read only mode..





it also says:

the program 'apt-get' is currently not installed you can install it by typing apt-get install apt



and that doesnt work either... so how do i change it to read and write? and how on earth am i suppose to isntall apt when it didnt even work for the command, i have compiz fusion and vmware so i dont understand how i dont have the apt thingy. please help.

---

### Post by MQMike on 2007-08-27
I also got the apt-get error.  I just did Control-D to get past it.  I don't know what that's about.  My apt-get works fine . . .?

---

### Post by mrphd on 2007-08-28
> **Likenota said:**
> okay when i boot it gives an error of something being in the file system error so it runs the check then a bunch of numbers display then it says check failed...

Automatic file system check failed the root file system is mounted in read only mode..

Try:

```
fsck -v
```

---

