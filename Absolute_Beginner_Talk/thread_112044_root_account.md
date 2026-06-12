---
title: "root account"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Grukti on 2006-01-03
first i have say that i have more than 2 years exprience(mainly used them as psybnc, www, ircbots servers) in using linuxs (i have used debians, redhats, mandrake i have not yet found right one, maybe ubunta will be right one if works as i want it do work). I like way that i can log in as root account to configure linux in graphig mode(like in kde or gnome).

Now to problem
when i try log in as root it says somethign like that i am not allowed log in as root. yep i know that can just use sudo <command> or just type password when needet but i dont like typing password every time i have configure something so that is why i want use root account to it so i dont have use type that password. 

So can anyone tell me how to i remove this root account restirection?

---

### Post by carlosqueso on 2006-01-03
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin#head-8352bb412ccfc81b89a48144986e8690c66e338c](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin#head-8352bb412ccfc81b89a48144986e8690c66e338c)

That link tells you how to do it...although it may break some of your graphical config tools.  You can get a root shell by "sudo -i" or "sudo su" if that helps.

---

### Post by 23meg on 2006-01-03
```
sudo passwd root
``` will allow you to enable the root account. To enable logging into Gnome as root, go to System / Administration / Login Screen Setup / Security and check the "Allow root to login with GDM" checkbox.

Disclaimer: Just don't do it.

---

### Post by Grukti on 2006-01-03
[QUOTE=23meg]```
sudo passwd root
``` will allow you to enable the root account. To enable logging into Gnome as root, go to System / Administration / Login Screen Setup / Security and check the "Allow root to login with GDM" checkbox.

Disclaimer: Just don't do it.[/QUOTE]
thanks for help and i have done it now :>

---

### Post by estel on 2006-01-03
"Don't do it"
"Thanks... I have done it"

That's great :D

---

### Post by 23meg on 2006-01-03
[QUOTE=estel]"Don't do it"
"Thanks... I have done it"

That's great :D[/QUOTE]
Indeed, it's great that everyone has the freedom to use their computer the way they like, as long as they're ready to face the consequences of any action they consciously take. No use in pressuring anyone to abide by "the rules".

---

### Post by Grukti on 2006-01-03
yep its my computer i can do it anything i want and if i messed something really bad it not big deal to install that again i dont have anything in linux that is not backuped somewhere (videos, etc files are on dvd:s, softwares can always installed back again).... :cool: 

i will not face consequence of my action... it's computer who facing them not me heh.. as i sayed its not big deal install everthing again(in my case)... i just want use root account to graphical configure everthing without typing password when asked (everthing else i will use normal account)

i have noticed now that gdmsetup program is not accepting root password (i have written it correctly, one more reason to use my way)

---

### Post by fastluck on 2006-01-03
[QUOTE=Grukti]Now to problem
when i try log in as root it says somethign like that i am not allowed log in as root. yep i know that can just use sudo <command> or just type password when needet but i dont like typing password every time i have configure something so that is why i want use root account to it so i dont have use type that password. 

So can anyone tell me how to i remove this root account restirection?[/QUOTE]

```

sudo su -

passwd root


```

---

