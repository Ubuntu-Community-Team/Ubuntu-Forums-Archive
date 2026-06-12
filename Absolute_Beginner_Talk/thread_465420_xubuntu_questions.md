---
title: "xubuntu questions"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-05
I'd like to recover some of the older abandoned machines at school, and it looks like xubuntu works with lesser resources  (ie machines that are slower than maybe 300 MHz and don't necessarily have loads of RAM) However, I can find no reference to a localised in Italian version. Does it exist?

Second question- any hints or pointers to HOWTOs about using older machines would be gratefully received by this willing but inexperienced newbie who just hates to see that hardware lying around unused, particularly when the school just doesn't have enough machines to go around anyway.

---

### Post by kerry_s on 2007-06-05
during the install you pick your language. not all old hardware will work with xubuntu, you might have to trim some down to a custom install with lighter stuff. ram is the real killer you want 128 minimal, any less than that and you just got to try it and see.

try dsl for those really old ones-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
and
debian has good old hardware support-> [http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)
debian mini net installer-> [http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://ftp.gtlib.gatech.edu/pub/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-businesscard.iso)

---

### Post by ginestre on 2007-06-06
Thanks for that. I'll look at the distros you suggest, and hope to make head and/or tail of it. It's all very new, rather exciting but more than a little beyond me. Nevertheless I think it's important.

> **kerry_s said:**
> .........not all old hardware will work with xubuntu, you might have to trim some down to a custom install with lighter stuff. ram is the real killer you want 128 minimal, any less than that and you just got to try it and see.





A follow up question if I may. You say that not all old hw will work with xubuntu- is the same warning also valid for other flavours of ubuntu, because hw detection is different from version to version? And if so, is this a consideration to make- ie, should I go for one flavour rather than another given that I'm still on a steep learning curve? Bearing in mind that tehse machines are for school, where there is really no technical assistance beyond my extremely limited (in both time and skills) efforts, ease of use and stability are primary considerations. But I find the present situation, in which the students don't have access to computers because windows keeps breaking and noone can fix it, with the end result that every so often the entire budget is spent on buying a couple of newer machines which then promply present identical problems, morally, ecologically and politically  wrong, so I'd really like to do something. All input gratefully received.

---

### Post by Haus Neuerburg on 2007-06-06
I just installed xubuntu 6.06.1 dapper on my acient pc (128RAM/400MHz/4GB HDD): it works fine, faster as Windows 98 which was on it before, I have, naturally, no partitions and the computer is much faster now. If the school needs the OOo-package than maybe the machine will slow down again because it gobbles up loads of memory space ;-), but if all they need is quick online access, it should be ok. 
Just one more thing: I tried installing from the live CD but got stuck on the second screen where the local settings are made: not enough RAM. I then did the installation from the alternate CD which is ok, too even if you're unexperienced

---

### Post by kerry_s on 2007-06-06
> **ginestre said:**
> Thanks for that. I'll look at the distros you suggest, and hope to make head and/or tail of it. It's all very new, rather exciting but more than a little beyond me. Nevertheless I think it's important.





A follow up question if I may. You say that not all old hw will work with xubuntu- is the same warning also valid for other flavours of ubuntu, because hw detection is different from version to version? And if so, is this a consideration to make- ie, should I go for one flavour rather than another given that I'm still on a steep learning curve? Bearing in mind that tehse machines are for school, where there is really no technical assistance beyond my extremely limited (in both time and skills) efforts, ease of use and stability are primary considerations. But I find the present situation, in which the students don't have access to computers because windows keeps breaking and noone can fix it, with the end result that every so often the entire budget is spent on buying a couple of newer machines which then promply present identical problems, morally, ecologically and politically  wrong, so I'd really like to do something. All input gratefully received.



Well, i'm a debian person so i kinda stick with debian based systems, there is tons of info on the net for debian. For something like a school, i would go with dsl(damn small linux) because it can be installed as a image(frugal), just like running the cdrom all the time, every boot will be brand new and clean and they can't easily change it, for the machines that have enough ram it can run completly in ram, so no moving parts makes it fast. The only thing is it is a big learning curve, you just need to play with it and get to know how it functions, it can run as live cd so you can use any computer to practice with out messing up the computer, if you have any problems there forum is very good at helping.

---

### Post by dstew on 2007-06-06
I have Xubuntu Dapper on my old machine. It works well, but sometimes is a little slow. The biggest issue I have is that there is a noticeable lag time when typing, using the Abi word processor. That will probably be an issue in a school setting if the students are going to do a lot of word processing.

If you have 128 Mb RAM, you need to install using the Alternate Install CD. It is one of the options listed on the [Xubuntu download page]("http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/").

---

### Post by kerry_s on 2007-06-06
> **Haus Neuerburg said:**
> I just installed xubuntu 6.06.1 dapper on my acient pc (128RAM/400MHz/4GB HDD): it works fine, faster as Windows 98 which was on it before, I have, naturally, no partitions and the computer is much faster now. If the school needs the OOo-package than maybe the machine will slow down again because it gobbles up loads of memory space ;-), but if all they need is quick online access, it should be ok. 
Just one more thing: I tried installing from the live CD but got stuck on the second screen where the local settings are made: not enough RAM. I then did the installation from the alternate CD which is ok, too even if you're unexperienced


I'm using a ancient vaio pcg-f430 450mhz 256ram(64 stock,upgraded to max) 20gig hd(upgraded it from the stock 6gig) and this puppy flies. I'm running a custom debian server install with fluxbox. If you want speed go custom, just install what you need.

-> [http://ftp.gtlib.gatech.edu/pub/debi...sinesscard.iso](http://ftp.gtlib.gatech.edu/pub/debi...sinesscard.iso)

type> server
reboot when its done
login  as root
apt-get install xorg gdm synaptic fluxbox thunar leafpad dillo
reboot
select fluxbox in session and login

i reccomend you learn to use opera, it's faster on old systems.
repo->
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free 

key->
gpg --keyserver subkeys.pgp.net --recv-key 033431536A423791
sudo gpg --armor --export 033431536A423791| sudo apt-key add -

---

### Post by meborc on 2007-06-06
this - [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) - is also a good read on installing ubuntu on low memory systems!

btw - xubuntu rocks on my c2d 6600 2gig ram nvidia 7900gs also... a good distro for low AND high memory systems!

---

### Post by buuntuu! on 2007-06-06
ubuntu è una delle distro migliori X chi sta iniziando con linux secondo me... forum  e documentazione sono ottimi, quindi anche se avrai qualche problema ci sarà quasi sempre subito qualchuno che ti può aiutare!

se fossi in te farei un tentativo con xubuntu, se il RAM nondovesse  bastare puoi fare un server install con un window-manager più [leggero]("http://ubuntuforums.org/showthread.php?t=103806") di xfce (il wm di xubuntu) consiglierei fluxbox, molto leggero ma non troppo spartanico - bisogna fare pubblicità X linux con i ragazzi a scuola ;)

viva i PCnosauri!

---

