---
title: "make deb out of source file ?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-25
how I can do that ?
let say I compiled a program from source , how I can make a deb file out of it  and give it to other ppl so they dont compile it ?

---

### Post by Happy_Man on 2007-05-25
uh... you can use checkinstall.
```
sudo apt-get install checkinstall
```

When you want to create a .deb file, do ./configure and make as usual, but instead of sudo make install, use sudo checkinstall. It will walk you through creating a .deb.

---

### Post by testube_babies on 2007-05-25
The easy way is to use checkinstall, but it doesn't handle dependencies well.
```
sudo apt-get install checkinstall
```
When compiling, use "sudo checkinstall" instead of "sudo make install"

---

### Post by medya on 2007-05-25
I am confused.... what does checkinstall do ? 
does it make deb out of an INSTALELD program from source ? can u tell me in example?

---

### Post by dannyboy79 on 2007-05-25
what it does is make a deb out of the soruce files just like you;re asking to be done BUT  since you already installed it I am not sure if this will work for the app in question. It might and you can always just give it a try. Go to the folder that you compiled your program in, you know, the place you ran ./configure, and make, and instead of running install again, just run checkinstall. This will create a .deb for you to pass around to people. Good luck. Also, this way, if you want to uninstall the app, you can simply double click on the .deb in ubuntu and tell it to uninstall or you can use dpkg -r I think but you'd ahve to check on the option for dpkg to uninstall it. good luck

---

### Post by andrew.46 on 2007-06-15
Hi,

 Saw your post:

> **medya said:**
> I am confused.... what does checkinstall do ? 
does it make deb out of an INSTALELD program from source ? can u tell me in example?

 According to:

```
man checkinstall
```

it does this:

>  checkinstall — generate packages by tracking installation scripts


Lots of options as well that I have personally never used :-)

                     Andrew

---

