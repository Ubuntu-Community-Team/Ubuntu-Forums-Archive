---
title: "how do set mbr to use gentoos grub?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by turtles on 2006-11-19
I have installed ubuntu to test it out on a spare 20 gig drive. It seems very nice everything just works.
 I asked the installer to install on that spare drive /dev/hdb.
It also installed a grub on that drive wich bypasses my main grub from Gentoo on hda1? I am assuming it switched some flag with fdisk or somthing.
 I would like to continue using that grub  not the new ubuntu grub. I am shure that grub is still there since I created some nice mount points where I can access my gentoo filesystem.
I copyed the revalant lines to my grub.conf (same as menu.lst?) on hda1. 
What is the best way to cahnge the mbr flag with out destroying any data. fdisk?

---

### Post by turtles on 2006-12-27
Well forget Ubuntu what use is a linux distro if there is no community? I guess I'll switch back to Gentoo now. 
Bye

---

### Post by ron999 on 2006-12-27
I'm sure that Gentoo has a better community - NOT
:rolleyes:

---

### Post by smoker on 2006-12-27
hme, life isn't so simple instant answers are always available, maybe there is no one on line at the moment that can answer your question.

maybe you should post a question like this in the gentoo forum in the other operating system section

hope you get an answer soon:-)


just noticed the original post date, i think you should have 'bumped' your post before now, this forum moves that quickly that posts can be pages old in a matter of hours!

---

### Post by louieb on 2006-12-27
I see you posted your question over a month ago. I guess your thread fell through the cracks.  One of the unwritten rules of this forum is the [COLOR=DarkGreen]bump[/COLOR]  That is if after an amount of time [COLOR=DarkGreen](at least 24 hours)[/COLOR] has passed and you haven't got a reply : Go ahead and post a reply to your thread with the word [COLOR=DarkGreen]bump[/COLOR] or [COLOR=DarkGreen]anybody[/COLOR] as the text.
Now to answer you question. You have two copies of GRUB one installed by Gentoo and one installed by Ubuntu. The MBR of your first hard drive now points to the GRUB installed by Ubuntu. and you want the MBR code to point to the GRUB installed by Gentoo. This is a very common question and I have seen it answered a 1000 times both in this forum and in Gentoo's. Rather that write another one see the grub link in my signature or check out the[ Illustrated Dual Boot site]("http://users.bigpond.net.au/hermanzone/").  Remember Google is your friend.

---

### Post by turtles on 2007-01-12
Sorry for being a whining grumpy crank
To use gentoo as your primary os and ubuntu as your 2nd AND if you are installing ubuntu on hdb and have gentoo on hda AND if you allowed ubuntus installer to flag its grub as the first one that boots AND if you are too lazy to change it with a live cd insert the following above the ubuntu entrys in menu.lst
```
title        Gentoo Side
savedefault
configfile   (hd0,0)/boot/grub/grub.conf
real_root=/dev/hda3
panic=15


```
Edit the time out to be quicker if desired and away you go.
Cheers

---

