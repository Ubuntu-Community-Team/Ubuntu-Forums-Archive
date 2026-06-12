---
title: "3 hsdpa"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by pps80 on 2008-04-19
Hi guys i want to make my 3 hsdpa working on linux i found a web page [http://oozie.fm.interia.pl/pro/huawei-e220/index.html](http://oozie.fm.interia.pl/pro/huawei-e220/index.html)
you can download a installer package from this also it tells you few commands to use
But my problem is using this command 
I tried putting it in terminal window and it said package not found.
i am new to linux and so have very little knowledge about it. 
Can some on please help me how can i execute this commands and to open this package.
and do i need to keep this package in a particular place or what???
thanks in advance

---

### Post by warbread on 2008-04-19
First of all, understand that this is not an official package that is being officially maintained in the official repositories.  This doesn't **necessarily** mean you're infecting your computer with malware, but consider this a warning.  Unsupported software can lead to bad things.  At the very least, it won't update itself.  

What you need to do, per the instructions, is to first download the file he220stat.tar.bz2.  Then:

```
$ tar xjvf he220stat.tar.bz2
$ cd he220stat*
$ ./configure
$ make
$ sudo make install
$ sudo xhe220stat
```

According to the website, this will get your modem working.

---

### Post by scorp123 on 2008-04-19
Please see this thread:
[http://ubuntuforums.org/showthread.php?t=609534](http://ubuntuforums.org/showthread.php?t=609534)

Huawei E220 modems will most likely work "out of the box" on Linux without any special software whatsoever. You just have to give it the right commands and it will happily connect to your provider.

I myself have a Novatel MC950D and it too "just works". As I said ... please see the thread above.

---

### Post by pps80 on 2008-04-19
Hey scorp... u r the best... make it work... thanks a lot 
One more question if u dont mind please
how to disconnect my usb modem and is there any way i can get data usage as well
Really appreciate your help... waiting for your reply now i dont have to go back to windows to check you comments can check here in ubuntu...... huray:guitar:

---

