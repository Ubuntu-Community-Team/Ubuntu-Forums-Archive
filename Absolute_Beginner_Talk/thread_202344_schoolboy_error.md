---
title: "schoolboy error?"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by stealthisuser on 2006-06-23
hello

having difficulties installing ubuntu. i have 2 hard drives: 20gb with windows xp and 80gb that was formatted in windows but was empty.

ran the cd. no probs. tried installing linux on hdb and letting the install program setup the partitions for me but it doesn't seem to be able to boot. the boot screen says that it's loading grub and then 'error 21' after which nothing happens. when i booted ubuntu from the cd hdb showed up as 'inaccessible'.

any ideas as to what's gone wrong and how i can fix it?

also, i'd really like to be able to at least get windows up and running again whilst i sort this out. how can i get my computer to boot windows?

cheers

dan

---

### Post by ajifans on 2006-06-23
error 21 happens because the BIOS cannot find the selected hard disk.

Firstly:  double check the power/IDE connections (sorry sounds dumb, but that was the problem for me :rolleyes:)
 
Secondly: check your BIOS settings.

Thirdly: have a browse of the following links:

[http://www.ubuntuforums.org/showthread.php?t=200187&highlight=grub+error+21](http://www.ubuntuforums.org/showthread.php?t=200187&highlight=grub+error+21)

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

[http://www.mepis.org/node/5782](http://www.mepis.org/node/5782)

[http://www.linuxquestions.org/questions/showthread.php?threadid=338856](http://www.linuxquestions.org/questions/showthread.php?threadid=338856)

[http://www.ubuntuforums.org/showthread.php?t=193709&highlight=grub+error+21](http://www.ubuntuforums.org/showthread.php?t=193709&highlight=grub+error+21)

---

### Post by stealthisuser on 2006-06-23
cheers ajifans

> Firstly: double check the power/IDE connections (sorry sounds dumb, but that was the problem for me )

will check

> Secondly: check your BIOS settings.

uhuh

> Thirdly: have a browse of the following links:
[http://www.ubuntuforums.org/showthre...=grub+error+21](http://www.ubuntuforums.org/showthre...=grub+error+21)
[http://lists.gnu.org/archive/html/bu.../msg00082.html](http://lists.gnu.org/archive/html/bu.../msg00082.html)
[http://www.mepis.org/node/5782](http://www.mepis.org/node/5782)
[http://www.linuxquestions.org/questi...hreadid=338856](http://www.linuxquestions.org/questi...hreadid=338856)
[http://www.ubuntuforums.org/showthre...=grub+error+21](http://www.ubuntuforums.org/showthre...=grub+error+21)

thanks for the links. a lot of the terminology is shooting way over my head at the mo' but i'll come back if i haven't got a solution

---

### Post by ajifans on 2006-06-23
If none of the above links help, search the forum with 'Grub Error 21' and it'll bring up lots of threads.

---

### Post by Iowan on 2006-06-23
Here's more than you wanted to know about GRUB errors:
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html")

---

