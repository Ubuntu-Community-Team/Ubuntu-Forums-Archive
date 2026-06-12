---
title: "grub stage 1.5"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by shimmybot on 2006-02-21
aaalright, i just installed ubuntu 5.10 and after i installed it, it tries to load grub... i then get the error during stage 1.5  "error 25"  now, i havn't gotten an awnser, and so i though i'd look here and see what i could find out  =)


any information is welcome  =)  lol

---

### Post by jorn on 2006-02-22
Searched Google for error 25 and found this: [http://tlug.dnho.net/?q=node/184](http://tlug.dnho.net/?q=node/184)
-Jorn-

---

### Post by shimmybot on 2006-02-22
yaaay found something   :D



problem is.... i don't have raid... o.O   :-k

---

### Post by jorn on 2006-02-22
Maybe grub can't find the place where you put Ubuntu.
Did you let grub automatically configure when you installed?
Do you use internal harddrive?
- Jorn -

---

### Post by shimmybot on 2006-02-22
hmm... i think i might know what the problem is...:-k 


i'm gonna re-install and this time i'm going to pay attention to where the partitions are going XD

---

### Post by Iowan on 2006-02-22
I searched for "grub errors" and found [THIS]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors").

---

### Post by NewbieNik on 2006-04-04
New install of Dapper flight 6 and I got the same error. After fixing MBR in windows and rebooting, a scan of the hard drive Ubuntu was installed on showed multiple errors.
Error 25 looks like its caused by GRUB not being able to read the Ubuntu install properly. Is this the general feeling or am I missing something glaringly obvious like an elephant in a yellow coat?

---

