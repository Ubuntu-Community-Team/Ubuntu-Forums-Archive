---
title: "Asus x101ch Resolution issues.."
date: 2012-03-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by MaMaPyCb on 2012-03-28
Hello, Kinda still new to this Ubuntu thing, I have a new eee pc X101CH and it will only let me have a 800x600 resolution. I've searched online and not found a fix, so I thought I should drop in and ask. 

 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)

 xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 


If that Helps at all?!?

---

### Post by MaMaPyCb on 2012-04-01
No one has anything to help?

---

### Post by roger_1960 on 2012-04-01
Hi

Have you seen this bug?  It does not look too hopeful, but there are some interesting comments near the end of the item.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934956](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/934956)

---

### Post by MaMaPyCb on 2012-04-02
The funny thing is that its only the GUI that seems influenced, as youtube vids in HD are still in HD.

---

### Post by jazzofilus on 2012-04-03
Same problem here.... Any workaround?

---

### Post by MaMaPyCb on 2012-04-04
I'm glad I'm not the only one.........

---

### Post by pharmak0n on 2012-04-28
Same problem

---

### Post by leosanmon on 2012-05-30
I don't know if you already found the solution but this worked for me [http://ubuntuforums.org/showthread.php?t=1953734&page=2](http://ubuntuforums.org/showthread.php?t=1953734&page=2)

After that I was getting an error related to the resolution 800x600 but I fix it by deleting the monitors.xml file with the next command:

sudo rm ~/.config/monitors.xml 

Anyway just by compiling the new Kernel resolution 1024x600 works perfectly.!

---

### Post by yashoda on 2012-07-07
Guys,

just found this BRILLIANT way to solve this problem.

nothing else worked!

[http://www.upubuntu.com/2012/06/how-to-install-kernel-342-under-ubuntu.html](http://www.upubuntu.com/2012/06/how-to-install-kernel-342-under-ubuntu.html)


and magically, full resolution.  the difference is mindblowing!

---

### Post by jasonsmithmusic on 2012-08-11
Thanks Yashoda,

that has sorted me out too, but I've got another problem. no VGA or HDMI output to external monitor. I really need to sort one of these out soon. any ideas?

---

### Post by MaMaPyCb on 2012-09-10
> **yashoda said:**
> Guys,

just found this BRILLIANT way to solve this problem.

nothing else worked!

[http://www.upubuntu.com/2012/06/how-to-install-kernel-342-under-ubuntu.html](http://www.upubuntu.com/2012/06/how-to-install-kernel-342-under-ubuntu.html)


and magically, full resolution.  the difference is mindblowing!

That totally fixed everything! Thanks for the help!!!!!!!:guitar:

---

### Post by jasonsmithmusic on 2012-09-10
> **MaMaPyCb said:**
> That totally fixed everything! Thanks for the help!!!!!!!:guitar:

...but doesn't this screw up the suspend function?

---

### Post by cpbl on 2012-11-23
Yes, but there are other problems with this netbook, still as of 2012 November. My advice is to avoid it completely:

[http://cpbl.wordpress.com/2012/10/30/asus-eee-pc-x101ch-review-very-poor/](http://cpbl.wordpress.com/2012/10/30/asus-eee-pc-x101ch-review-very-poor/)

---

### Post by yashoda on 2013-01-19
Hi Jason,

I initially had problems with suspend, but with a full update, that got sorted. as did difficulty switching displays.  Use the hotkeys.

What I'm stuck with now, is sound only playing from the left speaker.  And there seems to be no way around this for now.

Otherwise, a nice netbook.  very light. no fan noise. and good battery life.

---

