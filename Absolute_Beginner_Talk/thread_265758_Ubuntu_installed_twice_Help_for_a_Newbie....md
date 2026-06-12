---
title: "Ubuntu installed twice?? Help for a Newbie..."
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by computergirl on 2006-09-26
Hi, Im a newbie to this OS system. It was recommended to me by my instructor, giving me a challange to use a new OS. I love this Linux/Ubuntu OS! Anywhoo, I installed it as a partition on my HDD, giving my the choice to boot up in WINXP or UBUNTU. Well my system was fine til this a.m. When I turned my maching on, rather than showing the linux system, recovery system, mem chech, win ntfs, and windows xp; it gave me DOUBLE linux OS's! How could of this happened? And how can I get rid of one of the OS on the partition? I also noticed on the newer one made that there is no password loggin when im in administrative (i.e., networking) options. Can I have a viruse? Can someone be getting into my system? Please let me know, and ask any questions If this is not detailed enough to help.

Thank you

---

### Post by Bachstelze on 2006-09-26
Aren't the numbers different on the Ubuntus ? If so, that's because you have two versions of the kernel installed. If the new one works fine, you can remove the old one with Synaptic.

---

### Post by Perfect Storm on 2006-09-26
It's properly a previous kernel that you can see. It's normal. You can uninstall the previous kernel via synaptic package manager.

Don't worry you havn't installed ubuntu twice ;)

---

### Post by jordanmthomas on 2006-09-26
In a terminal, type
```
gksu gedit /boot/grub/menu.lst
```
Comment out (put a # in front of) the lines you don't want in the OS section.
To remove
```
title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

```
do this
```

[COLOR="Red"]#[/COLOR]title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
[COLOR="Red"]#[/COLOR]root            (hd0,0)
[COLOR="Red"]#[/COLOR]kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda1 ro single
[COLOR="Red"]#[/COLOR]initrd          /boot/initrd.img-2.6.15-27-686
[COLOR="Red"]#[/COLOR]boot

```

Personally, I would get rid of the recovery modes if you are worried about people logging onto your system, or at the very least set a root password
```
sudo passwd root
```

As for your password troubles, is this after you have already put in a password recently?
The system will remember that you have put in your password recently and won't ask you for a few minutes.  You can make it "forget" by typing
```
sudo -k
```

Hope this helped

---

### Post by bulldog on 2006-09-26
Let us see the outcome of 

sudo fdisk -l [as in like]

and 

cat /boot/grub/menu.lst

if it's not too much trouble.

Edit:Much too late :D

---

### Post by Bachstelze on 2006-09-26
AI, while you're here, could you tell me where I could get widgets like yours for KDE ?

Sorry for the thread hijacking, computergirl ;)

---

### Post by computergirl on 2006-09-26
Thank you. I will restart and check. Now, do I have to use theSynaptic? Now I may get fired down for saying this, but cant i delete it from the drive like in WIN? Like i said I am new with this, my instructor told me to try this system, it is awesome, If I didnt do graphic design, Id turn my whole system to this linux os. 
Please reply - before i restart. 
Thanks guys(gals)!

---

### Post by jordanmthomas on 2006-09-26
--for KDE widgets, try superkaramba

---

### Post by Bachstelze on 2006-09-26
The safe bet is to not touch anything. The extra kernel eats only about 30 MB of diskspace so it's not really annoying.

jordanmthomas > thanks :)

---

### Post by Brunellus on 2006-09-26
those kernels add up, though.

I dist-upgraded to dapper from breezy when dapper was still in development.  I was getting kernels every few days, and ended up keeping all of them (in case there was a problem with an update, I could always boot back into my "last known good" kernel).

Well, recently, I finally de-cruftified my machine (somewhat) and removed 1.5 GiB worth of kernel images!

In practice, you can use synaptic (recommended) to remove kernels.  I keep the last two good kernels, and discard older ones as they are superceded.  On the other hand, you may find that newer kernels break some functions for you, especially if you have weird hardware.  Then you determine what kernel you really need and apt-pin it.

---

### Post by computergirl on 2006-09-26
Thank you all for being helpful. 
I appreciate it!
;)

---

### Post by steve.horsley on 2006-09-26
Once you are sure the newer kernel version is working OK, you can delete the old kernel. Search in synaptic for **linux-image**. Make sure you leave the newest one.

It's best to use synaptic to delete the old ones because doing it that way gets your boot menu corrected, and synaptic won't keep thinking it's installed after you deleted it.

---

