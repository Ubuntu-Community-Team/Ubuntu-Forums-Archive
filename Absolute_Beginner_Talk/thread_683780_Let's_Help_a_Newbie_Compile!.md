---
title: "Let's Help a Newbie Compile!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-01-31
I need some help compile a Wine installer to drop all the day to a special directory.  How may I go about doing this?  I am completely new to compiling, so new.  I have never done it before.  So, please go into every step with lots of details.

I need to compile "wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb" with the specila directory in mind.

Note from mIRC:
if youre compiling from sources you can specify new dir when running configure (eg ./configure --prefix=/usr/wine-0.9.35)

How do I do that?

Thanks for any future help,
Sugi

---

### Post by jaytek13 on 2008-01-31
Well, you don't need to compile that, just install it. The .deb files are already compiled for you. Just right click on it, select open with package manager, and proceed to install.

---

### Post by emarkd on 2008-01-31
You've got a .deb there.  It's already compiled.  Just double-click it and it'll install.

---

### Post by jrothwell97 on 2008-01-31
If it's a .deb file, you should just be able to click it, and it'll extract and maybe compile.

The generic 'compile' command in Linux is

```
make install
```

but I would recommend reading the README and INSTALL files beforehand.

---

### Post by emarkd on 2008-01-31
It's a bit more complicated than that.  If you really need to compile this from source, you'll have to get the source from Wine and then read this:


    [In-depth guide including building software from source]("http://psychocats.net/ubuntu/installingsoftware")

---

### Post by jrothwell97 on 2008-01-31
Exactly: 'make install' is only a generic command which sometimes works, sometimes doesn't. Which is why it makes sense to read the 'INSTALL' file.

---

### Post by jan quark on 2008-01-31
compiling is the most complicated way to install applications
it requires the most experience

try this guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

it tells you how to install many things in ubuntu

---

### Post by Sugi on 2008-01-31
I need to install the .deb to ~/.wine-0.9.35 because i already have win 0.9.54 installed.  I don't want wine to uninstall 0.9.54 directory.  I need 0.9.35 for Warhammer 40,000.  So, how do I compile it to install to a special directory?

---

### Post by Sugi on 2008-02-05
If i install the 0.9.35 .deb from the terminal and i want it to install to a special directly.  would I type this in?:

     **code**
> dpkg -i /home/USER_NAME/Desktop/wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb ./configure --prefix=/usr/wine-0.9.35
is that corrent?

---

