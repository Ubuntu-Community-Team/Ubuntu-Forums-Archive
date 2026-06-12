---
title: "Is there any repositories CDs for download ?"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by mohmf on 2006-11-06
I'm very new to Ubuntu and i has installed Ubuntu 6.10 but i found that there are alot of missed packges and dependices .
i know that there the wonderful apt tool , but i can't use internet in my Ubuntu because some of problems in my modem, so i ask if can i get CD's' that contain the other softwares that are missed from the default installation , help plzz :(

---

### Post by Dinerty on 2006-11-06
I did hear the dvd download of ubuntu contains the some of the repo's, if not all?

---

### Post by ReaderRat on 2006-11-06
You may find a solution to your modem problem here:
[**[color=RED]Modem HowTo[/color]**](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by mohmf on 2006-11-07
> **Dinerty said:**
> I did hear the dvd download of ubuntu contains the some of the repo's, if not all?
I'm also heared that , but the problem is that i'm don't have DVD burner drive , so i want to download CD's because i have CD burner drive ..


> You may find a solution to your modem problem here:

thanks, i will read it ..

---

### Post by sKuarecircle on 2006-11-07
This might help

[http://www.ubuntuforums.org/showthread.php?t=286713](http://www.ubuntuforums.org/showthread.php?t=286713)

---

### Post by Bachstelze on 2006-11-07
> **mohmf said:**
> I'm also heared that , but the problem is that i'm don't have DVD burner drive , so i want to download CD's because i have CD burner drive

What the heck do you need a burner for ? Don't waste CDs / DVDs for it and simply mount the ISO file :)

```
sudo mount -o loop /path/to/file.iso /cdrom
```

---

### Post by sKuarecircle on 2006-11-07
> **HymnToLife said:**
> What the heck do you need a burner for ? Don't waste CDs / DVDs for it and simply mount the ISO file :)

```
sudo mount -o loop /path/to/file.iso /cdrom
```

Its on another computer oh bright one:D

---

### Post by Bachstelze on 2006-11-07
That's what USB drives are for :)

---

### Post by mohmf on 2006-11-07
> What the heck do you need a burner for ? Don't waste CDs / DVDs for it and simply mount the ISO file 
Ohh , this is great idea , Why i don't try that ??
but u know what the problem ? i must download entire DVD ???!!
in my country this seem impossible . so i want a CD not DVD !

---

### Post by Bachstelze on 2006-11-07
You could also download the packages you need from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them manually with dpkg -i but it can become quite tedious if there are complex dependencies...

Maybe consider switching to Debian, the latest release has 21 CDs full of apt-get'able packages :)

---

### Post by mohmf on 2006-11-07
> You could also download the packages you need from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them manually with dpkg -i but it can become quite tedious if there are complex dependencies...
That's realy is my nightmare :confused: !! ...

> Maybe consider switching to Debian, the latest release has 21 CDs full of apt-get'able packages
when i finished download this 21 CDs , it will be there linux on the moon ](*,) ](*,) !!

---

