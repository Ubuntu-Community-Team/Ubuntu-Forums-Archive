---
title: "Bootskin"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Europa7 on 2008-02-01
Can a "bootskin" be added to Ubuntu? I just installed it and it's taking about 3 minutes to boot and it's just a blank screen the entire time. Windows XP has a bootskin program called wincustomize [http://www.stardock.com/products/bootskin/](http://www.stardock.com/products/bootskin/)   Is there a program like this for Linux? I really like the green handprint bootskin that is used in Backtrack 2 and would like to add it if possible. Thanx

---

### Post by Het Irv on 2008-02-01
[www.gnome-look.org]("http://www.gnome-look.org")

What you are looking for are the splash screens.

To fix the booting problem go to a terminal and type:

```
sudo apt-get install bootchart
```

on each boot this program will store a chart in /var/log/bootchart
Post one of your bootcharts here so we can see what it is hanging up on.

---

### Post by airbornemist6 on 2008-02-01
> **Europa7 said:**
> Can a "bootskin" be added to Ubuntu? I just installed it and it's taking about 3 minutes to boot and it's just a blank screen the entire time. Windows XP has a bootskin program called wincustomize [http://www.stardock.com/products/bootskin/](http://www.stardock.com/products/bootskin/)   Is there a program like this for Linux? I really like the green handprint bootskin that is used in Backtrack 2 and would like to add it if possible. Thanx

O.o
You installed a windows program in linux? It shouldn't even be able to do anything. But, anyway, there are programs like what you are looking for. First of all, to make grub look better you can use gfxboot, and then to make the splash look better you can use Splashy. If I remember right, both are in the repositories and can be installed via synaptic, but you might want to look up some howtos for them as you can rather easily break things by installing them.

---

### Post by Het Irv on 2008-02-01
I just asked this question myself actually
[http://ubuntuforums.org/showthread.php?t=684024]("http://http://ubuntuforums.org/showthread.php?t=684024")

Have fun.

---

