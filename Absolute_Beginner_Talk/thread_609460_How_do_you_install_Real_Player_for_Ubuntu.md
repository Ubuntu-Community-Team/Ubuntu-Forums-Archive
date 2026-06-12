---
title: "How do you install Real Player for Ubuntu"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Charlie Dorff on 2007-11-11
Hi...
I was wondering how to install Real player on Ubuntu. I listen to BBCworld servie online and it requires Real Player. Thanks.
Charlie

---

### Post by dcstar on 2007-11-11
> **Charlie Dorff said:**
> Hi...
I was wondering how to install Real player on Ubuntu. I listen to BBCworld servie online and it requires Real Player. Thanks.
Charlie

Download the RealPlayer10GOLD.bin file from the RealPlayer site, then in a terminal (in the directory you downloaded it to):

```
sudo ./RealPlayer10GOLD.bin
```

And answer any questions etc.

---

### Post by quddusaliquddus on 2008-03-24
Hi all. I followed your instructions but with version 11 of realplayer but the termianl says "sudo: ./RealPlayer11GOLD.bin: command not found"

Any ideas on how i can fix this?

Many thanks :D

Regards
Q

---

### Post by Dark Star on 2008-03-24
Real player performance is pathetic.. No need to install it.. Rather use Media Ubuntu packages to play .rm files [How to : Enable Multimedia Suport in Ubuntu 7.10.]("http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/")

---

### Post by jan quark on 2008-03-24
```
sudo chmod a+x /home/yourname/RealPlayer10GOLD.bin
```

now you can execute the file
this code changed the file permissions so it is executable

---

### Post by quddusaliquddus on 2008-03-24
How do i execute the file? I tried dbl clicking the Real Player bin file - but that didnt work

---

### Post by jan quark on 2008-03-24
> How do i execute the file? I tried dbl clicking the Real Player bin file - but that didnt work
see your post :)

---

### Post by quddusaliquddus on 2008-03-24
silly me. I see now that you've posted the code. What do i replace' yourname' with? The reaplayer bin file is on my desktop so would the following work?

```

sudo chmod a+x /desktop/RealPlayer10GOLD.bin

```

---

### Post by jan quark on 2008-03-24
this should be correct
```
sudo chmod a+x home/<your username you type when you login>/Desktop/RealPlayer10GOLD.bin
```

linux is case sensitive so desktop is not the same as Desktop

---

