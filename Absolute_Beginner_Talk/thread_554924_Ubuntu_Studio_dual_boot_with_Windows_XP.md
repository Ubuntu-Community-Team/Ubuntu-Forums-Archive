---
title: "Ubuntu Studio dual boot with Windows XP"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by dgilo on 2007-09-19
Hi,
I'm a newbie to Linux (only have a bit of Knoppix experience) and I make music so I really want to try out Ubuntu Studio
Is it possible to install Ubuntu Studio on a system where Windows XP is already installed and have a dual boot option ?

I have been searching the net and this forum and find a lot of info on dual booting Ubuntu with XP, but nothing on Ubuntu Studio and XP specifically. Since installing Ubuntu Studio is a little different from installing the Ubuntu (text based vs live cd) I wanted to double check.

thanx in advance

---

### Post by por100pre1 on 2007-09-19
Go ahead and install Ubuntu Feisty 7.04. Once you have Ubuntu installed reboot and login into Ubuntu and in Terminal (Applications> Accesiories> Terminal) Copy, Paste and ENTER this lines one by one:

```
sudo aptitude update && sudo aptitude upgrade
```

(use your user password when prompted)

```
sudo reboot
```

You system will reboot...

Log back in and then do [this]("http://ubuntuforums.org/showpost.php?p=3352670&postcount=2").

When finished you'll have Ubuntu Studio with all it's software.

---

### Post by dgilo on 2007-09-19
thanx a lot for the detailed info !

so it's not possible to do it from the Ubuntu Studio dvd ? because i have downloaded and burned that already. If it is, I'd like to try it. Or doesn't this install take any other OS into consideration ?

also, when you upgrade Ubunto to Studio like you explained, is it exactly the same? I mean also the low latency kernel ? 

greetz

---

### Post by por100pre1 on 2007-09-19
> **dgilo said:**
> thanx for the info !

so it's not possible to do it from the Ubuntu Studio dvd ? because i have downloaded and burned that already. If it is, I'd like to try it. Or doesn't this install take any other OS into consideration ?

also, when you upgrade Ubunto to Studio like you explained, is it exactly the same? I mean also the low latency kernel ? 

greetz

You can install it with the DVD. No LiveDVD is the big difference.

You will get the low latency kernel with either method.

The method suggested is shown in the [Ubuntu Studio webpage]("http://ubuntustudio.org/downloads").

---

### Post by johnny.c on 2007-09-25
Another big thanks for this info here :)

---

