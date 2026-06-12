---
title: "Grub now shows 4 ubuntu entrys"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Bohlio on 2007-06-03
Hello everyone,

My Grub boot loader used to have i think 2 ubuntu options to boot, regular Ubuntu Kernel blah blah blah, and the same thing except recovery. Now I have 4 Ubuntu options, they are the same things with different Kernel versions (I think). I dont know when the new kernel was added to the list, but i use that and it works fine. Is it recommended that i leave the older kernel option there, or should i remove it? If i should remove it, How would i go about doing that.

Any help regarding configuring Grub, What the kernels are (yes i know, noob question), or any other general information that you think i should know would be greatly appreciated.:D

---

### Post by Inxsible on 2007-06-03
Thats because you updated your computer with the latest kernel. quite possibly the 2.6.20-16 and you already had 2.6.20-15.

I would advise you to keep both of them around until you are sure that the new kernel i.e. -16 works well on your machine. Many people have had lots os trouble with the -16 kernel

---

### Post by ryanVickers on 2007-06-03
It usually is a good idea to keep the old kernels, until you realize the new one works fine.  If it doesn't, go back and use the old one, but since it does for you, go into /boot/grub/menu.lst as root (in terminal: "gksudo gedit /boot/grub/menu.lst" without quotes) and remove the older entries.  Simple!

---

### Post by Inxsible on 2007-06-03
> **ryanVickers said:**
> It usually is a good idea to keep the old kernels, until you realize the new one works fine.  If it doesn't, go back and use the old one, but since it does for you, go into /boot/grub/menu.lst as root (in terminal: "gksudo gedit /boot/grub/menu.lst" without quotes) and remove the older entries.  Simple!

Removing them from the grub menu doesnt un-install them however. If you really want to un-install them you should go to the Synaptic Package Manager and remove them. However it is always a good idea to keep atleast one old (and presumably stable) kernel around.

I am sure he hasnt explored the new kernel fully yet, and it might have holes in it. Some harmless, some not so trivial and some just plain annoying.

I get phantom drive icons for my CD/DVD drive, but when i click on it..it gives me mount errors...the other actual icon works flawlessly. so mine would be a harmless as well as annoying problem :)

---

### Post by ryanVickers on 2007-06-03
> Removing them from the grub menu doesnt un-install them however. If you really want to un-install them you should go to the Synaptic Package Manager and remove them.

right, yeah.  Not thinking here! :p

Well, I myself find the menu never opining unless I hit ESC because it's unnessessary at this point.  But your right, explore everything, and then *fully* remove them I guess...

---

### Post by Dougie187 on 2007-06-03
If you do keep an old kernel around just incase something happens, and you dont want it to show up in your grub menu you can just comment out the lines in your menu.lst file. That way they wont show up, but if you need them you can just uncomment the lines and they will come up just fine.

---

### Post by Bohlio on 2007-06-03
Thank you all for your help. I will keep the older version of the kernel around for a while untill i find out if the new one is perfectly stable. As Inxsible said, I havent fully explored the new kernel as i am a relatively new Ubuntu user. Thanks again, This community is AWSOME! :-D

---

