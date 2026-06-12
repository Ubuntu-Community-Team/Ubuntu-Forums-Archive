---
title: "writing a device driver"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kishoredon on 2008-01-20
Hello all,

            I am very new to linux world. I am trying to write a simple driver of my own. The purpose is to  get started with writing drivers.

 Can any one please help me with this by  indicating the steps required to execute..

I am planning to start of with a simple printk  call. 

Thanks.

---

### Post by Hospadar on 2008-01-20
Hey, I don't know anything about writing drivers really, but I do know that generally device drivers in linux are implemented as kernel modules.  So that might at least give you a place to start.

---

### Post by nick_h on 2008-01-20
O'Reilly publish a book called "Linux Device Drivers" which is free to download - [link](http://www.linux-books.us/linux_general_0012.php).

---

### Post by kishoredon on 2008-01-27
thanks for the reply

---

### Post by jhenager on 2008-01-27
Usually, 'calls' are to procedures (software). Drivers are generally required by hardware devices.
In any case, even if you have previous programming experience, this isn't exactly beginner stuff.

---

