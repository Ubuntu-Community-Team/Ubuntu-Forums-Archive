---
title: "help my as a newbies"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by mukh_86 on 2006-02-21
i had 2 problem...

1)i cant play mp3,avi,mpeg files...
  it show like this...

  [[IMG]http://img50.imageshack.us/img50/1624/screenshot5ej.th.png[/IMG]](http://img50.imageshack.us/my.php?image=screenshot5ej.png)

2)if i open 5tab or more....the firefox will close automatic..why?

anybody can help me?:D

---

### Post by codejunkie on 2006-02-21
try automatix it will let you install the required codecs to play multimedia files and install the latest version of firefox which might fix your problems.
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by mukh_86 on 2006-02-21
thx.

after i run the code in terminal..what should i do?

wget [http://www.fuckbirdflu.com/automatix/automatix_5.4-3_i386.deb](http://www.fuckbirdflu.com/automatix/automatix_5.4-3_i386.deb)
sudo dpkg -i automatix_5.4-3_i386.deb

then?

---

### Post by meborc on 2006-02-21
The automatix is probably now installed... try looking through your menues on the upper left corner of your screen... sorry, i'm not @ my ubuntu box, so i can't be sure, where the automatix is located... but it is there somewhere :)

---

### Post by mukh_86 on 2006-02-21
the automatrix install already?
what sholud i search in the right button?

how can i install codecs?

sorry...im newbies~

---

### Post by rudiz on 2006-02-21
try this:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)

---

### Post by rudiz on 2006-02-21
remove totem-gstreamer and install mplayer 

sudo apt-get install mplayer-586 mplayer-fonts mozilla-mplayer

an the codecs

dont use automatix

---

### Post by Perfect Storm on 2006-02-21
You can start automatix with **Applications** tab ---> System Tools
or write this in ther terminal:
```
Automatix
```

---

### Post by mukh_86 on 2006-02-21
wow...thx..i can listen to mp3 now.
still find out for the code and mplayer.

thx for teaching me as a newbies.

actually....i dont know wat automarix work....what the function...can anybody explain in simple words?\\:D/

---

### Post by Coelocanth on 2006-02-21
Automatix is basically an install package that grabs a ton of the most popular programs and installs it automatically so you don't have to do it all individually. I decided to forego using it, as I wanted to learn how to do it myself, but it seems like a pretty slick program.

[Click Here](http://www.ubuntuforums.org/showthread.php?t=114251) for more info about Automatix.

---

### Post by mukh_86 on 2006-02-22
so is same like yum?

can u all suggest a good codes i can find?
still have problems with that.

---

### Post by Perfect Storm on 2006-02-22
> so is same like yum?

No, it's just a installing script, if you want something like yum ubuntu have synaptic package manager (System ---> Adminstration ---> Synaptic package manager)

> can u all suggest a good codes i can find?

Not sure what you mean...

---

### Post by mukh_86 on 2006-02-22
thx.

where can i get codecs besides the codecs recommend in this thread?

---

### Post by mukh_86 on 2006-02-22
now i can watch the movie.very happy.

next question...how can i create webpage using nvu?seems very new to me.

2)where can i upload my video?
3)can ubuntu do buffer overflow?can anyone teach me?

---

