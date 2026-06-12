---
title: "Dual Moniter Help Please!"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by blackmajik2021 on 2007-05-08
i really really need some help figuring out how to get both my monitors to work individually. Right now they're both working, but the 2nd monitor is simply a clone of the first. Ive searched for the last two days on numerous websites and on a bunch of topics here on how to get it working. Ive found a few methods that i want to try, but im too much of an ubuntu noob to even follow the tutorials on how to use these methods. Im using an ati x850, and ive heard that the x series has been buggy in fawn so im not to thrilled about that. I really cant stand having one monitor, its so hard when going back from two, it literally cuts my productivity in half. If someone could help me i would REALLY appreciate it .

thanks so much

---

### Post by Happy_Man on 2007-05-08
Could you post a link to one of these howto's you wanted to try? One of us could translate them into english for you then. ;)

---

### Post by blackmajik2021 on 2007-05-08
[http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86)

---

### Post by Happy_Man on 2007-05-08
First, open up a terminal (Applications --> Accessories --> Terminal) and type:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
gksudo gedit /etc/X11/xorg.conf
```

Scroll down to the end and type this in:
> Section "ServerFlags"
  Option "Xinerama" "true"
 
EndSection

And see if that works. Remember to save after editing, and then restart X by pressing ctrl+alt+backspace.

---

### Post by blackmajik2021 on 2007-05-08
you broke my ubuntu! :[ now i cant even start it up. the farthest i can get to is to an all text version of ubuntu where it looks kinda like dos. at this point it asks me for my username and pass and i log in but it stays at the prompt. the error i get before all of this happens is like "failed to start x server it is not set up correctly". do i need to re-install ubuntu?

---

### Post by blackmajik2021 on 2007-05-08
can anyone help me? i cant even get on

---

### Post by Happy_Man on 2007-05-08
yeah, when it shows:
```
blackmajik@black-home~:
```

Simply enter:
```
 cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

And then press ctrl+alt+backspace. it'll put you right back where you started, but oh well. Them's the breaks.

---

### Post by blackmajik2021 on 2007-05-08
someone else told me to do that and nothing happend, wierd. do caps matter?

---

### Post by blackmajik2021 on 2007-05-09
i typed that in EXACTLY with case sensitivity and all and i keep getting "no such file or directroy"

am i supposed to type in

cp/etc/X11/xorg.conf_bak /etc/X11/xorg.conf

or am i supposed to type in

cp/etc/X11/xorg.conf_bak

then press enter

/etc/X11/xorg.conf

then press enter again

also, i did it both ways, about 10 times and every time i get "no such file or directory", but when i ask for the diagnosis it tells me the error is in that location(xorg.conf). I really really dont get why this is not

---

### Post by Happy_Man on 2007-05-11
No, you type:

```
cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

There are spaces between cp and /etc and between bak and /etc...got it?

Also, if that doesn't work, type this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

