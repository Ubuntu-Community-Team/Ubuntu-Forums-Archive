---
title: "Dual boot, problem"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by vligu on 2008-03-01
Hello,
well im a new bie to Linux and i just installed Ubuntu 7.10 at a 2GB RAM, AMD 3800+ 64bits machine. I have now a dual boot machine one of those OS is win xp pro. Since i installed ubuntu i cant see my win xp pro partition. It seems that it doesn't recognize it. I use a reifers file system to ubuntu. So i can't access win xp pro from ubuntu neither to see that partition. I have been a linux user before and i had ubuntu 6.10 and everything was perfect. I was able to access win xp pro before, offcourse not to write on it but read only. Can anyone pls help me?
Thanks for any help!

---

### Post by wolfen69 on 2008-03-01
what version of ubuntu are you using?

---

### Post by Baelari on 2008-03-01
go to /root/boot/grub/menu.lst, scroll down to the bottom, copy one of the sets of text, replace the title with whatever you want it to say, and change the second number in the parenthesis to the one that represents windows xp.

I have no clue how to find that, so I usually just start with 0 and go up until I hit it. annoying and inefficient, but it works

Edit, I think I got the question wrong. that works for making it have the option to use windows when you boot up. I have no clue how to make it read the windows partition from within ubuntu. I'm new to linux too

---

### Post by vligu on 2008-03-01
well Ubuntu 7.10. I have been using b4 ubuntu 6.10 and the win partition was automatically detected (read only mode) but now i cant see anything.

---

