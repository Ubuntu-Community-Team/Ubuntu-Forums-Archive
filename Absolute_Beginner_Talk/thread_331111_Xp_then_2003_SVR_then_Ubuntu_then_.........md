---
title: "Xp then 2003 SVR then Ubuntu then ........"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2007-01-04
Hi right now i am using windows xp, then windows 2003 SVR then Ubuntu 6.10 now i want to install one more linux OS is this Possible.

---

### Post by kidders on 2007-01-04
Hi there,

Yes, you can install as many OSs as you like (or have space for!).

---

### Post by lucky_chouhan on 2007-01-05
My question is persent my system is running 

c:\Windows xp
d:\windows 2003
e:\data1
f:\data2
g:\data3
Ext2:\Ubuntu6.10

now if i delete data3 (15 GB) and install suse (example) 

after setup can i get this type grub menu -

Ubuntu 6.10
Suse 
Other Operating system (Windows xp, 2003 etc.)
My is - Windows Xp
           Windows 2003 server

---

### Post by kidders on 2007-01-05
Hey again,

You can. Check out grub's man pages for how to do it ... imo it's easiest just to rewrite menu.lst yourself, once you have all your operating systems installed the way you want them. If there's an upper limit on the number of menu items grub can manage, it's pretty high, I'd say.

One thing worth noting it that many Linuxes like to rewrite your bootloader when their update managers upgrade your kernel. When you're all set up, it might be worth thinking about how to manage that sensibly ... sharing your grub config between all your OSs, or uninstalling grub from all your Linuxes except one would be two possibilities.

---

### Post by lucky_chouhan on 2007-01-05
If i installed Suse in data3 format as linux type after installing suse the suse linux grub rewrite on my exist boot loader that is ubuntu. so suse boot loader detect buntu and 2 windows OS.

One time I install xp then 2003 then Vector Linux then Suse but suse overwrite on my vector linux.

---

### Post by kidders on 2007-01-05
It *overwrote* a filesystem without asking?! :eek: Wow. That sounds like something Windows would do!

---

### Post by lucky_chouhan on 2007-01-05
Its not overwrite file system file system is exist only grub overwrite. vector linux is still some partition

---

### Post by kidders on 2007-01-05
Ah, in that case, a simple tweak to your menu.lst is all you would need.

This is why I mentioned coming up with some strategy for dealing with bootloader rewrites. If you have two or three copies of grub, each overwriting the other at random intervals, you'll very quickly get totally confused! How you'd prefer to sort it out is very much up to you, though.

Incidentally, even if an OS doesn't appear in your grub menu, you can still boot into it with the grub console. Little bonuses like this are, perhaps, the reason Ubuntu (and so many others) have opted for grub by default, rather than lilo, etc.

---

### Post by lucky_chouhan on 2007-01-05
some time for testing

---

