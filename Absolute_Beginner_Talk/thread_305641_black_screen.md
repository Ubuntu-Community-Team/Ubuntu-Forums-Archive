---
title: "black screen"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by ercerd on 2006-11-23
firstly sorry for my poor english.

i've ubuntu 6.10 installed with radeon 9550 video card.

i've messed up the driver of video card, wine, cedega and some other programs. And now when i try to run xawtv or xmame or kmame i get an black screen and have to ctrl+alt+backspace and restart gnome.
May this issue be related with the driver thing?](*,)

---

### Post by jonesyp on 2006-11-23
Try looking at

[http://ubuntuforums.org/archive/index.php/t-76147.html](http://ubuntuforums.org/archive/index.php/t-76147.html)

---

### Post by ercerd on 2006-11-23
> **jonesyp said:**
> Try looking at

[http://ubuntuforums.org/archive/index.php/t-76147.html](http://ubuntuforums.org/archive/index.php/t-76147.html)

thanks for reply but that is not my issue. my video card recognized and 3d acceleration working. i can play some 3d games. but when running xawtv or x/kmame i get whole screen black.

---

### Post by unarmedninja on 2006-12-10
I have the same problem. I have 3d acceleration working with my ati x800 but when i type xmame in the command or use gxmame the screen goes black and i have to restart gnome to fix it.  anyone have any ideas?

---

### Post by cor2y on 2007-01-14
Heres the solution i found from this [post](http://www.ubuntuforums.org/showpost.php?p=600299&postcount=7)

Anyhow here it is first install xmame-sdl, tools and common
so thats 
> 
sudo apt-get install xmame-sdl xmame-tools xmame-common



next download and install the beta version of gxmame or kxmame if you desire a frontend 
> 
wget -c  [http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb](http://surfnet.dl.sourceforge.net/sourceforge/gxmame/gxmame_0.35beta2-1_i386.deb) 


Now before running xmame or gxmame do this

> 
xmame --showconfig > ~/.xmame/xmamerc


Now run your frontend or xmame from the terminal
No more black screen.

I am using Ubuntu Edgy.

---

