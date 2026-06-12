---
title: "Weird Grub menu??? (After Ubuntu Studio)"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-06-14
Ok, so I turned my regular Ubuntu into Ubuntu Studio by downloading the appropriate programs etc...

So now my Grub menu shows all this stuff:

> 
Ubuntu Kernel 2.6.20-16-low latency
Ubuntu Kernel 2.6.20-16-low latency (recovery mode)
Ubuntu Kernel 2.6.20-16-generic  <---------------------------------------This is the one I select
Ubuntu Kernel 2.6.20-16-generic (recovery mode)
Ubuntu Kernel 2.6.20-15-low latency
Ubuntu Kernel 2.6.20-15-low latency (recovery mode)
Ubuntu Kernel 2.6.20-15-generic
Ubuntu Kernel 2.6.20-15-generic (recovery mode)
Ubuntu Memtest
Microsoft Windows XP


Just note, I use the Ubuntu Kernel 2.6.20-16-generic. Xorg crashes on the low latency ones.
What the heck is all this? Why does it show the grub menu even when I don't ask for it (ie hit ESC key), and what can I do to clear it up. IE- make it normal, heck, I'm want to remove all the ubuntu studio stuff, it's way too much. I just wanted 3 programs. Help!

---

### Post by raeb on 2007-06-15
Hmm... maybe the kernel update screwed up your /boot/grub/menu.lst.  If you want to have grub stay hidden, you need to edit your menu.lst file.  Uncomment the "#hiddenmenu" option (remove the pound so it's just hiddenmenu).  Set the "timeout" option to however long you want, the number is seconds.  If you want to remove the extra kernels, scroll down the the Automatic Kernels List near the bottom, and remove the entries you don't want to appear.

EDIT: changed xorg.conf to menu.lst

---

### Post by Inxsible on 2007-06-15
> **raeb said:**
> Hmm... maybe the kernel update screwed up your xorg.conf.  If you want to have grub stay hidden, you need to edit your xorg.conf file.  Uncomment the "#hiddenmenu" option (remove the pound so it's just hiddenmenu).  Set the "timeout" option to however long you want, the number is seconds.  If you want to remove the extra kernels, scroll down the the Automatic Kernels List near the bottom, and remove the entries you don't want to appear.

you probably mean the /boot/grub/menu.lst and not the xorg.conf :)

---

### Post by NeoLithium on 2007-06-15
Well, you can remove the low latency kernels by opening up the synaptic package manager and searching for linux-image; select the kernels you don't want and mark them for removal. Just be absolutely sure you pay attention to which ones you are taking away, so you don't get rid of one that you need :)

---

### Post by raeb on 2007-06-15
> **Inxsible said:**
> you probably mean the /boot/grub/menu.lst and not the xorg.conf :)

Aye, it's been a long day.

---

