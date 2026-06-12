---
title: "Screen resolution resolved !!!"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-06
I was fighting with my console being much smaller than my screen, with about a 2 inch border all around. The usual tricks didn't work at all (xserver-xorg reconfigure). So I took a chance and tried this:

[https://wiki.ubuntu.com/LaptopSmallConsole?...ocumentation%29](https://wiki.ubuntu.com/LaptopSmallConsole?...ocumentation%29)

Worked like a champ. Screen is perfect! What I didn't know was what my favorite text editor was, since I had no friggin clue what that meant. So after step 2, type in **sudo gedit**. Then add the vga=791 text after **both** /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash entries. 

Thanks again to everyone that helped!!!

---

### Post by TheFourElements on 2006-05-06
^^Is that just for laptops. I have a 17 desktop monitor and about a half inch border around my screen that I would like to get rid of.

---

### Post by bt224 on 2006-05-06
Pretty sure it only applies to laptops, but not certain. Sorry.

---

