---
title: "deleting folders and files"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-06-14
using 
          Linux ubuntu 2.6.20-15-server 
with
          SSH Secure Shell 
and
           SSH Secure File Transfer

ive been using  the ssh  file transfer  program  .  When it comes to  deleting a folder i have to  delete everything inside before it will actually delete  , but its not very  good when theres loads inside  each other , anyone  have  a solution to  this  little problem ,  THANKS VERY MUCH GUYS

---

### Post by Rocket2DMn on 2007-06-14
Try
```
rm -r /path/to/directory
rmdir /path/to/directory
```
This deletes everything recursively then removes the folder

---

### Post by doughardy on 2007-06-14
thx very much rocket :p

---

### Post by ggaaron on 2007-06-14
rm -dr directory
works too, and it is a single command, you can also use
rm -drf directory
this won't ask about anything, just delete, you can also just use mc and F8 I think=)

---

