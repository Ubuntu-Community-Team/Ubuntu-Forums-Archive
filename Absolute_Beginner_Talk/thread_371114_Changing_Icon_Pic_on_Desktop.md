---
title: "Changing Icon Pic on Desktop"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by genghiskhano on 2007-02-26
Hello,
I have an icon on my desktop to my windows files, I want to change the icon picture (by right clicking and going to properties)  but it gives me error " Could not save properties. You do not have sufficient access to write to /home/tico/Desktop/sda1/.directory." ,
Thanks for your help and expect more posting with several little problems I have :)

---

### Post by tronica on 2007-02-26
you need to change the permissions on that,  try

> chmod 777 directory_name_here

---

### Post by genghiskhano on 2007-02-26
I DID THIS tico@tico-laptop:~/Desktop$ sudo chmod 777 sda1
but still gives me the same error
if I do this sudo chmod 777 /sda1/.directory
I get this chmod: cannot access `/sda1/.directory': No such file or directory
either way I can't change the icon
thanks for your help:confused:

---

