---
title: "Kernel questions"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by pinga on 2007-09-12
Hi, I'm pretty new with Linux. Although I've learned some basic commands and stuff, I still can't do some basic things. I have two questions about kernel:

1 - (easy one) My kernels have wrong information on them, and I know how to change them to properly boot. The problem is, the changes don't get saved, so every time I restart the computer, I get the message "error 15: file not found", so I have to change a line every time. How do I get to save the changes I make?

2 - As of now, I have two kernels: 2.6.20-15 and 2.6.20-16. 15 works fine, but when I boot using 2.6.20-16, I don't get internet access. How do I fix this kernel? Or should I just use the older one since it's working?

Thank you!

---

### Post by SOULRiDER on 2007-09-12
1) Press alt + f2 and type:
```
gksu gedit /boot/grub/menulst
```
If you edit the lines there the changes will be permanent so you wont have to edit GRUB every time you reboot.

2) Im not really sure about this one actually, it may be that soem module is not loading. Lets hope somebody can answer the question for us :)

If you have any other questions just ask :)

---

### Post by rsambuca on 2007-09-12
A little typo in there!  There is a period in menu.lst: ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by pinga on 2007-09-12
thanks SOULRIDER! 
So far, the older kernel is working, well, pretty fine... (still haven't gotten my cdrw/dvd drive to work...), but hopefully, as you said, we might get an answer.

---

### Post by SOULRiDER on 2007-09-13
> **rsambuca said:**
> A little typo in there!  There is a period in menu.lst: ```
gksudo gedit /boot/grub/menu.lst
```

Thanks for that, I try to be as careful as possible but I tend to make a big number of typ0s.

---

