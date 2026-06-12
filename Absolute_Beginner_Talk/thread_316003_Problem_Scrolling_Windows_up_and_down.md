---
title: "Problem Scrolling Windows up and down"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-10
Almost all windows that I scroll up and down on move slowly. For example, while scrolling down the ubuntu forums page, the transition of the page start from top to bottom. 

What should I do with this?

Is ubuntu really slow with scrolling windows up and down?

---

### Post by luckyaba on 2006-12-10
Ubuntu should not be slow scrolling up and down. 

Possibly try reloading your graphics card drivers.

---

### Post by wersdaluv on 2006-12-10
I have not installed a single driver. The problem is, I can't install any driver with ubuntu. What can I do?

---

### Post by luckyaba on 2006-12-10
Has it always had this problem or did it just start happening?

---

### Post by wersdaluv on 2006-12-10
it has always been like that

---

### Post by luckyaba on 2006-12-10
What are the specs of your comp? what kind of graphics card?

---

### Post by wersdaluv on 2006-12-10
I don't know what graphics card but I know that it's 32bit and my ram is 512mb. In ubuntu, where can I see the system information?

---

### Post by luckyaba on 2006-12-10
System > Administration > Device Manager might give you some info

or typing "lspci" into a terminal without the quotes will give you a bit more.

05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0292 (rev a1)
**example of output from lspci**


[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

under the Hardware section will give you all the info you need on installing drivers.

---

### Post by wersdaluv on 2006-12-10
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
That's what I got using lspci

---

### Post by luckyaba on 2006-12-10
I think you should be ok with a generic driver then but i could be wrong.

Gedit /etc/X11/Xorg.conf and under the device section you should see something that says

Driver      "VGA"

if it does then you should have the right driver.

---

### Post by wersdaluv on 2006-12-12
If it's not a driver problem, then what can I do to improve scrolling up and down?

---

### Post by wersdaluv on 2006-12-14
I have just installed Kubuntu in this laptop where I had problems scrolling up and down with Ubuntu and noticed that there is no problem scrolling up and down. 

I believe that all drivers and all other applications installed in Ubuntu are installed in Kubuntu as well, which makes me think that the problem is not with the graphics card driver.

What can I do to fix this?

---

### Post by wersdaluv on 2006-12-20
I believe that gnome should run a bit faster than KDE but scrolling up and down is only slow with my ubuntu desktop. Whenever I use Kubuntu, scrolling up and down go smoothly. 

Why is it the case?

---

### Post by saisrujan on 2006-12-23
Hi,

I have an AMD64 with on-board-GPU-Mobo NVIDIA® GeForce&#8482; 6100 and NVIDIA nForce&#8482; 430 chipset. I find the scrolling speeds to be too low on Ubuntu 6.06. It has always been that way. It works fine when scrolling up/down slowly, but when i scroll fast (to reach the bottom of a page etc) then its really slow - as slow as working on a remote system sometimes. 

Any help to improve the situation here? 

Thanks,
Sai

---

### Post by saisrujan on 2006-12-24
I realized I was using vesa drivers. I downloaded nvidia-glx drivers and the problem is solved.

I should have done my home-work before posting

---

