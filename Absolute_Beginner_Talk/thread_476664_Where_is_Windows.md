---
title: "Where is Windows?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by odyssey41 on 2007-06-17
Windows alternative disappeared from the dual boot menu. How can I restore it?

---

### Post by Benbow on 2007-06-17
I wish I could answer this, I have exactly the same problem.

---

### Post by plcdfa on 2007-06-17
Ok, you'll need to edit /boot/grub/menu.lst . You can do this by typing:
```
gksudo gedit /boot/grub/menu.lst
```
Or if you have KDE:
```
kdesu kate /boot/grub/menu.lst
```
Scroll to the bottom of th file and add these lines:
```
title		Windows XP Professional
root		(hd0,1)
makeactive
chainloader +1 
```
The title can be anything really, so if you have Vista then name it so. The second line should be root (hdx,y), where x is the number of the winchester you have windows on (0 means the first, 1 the second and so on,) and y the number of the windows "c:" partition on the given disk. (Similarly 0 the first, etc.) Then save the file, reboot, and voila. :)

---

### Post by coffeecat on 2007-06-17
> **plcdfa said:**
> where x is the number of the winchester you have windows on


**plcdfa**, you've made my day. I haven't heard of a hard drive being referred to as a Winchester since about - oh - 1993. <nostalgia-mode> sigh! </nostalgia-mode>

:wink:

---

### Post by w4ett on 2007-06-17
> **coffeecat said:**
> **plcdfa**, you've made my day. I haven't heard of a hard drive being referred to as a Winchester since about - oh - 1993. <nostalgia-mode> sigh! </nostalgia-mode>

:wink:

That is about as good as "load"  *.*,8,1  LOL 8)

---

### Post by plcdfa on 2007-06-17
> **coffeecat said:**
> **plcdfa**, you've made my day. I haven't heard of a hard drive being referred to as a Winchester since about - oh - 1993. <nostalgia-mode> sigh! </nostalgia-mode>

:wink:

Hey, come on, we still use this word here in Hungary. I didn't realise it's not fashionable in english  anymore. Does it mean I'm not **COOL**??? I think I'll go and hang myself. :cry::cry::cry:;)

---

### Post by w4ett on 2007-06-17
> **plcdfa said:**
> Hey, come on, we still use this word here in Hungary. I didn't realise it's not fashionable in english  anymore. Does it mean I'm not **COOL**??? I think I'll go and hang myself. :cry::cry::cry:;)

Just haven't heard it in awhile....LOL......takes me back to the good old days of CP/M and my Kaypro with 8 inch floppies.  It's good to hear it again.

---

### Post by coffeecat on 2007-06-17
> **w4ett said:**
> takes me back to the good old days of CP/M and my Kaypro with 8 inch floppies.  It's good to hear it again.

When I hear the word "Winchester" I think of something about the size of a cathedral and which has a storage capacity measured in - wait for it - MEGAbytes! :shock: :lol:

**Edit**: **plcdfa**, I hope I didn't hurt your feelings. It's good to hear that the word is still used outside of the anglophone countries. :)

---

### Post by plcdfa on 2007-06-17
No problem.:)  In fact we also use the  loan-translated form of hard drive ("merevlemez" in Hungarian,)  but it counts a bit offical or scholastic, in common language winchester (or the abbreviated form "vinyó") is still more widely used. Free Hungarian lesson is over. :p

---

