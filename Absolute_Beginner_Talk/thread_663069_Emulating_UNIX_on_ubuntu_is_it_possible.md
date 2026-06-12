---
title: "Emulating UNIX on ubuntu is it possible?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Altamarus on 2008-01-09
Hello I am running Linux and I have to run a .bin file that has been compilated in UNIX. Is there an emulator that could do the job? 

Thanks in advance!

---

### Post by llamakc on 2008-01-09
chmod +x file.bin

./file.bin

OR

sh /path/to/file.bin

---

### Post by Altamarus on 2008-01-09
> **llamakc said:**
> chmod +x file.bin

./file.bin

OR

sh /path/to/file.bin

I tried it but I get this result: (note that I am in the folder with the ProSyn binary

x@x-laptop:~/Desktop$ chmod +x ProSyn.bin
chmod: cannot access `ProSyn.bin': No such file or directory

OR

x@x-laptop:~/Desktop$ sh ProSyn.bin
sh: Can't open ProSyn.bin

---

### Post by p_quarles on 2008-01-09
In this directory, what is the output of:
```
ls -l
```
If it's a lot of output, you can cut most of them; the only relevant one is the entry for ProSyn.bin.

---

### Post by RomeReactor on 2008-01-09
> **Altamarus said:**
> I tried it but I get this result: (note that I am in the folder with the ProSyn binary

x@x-laptop:~/Desktop$ chmod +x ProSyn.bin
chmod: cannot access `ProSyn.bin': No such file or directory

OR

x@x-laptop:~/Desktop$ sh ProSyn.bin
sh: Can't open ProSyn.bin

Hi. Please note that from your terminal output you're in the Desktop; if you dont' have the file there, change directory first to where the file is.

---

### Post by Altamarus on 2008-01-09
> **p_quarles said:**
> In this directory, what is the output of:
```
ls -l
```
If it's a lot of output, you can cut most of them; the only relevant one is the entry for ProSyn.bin.

xx@xx-laptop:~/Desktop$ ls -l 

-rwxrwxrwx 1 xx xx 186604 2008-01-09 13:32 ProSyn

---

### Post by p_quarles on 2008-01-09
In that directory, type:
```
./ProSyn
```

---

### Post by jordanmthomas on 2008-01-09
just run 
```
./ProSyn
```

If it complains about permissions, (this may be an installer, I don't know what ProSyn is)
```
sudo ./ProSyn
```

edit 
beaten :|

---

### Post by jordanmthomas on 2008-01-09
Also, which UNIX was it compiled under?
Odds are, if it was made for something other than Linux it won't run under Linux without a recompile.

---

### Post by Altamarus on 2008-01-09
> **jordanmthomas said:**
> Also, which UNIX was it compiled under?
Odds are, if it was made for something other than Linux it won't run under Linux without a recompile.

You must be right... I get this syntax error....I guess I wont have no choice but to install UNIX hehe

xx@xx-laptop:~/Desktop$ sudo ./ProSyn
[sudo] password for xx:
./ProSyn: 1: Syntax error: "(" unexpected

---

### Post by p_quarles on 2008-01-09
> **Altamarus said:**
> You must be right... I get this syntax error....I guess I wont have no choice but to install UNIX hehe

xx@xx-laptop:~/Desktop$ sudo ./ProSyn
[sudo] password for xx:
./ProSyn: 1: Syntax error: "(" unexpected
Are you sure this is a binary? Try running:
```
less ProSyn
```
If it says "warning, this is a binary," just cancel. If it displays text, it's not a binary.

---

### Post by Altamarus on 2008-01-09
> **p_quarles said:**
> Are you sure this is a binary? Try running:
```
less ProSyn
```
If it says "warning, this is a binary," just cancel. If it displays text, it's not a binary.

less ProSyn
"ProSyn" may be a binary file.  See it anyway?

---

### Post by HermanAB on 2008-01-09
Install VMware, then install OpenSolaris or whatever you got in that.

---

### Post by p_quarles on 2008-01-09
Okay, so it's definitely a binary. 

Can say a bit more about this file? What it's supposed to do? Did it come with any instructions or guidelines?

---

