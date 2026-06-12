---
title: "mounting problems"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-03-11
Hello there,

My problem is that when I put a USB drive into me laptop, it shows up on the desktop but when I click it it wont mount and comes up with error (something about the user doesnt have the right). The only way I can get it to mount is by typing the following:

sudo mount /dev/sda1 /media/usbdisk

Then when I open a file and modify it, it won't let me save it (it is read only).

This is a real pain and I'm sure it can't be hard to sort, I just don't know how. 

I run Kubuntu, thanks very much, Tom

---

### Post by tommy1987 on 2007-03-11
Problem Solved, I had to remove the entry which I stupidly made in /etc/fstab!

---

