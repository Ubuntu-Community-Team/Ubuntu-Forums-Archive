---
title: "chroot"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-30
what is command at prompt to chroot from /dev/hda3 to /dev/hda1 please
new to acess grub.conf file as have problems at bootintig into /dev/hda1.

lex1;)

---

### Post by Darkriser on 2006-03-30
i'm not sure what you mean, but doesn't "sudo vim <filename>" do exactly what you need?

---

### Post by lex1 on 2006-03-30
I do know how to acess /dve/hda1 its someonesuggested chroot - what would be the command with VIM (txt editor0?

lex

---

### Post by Darkriser on 2006-03-30
i thought you need to access (modify) the grub.conf file. this is how i understood your question. pls, explain clearly your problem....maybe we can help you...8)

---

### Post by lex1 on 2006-03-30
I cannot acess /dev/hda1 which is a linux ext3 files 

 /dev/hda3 is the device node for, the third primary partition on your first ide master hard drive     so I need to   mount /dev/hda1 /mnt/    and work in /mnt/boot/grub/        

lex1

---

