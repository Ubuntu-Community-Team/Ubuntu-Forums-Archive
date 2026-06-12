---
title: "Slow desktop performance"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-15
Is there any way to speed up the perfomance of my desktop? Some hidden tweaks somwhere? Ive used other distributions that are considerably faster on the desktop.

For example, my terminal takes 4 seconds to load, and 2 seconds every time after that. Other distros i have used, the terminal is up in like .5 seconds after i click the icon. Other distros my filemanager is up almost instantly, on ubuntu it takes like 1.5-3 seconds to open.

I cant imagine they are automagically faster, theres gotta be something i can tweak to kick things up a notch. Perhaps a config file or something....

BTW my system is a Pentium4 2.6ghz and 1024mb ram.

---

### Post by aysiu on 2006-03-15
Your profile says you're using Xubuntu.
So you're getting slow desktop performance even with XFCE?

---

### Post by dermotti on 2006-03-15
The XFCE doesnt seem any faster than gnome or KDE. 

I like XFCE's layout much better than both KDE and Gnome. Thats why im using it.

But im assuming everyone else who uses Ubuntu is having the same response times as i am getting, im using a vanilla xubuntu server install.

Unless the server install is missing a "desktop acceleration" package or has dedicated more resources to background services instead of forground services...

---

### Post by aysiu on 2006-03-15
Something's wrong.

XFCE is almost always faster than Gnome and KDE.

Maybe you have the wrong kernel or need some kind of hardware acceleration? I don't know much about that kind of stuff, but others here do.

---

### Post by dermotti on 2006-03-15
Well i was on breezy, and upgraded to dapper, performance stayed the same. Ive had the 2.6.12 breezy kernel and multiple 2.6.15 kernels installed and it didnt make much of a difference. Im using a nvidia 6200 vid card with nvidia-glx drivers from ubuntu....

---

### Post by aysiu on 2006-03-15
Again, I don't know much about all this stuff, but I know, for example, that there's a special kernel (k7) just for AMD processors.

---

### Post by taurus on 2006-03-15
Are you using just i386 kernel or SMP kernel?

---

### Post by dermotti on 2006-03-15
i686 kernel

---

### Post by patrick295767 on 2006-03-16
hi, 
  
Did you try fvwm ? 
```
apt-get -f -y install fvwm
```
  
That's my favourite in terms of fast pc. I used it for an old pc, and got better results than xfce ...

---

### Post by _simon_ on 2006-03-16
[QUOTE=dermotti]

But im assuming everyone else who uses Ubuntu is having the same response times as i am getting, im using a vanilla xubuntu server install.

[/QUOTE]

Nope, it's there as soon as I click on it! I'm using Breezy with Gnome.

---

### Post by atoponce on 2006-03-16
[quote=patrick295767]hi, 
  
Did you try fvwm ? 
```
apt-get -f -y install fvwm
```   
That's my favourite in terms of fast pc. I used it for an old pc, and got better results than xfce ...[/quote] He isn't using old hardware, though.  He has a fast processor with loads of RAM.  There should be no reason why everything isn't snappy.  He shouldn't have to resort to fvwm or xfce to get speed increases.

---

### Post by taurus on 2006-03-16
I agree.  I have a P4 3.0GHz with 1GB of RAM (using SMP kernel) and Gnome flies.  There is no reason his machine is so slow unless there is something misconfigured!!!

---

### Post by _simon_ on 2006-03-16
Unless it's hardware related e.g. overheating CPU?

---

### Post by Lord Illidan on 2006-03-16
Is DMA enabled?
Check it : ```
sudo hdparm /dev/hd*
``` and post results here. Check here, also : [https://wiki.ubuntu.com/DMA?highlight=%28Dma%29](https://wiki.ubuntu.com/DMA?highlight=%28Dma%29)

Also, check which processes are taking up a lot of processor time and memory, by using ```
top
``` in a terminal, or running System Monitor from a GUI.

---

