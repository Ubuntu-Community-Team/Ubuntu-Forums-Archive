---
title: "Problem in booting fron kubuntu CD"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by doronb2 on 2007-06-12
hello,
After a month i'm having ubuntu in my Virtual Box from windows, i decided to install Kubuntu in a dual boot.
when the cd is loading i'm trying to install the cd but after i'm pressing "install kubuntu" or even "check cd for defects" i see a lot of program lines and in the last of them is written - 
"<a word that i don't remember> kernel: trying to kill init!" (or something like that)
 and in that point the computer stuck, i cant do even ctrl-alt-del.
(i checked the cd in a new boot from my virtual box from windows and it worked fine)

WHAT CAN I DO??   :confused:

---

### Post by doronb2 on 2007-06-12
anyone?????

---

### Post by doronb2 on 2007-06-12
added a screenshot...

PLEASE HELP..

[IMG]http://img511.imageshack.us/img511/3507/picxq3.jpg[/IMG]

---

### Post by doronb2 on 2007-06-13
:(

---

### Post by doronb2 on 2007-06-13
i tried the Alternative version but the same result.. :(

---

### Post by bbarcelo on 2007-06-13
Don't know what the policy is here on linking to another forum but since all knowledge should be free.. [Here's a good description along with some possible causes to this problem]("http://www.linuxquestions.org/questions/showthread.php?t=353920").

In summary, your IDE controller might be faulting.

---

### Post by doronb2 on 2007-06-13
> **bbarcelo said:**
> Don't know what the policy is here on linking to another forum but since all knowledge should be free.. [Here's a good description along with some possible causes to this problem]("http://www.linuxquestions.org/questions/showthread.php?t=353920").

In summary, your IDE controller might be faulting.

ok.. i read there.. 
there is something i can do??

---

### Post by doronb2 on 2007-06-13
ok. now we're getting somewhere.

after i added PCI=off (with noapic...) as parameters i see the Kubuntu logo for 5 seconds and then the i see again command lines:
"/bin/sh : can't access tty : job control turned off
(initramfs)"

and after this (initramfs) i can enter command (that i can see by typing "help".

anyone know how can i proceed from here??

---

