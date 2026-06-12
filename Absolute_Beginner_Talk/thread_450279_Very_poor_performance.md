---
title: "Very poor performance"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Otustelija on 2007-05-21
I just installed Ubuntu on my laptop (Celeron 833Mhz 128 RAM), and it is very slow.

I had Debian on the same computer earlier and it run very smoothly. First I checked that the settings for the graphics adapter in xorg.conf were correct, but they were exactly the same as the ones I used with Debian.

System Monitor shows 32 processes that take a total of less than 30 MB, but at the same time 90MB User memory and 114 MB swap are used. Even  after not touching the computer in 15 minutes the load average is 30-40%.

What takes up all the memory? Where should I look next for the problem?

Edit: I'll post any information, just no idea what might be needed.

---

### Post by Kobalt on 2007-05-21
A good way of knowing what's going on in your system is to use htop. You can install it this way ```
sudo apt-get install htop
```
I like it more than top actually...
Anyway : Ubuntu comes with such things as Network-Manager installed/enabled by default and some other accessibility tools that Debian doesn't install by default. This is a possible lead. 
Even though, especially on my laptop, Debian has always been a little bit snappier than Ubuntu if I compared them straight after a fresh install.

---

### Post by Otustelija on 2007-05-21
Thanks, I'll see what htop reports.

I'd understand "a little bit snappier", but I find it next to inpossible to do anything now. Opening file manager takes ages. Haven't dared to try opening OpenOffice yet...

---

### Post by Kobalt on 2007-05-21
On such a config as yours I'd go with XFCE or OpenBox actually, not Gnome or KDE.

---

### Post by ruy_lopez on 2007-05-21
128mb isn't a great deal of RAM. You could try disabling some of the services that aren't necessary. Disable things like Beryl and Compiz if your running on low memory. But, if I were you, I'd look into getting more RAM, putting in at least an extra 512mb should give a good improvement. You can also try "sudo apt-get install sysv-rc-conf" for a simple way to disable start-up items. Just be sure you know what you are disabling before you do it. The url below has some good advice.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by heimo on 2007-05-21
Also this recent thread has some suggestions for lightweight apps:
[http://ubuntuforums.org/showthread.php?t=447007](http://ubuntuforums.org/showthread.php?t=447007)

---

### Post by kakk on 2007-05-21
Check if you have swap correctly enabled. I have seen problems with swap in ubuntu, You can check it with top or htop.

---

### Post by stefaan.dutry on 2007-05-21
> **Otustelija said:**
> 128 RAM

The minimum to run the live CD is 256 MB RAM so I think you're just short of RAM (having 128MB ram would require 128MB swap) not great at all.

---

### Post by Otustelija on 2007-05-21
> **stefaan.dutry said:**
> The minimum to run the live CD is 256 MB RAM so I think you're just short of RAM (having 128MB ram would require 128MB swap) not great at all.

Yeah, had to use the alternate cd to get install work.

The problem is I don't have an internet connection on that machine. Otherwise I'd have installed the mini image, and add only stuff I need. Now selecting stuff that's not on the cd is kinda difficult.

Is it possible to burn a larger collection of software on cds like in Debian, where there's over ten cds with anything you might need?

Or maybe I should choose a lighter Linux? Any suggestions?

---

### Post by freebeer on 2007-05-21
I suspect a lighter distro is your best bet.  I can't offer a suggestion there, as I don't have any experience in them.  FYI, I installed 7.04 on a desktop with similar specs...  Celeron 733 Mhz but with twice the ram.  I found it slow, too.  Usable (with GUI) but slow.  I didn't expect otherwise, though.

---

### Post by houstonbofh on 2007-05-21
The best tuner guide I have found. [http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/)  Some of the stuff he has installed on makes you system seem fast!

---

### Post by Kobalt on 2007-05-21
This one is for Edgy, but you'll find another one for Feisty K.Mandla has made before stopping (snif...) his blog activity.

---

