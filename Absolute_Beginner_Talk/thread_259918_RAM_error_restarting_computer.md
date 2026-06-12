---
title: "RAM error restarting computer"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by kaplis on 2006-09-18
hey

i was restarting computer after system requirement after updating. the mesage came out as usual- Uncompressing linux...Ok, booting the kernel- but then appeared this one:

20.404783 RAMDISK: ran out of compressed data
20.404852 invalid compressed format (err:1)
20.406853 kernel panic- not syncing: VFS: Unable to mount root fs on unknown block (0,0)
20.406911

so, as far i understand that theres smth wrong with my RAM if it isnt dead at all??? :-\" 

tnx

---

### Post by amo-ej1 on 2006-09-18
no it has nothing to do with your physical ram, it has everything to do with your 'ramdisk'. Now what is a ramdisk ? Wikipedia has all the answers: [http://http://en.wikipedia.org/wiki/RAM_drive]("http://http://en.wikipedia.org/wiki/RAM_drive")

There is probably something wrong with  the initrd file that is tried to be loaded, can you verify it exists ? That is has the some version as the kernel ? (you can verify these from the grub prompt)

---

### Post by bigken on 2006-09-18
its not the ram chips its more to do with your hdd and its software errror not hardware ;)

---

### Post by kaplis on 2006-09-18
ok, i see.
i will check it when i will be at home;) 
tnx anyway

---

