---
title: "Trying to learn the terminal"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-04-30
I'm following the intructions [here]("http://www.linuxcommand.org/lts0020.php")

But when i get to the first change directory example , i fail - lol

His example:


> [me@linuxbox me]$ cd /usr/X11R6/bin

[me@linuxbox bin]$ pwd
/usr/X11R6/bin

[me@linuxbox bin]$ ls

Animate               import                xfwp
AnotherLevel          lbxproxy              xg3
Audio                 listres               xgal
Auto                  lndir                 xgammon
Banner                makedepend            xgc
Cascade               makeg                 xgetfile
Clean                 mergelib              xgopher
Form                  mkdirhier             xhexagons
Ident                 mkfontdir             xhost
Pager                 mkxauth               xieperf
Pager_noxpm           mogrify               xinit
RunWM                 montage               xiterm
RunWM.AfterStep       mtv                   xjewel
RunWM.Fvwm95          mtvp                  xkbbell
RunWM.MWM             nxterm                xkbcomp

and many more...



What i end up with:

> dallas@dallas-ubuntu:~$ cd /usr/x11r6/bin
bash: cd: /usr/x11r6/bin: No such file or directory
dallas@dallas-ubuntu:~$ 


I'm prolly missing something super obvious huh?

If there's a better place to learn the terminal please feel free to share , thanks! :)

---

### Post by Swab on 2007-04-30
/usr/X11R6/bin

note that X11R6 is upper case.

---

### Post by Sef on 2007-04-30
> dallas@dallas-ubuntu:~$ cd /usr/x11r6/bin
bash: cd: /usr/x11r6/bin: No such file or directory
dallas@dallas-ubuntu:~$

Put a ~ before /usr/, so you will end up with this: cd ~/usr/X11R6/bin

Took me a bit of time to learn that trick.

Linux, like Unix, is case sensitive.

---

### Post by Swab on 2007-04-30
> **Sef said:**
> Put a ~ before /usr/, so you will end up with this: cd ~/usr/X11R6/bin

Took me a bit of time to learn that trick.

~/ is a shorthand way of typing the path to your home directory.

---

### Post by Wiebelhaus on 2007-04-30
Lol , omg......... thanks.

---

