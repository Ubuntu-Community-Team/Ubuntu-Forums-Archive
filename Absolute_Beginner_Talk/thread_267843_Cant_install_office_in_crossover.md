---
title: "Cant install office in crossover"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by l @ l o on 2006-09-29
hi,

i've just installed crossover,i need it for using outlook, but i cant install any windows software.

all version i ever tried, they dont works

[IMG]http://i3.photobucket.com/albums/y64/lalog82/tmp1.jpg[/IMG]

same error i get when i try to install for example windows xp

what can be?

thanks in advance

---

### Post by shoot2kill on 2006-09-29
what does the installation log say..?

---

### Post by dcherryholmes on 2006-10-29
Probably that the permissions on (for me) /dev/.tmp-22-0 need to be set world-readable.  It already is world-readable, but I give the script permission to change it.  It just loops like that, giving the same error and trying to set permissions.  

If you tell it to continue installing and ignore the errors, it looks like it works (I'm in the middle of installing as we speak).

---

### Post by andrinho on 2006-10-30
Hi!

I've got the same problem (/dev/.tmp-22-0). And when I klick on "continue despite error" it seems like it would install the programs, but eventually fails. Any idea?

---

