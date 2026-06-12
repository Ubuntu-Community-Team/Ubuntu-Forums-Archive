---
title: "update manager/apt-get EXTREMELY slow"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by doubleuicked on 2007-04-21
hey guys

my internet browser works fine, but when im trying to get apps im downloading at like 12 kb per hr

does anyone know why?


cheers

---

### Post by Pobega on 2007-04-21
Try another mirror, and post the output of

```
cat /etc/apt/sources.list
```

---

### Post by halitech on 2007-04-21
I was having the same issue after an upgrade to fiesty. I changed from the Canadian mirror to the main one and it works alot better.

---

### Post by doubleuicked on 2007-04-21
how do i go by choosing another mirror?

---

### Post by halitech on 2007-04-21
open synaptic and then go settings - repositories and in the middle where it says download from, change it to main server or a location closer if listed.

---

### Post by doubleuicked on 2007-04-21
wow, its a LOT faster now

thanks so much!

---

### Post by codingmaster on 2007-04-21
Hello!

You can choose an other mirror using synaptic.

You can also edit /etc/apt/sources.list

sudo gedit /etc/apt/sources.list

Change: [http://XY.archive.ubuntu.com/ubuntu/](http://XY.archive.ubuntu.com/ubuntu/)

to a mirror close to your location, e.g:

[http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/)

Also check for some addtional mirror locations:
[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

Best regards, Georgy Berdyshev

---

### Post by doubleuicked on 2007-04-22
thanks guys!! 

now im just having trouble with my sound, and i trying to read and read to get that fixed

---

### Post by codingmaster on 2007-04-22
Hello!

Opening a new thread is a way to get help, when you will not know at all!

Best regards, Georgy Berdyshev

---

