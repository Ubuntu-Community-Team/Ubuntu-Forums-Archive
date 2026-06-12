---
title: "Dual Booting (different machines)"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by slushpuppy on 2007-12-07
Hi,
  I have noticed that this was posted before in the forums but didn't have any replies. I installed Ubuntu into a external harddrive from a desktop computer. I managed to run everything smoothly until I decided boot into my external harddrive from a different machine(laptop). Even when i selected the normal ubuntu boot, I get thrown into command line. I did some research and I was informed about Ubuntu not being able to recognise new machine drivers. I am running a vista machine on the laptop

    My question is, if i am right, how am I able to configure ubuntu to recognise the new drivers. I prefer if I could boot ubuntu from both computers without doing serious modifications to the configration files. 

Thank you very much.
Slushpuppy

---

### Post by gn2 on 2007-12-07
When you boot the other computer and the command line pops up log in and type:

sudo dpkg-reconfigure -phigh xserver-xorg

Or use a big flash drive: [http://tinyurl.com/2xnnp8](http://tinyurl.com/2xnnp8)

---

