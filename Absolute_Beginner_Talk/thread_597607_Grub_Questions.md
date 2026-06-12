---
title: "Grub Questions"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by infamous16 on 2007-10-30
So I'm dual booting with xp, so I can keep all my files and for my little brother to use the computer with something that is familiar with him. And I have a few questions.

1. I have ubuntu 7.10 right now, and thats what I had first. I once installed kubuntu to that partion over ubuntu because I wanted to try something different. The Grub loader at the beginning still said ubuntu 7.10 now kubuntu....is it supposed to?

2. How can I make windows xp boot first instead of ubuntu, because sometimes my brother will just turn on the computer and come back in a little bit and I'd rather not have him trying to mess around with my stuff.

Thanks a bunch!!!

---

### Post by mikewhatever on 2007-10-30
To change the default OS to boot, check out this [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

If it bothers you, change what it says in the menu from Ubuntu to Kubuntu or to anything else you like.

---

### Post by Pumalite on 2007-10-30
# 2.- Edit menu.lst. Change the line 'default' from '0' to the number that Windows is in the list minus one (Grub starts counting from 0)

---

### Post by maybeway36 on 2007-10-30
1. Yes, they use the same kernel and core components.

---

### Post by stchman on 2007-10-30
> **infamous16 said:**
> So I'm dual booting with xp, so I can keep all my files and for my little brother to use the computer with something that is familiar with him. And I have a few questions.

1. I have ubuntu 7.10 right now, and thats what I had first. I once installed kubuntu to that partion over ubuntu because I wanted to try something different. The Grub loader at the beginning still said ubuntu 7.10 now kubuntu....is it supposed to?

2. How can I make windows xp boot first instead of ubuntu, because sometimes my brother will just turn on the computer and come back in a little bit and I'd rather not have him trying to mess around with my stuff.

Thanks a bunch!!!

I have a GRUB tutorial.

[http://www.stchman.com/grub_menu.html](http://www.stchman.com/grub_menu.html)

---

