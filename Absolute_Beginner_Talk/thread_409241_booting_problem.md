---
title: "booting problem"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-04-14
hi there,
              After a recent software update on my ubuntu i cant seem to boot up???!!!
I get the following error:
                                     /bin/sh:can't access tty; job control turned off

how do i resolve this issue?

---

### Post by Akrit on 2007-04-14
I have meet this problem before,and it turn out that there is something wrong with my menulist.lst.
You know in the menulist.lst there will item like this:
kernel		/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro  splash locale=zh_CN
 vga=792

So ,your root part partition may be changed .Check you root partition number and change[FONT="Arial Black"] root=[/FONT]  as your partition

It may help.Good Luck!

I'm sorry that my English is so poor,but I'm trying to improve it.:D

---

### Post by wannabuntu on 2007-04-14
Thanks Akrit,
                    Yeah I think you're definitely right...thanks for your help will try it out! Your english seems fine to me.
cheers

---

