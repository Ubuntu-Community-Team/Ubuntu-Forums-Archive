---
title: "how can i download and install later"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ali_hammad on 2007-06-20
Hello there

I am new to Ubuntu rather linux community, very eager to learn use ubuntu.. 

But plz tell me is there any way that i can download a software and then later on install it on another pc which may not have any internet connection or has minimum bandwidth.

If yes, then plz tell me how can i do that and from where will I find the desired software.. for example , multimedia/ mp3 players.

Thank you for your coorporation.

Ali Hammad Baig

---

### Post by buuntuu! on 2007-06-20
hi!
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/") has all the packages for manual download, but you'll have to take care of dependencies manually,
[aptoncd]("http://aptoncd.sourceforge.net/") is a program which lets you create a cd with all the stuff installed on your system, for easy sharing with boxes without internet!

---

### Post by atria on 2007-06-20
You can download packages using
```
aptitude download <packagename>
```

After that copy the packages you need from /var/cache/apt/archives

---

### Post by macsta on 2007-06-20
If you're a new to all this as I was a few weeks ago, you'll find a lot of the advice you get and the stuff you read on the net is far too advanced.   I downloaded the current version of Ubuntu with no difficulty.   When asked if you want it as data or an image choose Image.   Then when your CD is made, you can just pop it into a computer and it should boot off the CD and run Ubuntu for you without installing it in the hard disk.   The CD offers you the option to install it, so you can try it, then if you like it install it.   It offers some chance to divide your hard disk but I didn't do that, so I cant comment on whether you can keep your old operating system.   If you don't choose to divide your hard disk it reformats it for you so all previous data is lost.   I find Ubuntu really easy and nice to use, but getting intelligible info for beginners has been a problem for me.   For example I still haven't been able to get my printer working and wherever I look for info they talk to me as if I were a computer whizz.   I'm not!   Good luck.

---

### Post by buuntuu! on 2007-06-20
@ macsta: i think we are talking about additional software and installing it on a box without internet access, not the installation of ubuntu itself ;)
a very valid question by the way: when i first installed on an offline pc i nearly went crazy when i found out that i couldn't play my dvds and  mp3s out of the box but had to install restricted drivers first... aptoncd is perfect there!

---

### Post by ali_hammad on 2007-06-20
**[COLOR="Red"][SIZE="6"]aptoncd  ???[/SIZE][/COLOR]**

---

### Post by ali_hammad on 2007-06-20
ok got it :P

---

### Post by kirbyboy on 2007-06-20
Hi, aptoncd only works with cd's and dvd's?, how can i do the same with a memory stick?

---

### Post by buuntuu! on 2007-06-20
you can save an image of your packages to any media, as the [documentation]("http://aptoncd.sourceforge.net/doc-manual.html") says...

---

