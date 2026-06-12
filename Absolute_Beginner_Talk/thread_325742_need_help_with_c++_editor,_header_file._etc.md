---
title: "need help with c++ editor, header file. etc"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-12-26
hello . i am really confuse... ok leave it . i was looking for best c++ editor and the header file. ( i.e studio.h) . so  where do i get those .h (header) file. and where do i put them?

---

### Post by po0f on 2006-12-26
pavel_kbc,

```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install build-essential[/FONT]
```
build-essential is just a meta-package for the GCC compiler, libc6-dev (which contains **stdio.h**, as well as other header files), and some other stuff.  I use GEdit for all of my programming (none of my projects are terribly large enough to where an IDE would be useful).  For future reference, post in [Programming Talk](http://www.ubuntuforums.org/forumdisplay.php?f=39) for all your programming questions.

---

### Post by pavel_kbc on 2006-12-30
Thank you. i have installed that after install ubuntu.. anyway thanks again :)

---

### Post by neowolf on 2006-12-30
```

#include <stdio.h>
#include <stdlib.h>

int main(void) {
printf("This is a test");
return 0;
}


```

Save that as test.c, then run

```

gcc test.c -o test-bin

```

See if it will compile, then if it does you know the header files are ok.
If your just learning programming I would suggest just using a text editor like GEdit (GUI) or Vim (CMD).

---

### Post by pavel_kbc on 2006-12-30
[~] ->> $ gcc testing.cpp -o test-bin
/tmp/ccMw7dY3.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

well dude its giving me error... :-s what i do now?

---

### Post by radu_chindris on 2006-12-30
You have to options:
- change the file extension from .cpp to .c
```
mv testing.cpp testing.c; gcc testing.c -owhatever
```, or 
- use g++ to compile it:```
g++ testing.cpp -owhatever
```

---

### Post by almahtar on 2006-12-30
I'm a Gnome guy all the way, but I really really like the "kate" editor that ships with KDE.  You may want to give that a shot if you GEdit doesn't do it for you.

Also, an extremely powerful editor with a steep learning curve is "vim".  Like I said: steep learning curve.  It's worth it if you're planning on spending a whole lot of time programming, but if you just program for a hobby Kate or Gedit are probably better bets for you.

Anjuta is a good IDE, but it is a bit buggy :-\  I haven't used KDevelop, but I've heard good things about it.

---

### Post by pavel_kbc on 2006-12-31
neowolf , radu_chindris thanks to you guys.... 


almahtar: i hate KDE... so i wont use kde softwares. 
can you tell me how to exit from vim ...

---

### Post by radu_chindris on 2006-12-31
pavel_kbc:
  SHIFT + : + 
q - if you simply want to exit and there are no changes which need to be saved
wq - write changes and quit
q! - quit and loose all changes

almathar:
 On windows I can't live without visual studio, especially because of the integrated debugger. On *NIX I've tried to compensate VS with kdevelop, anjuta, codeblocks and a handful of other not-so-well-known IDE-s or editors. But each one of them had it's glitches, lacking especially on the integrated debugging side. So far, emacs (with xft support) + ecb + xrefactory + gud is the most suited for me on *NIX. The best IDE/editor/etc is a matter of personal preferences/programming language/work style, thus there's no "one suits all" solution. And that's the beauty of it ;)

peace

---

