---
title: "Configuring modem with Kernel"
date: 2005-03-09
forum: Apple PPC Users
---

### Post by michelem on 2005-03-09
How i can make to configure kernel to detect and use my internal modem? 
I know that's difficult but i'd like to learn to do it...  :)   
I saw the site linuxant.org and linmodems.org but i haven't resolved the problem. I repeat, It's Conexant Rockwell Aztech MDP3858V-E.

Bye

---

### Post by az on 2005-03-09
"I saw the site linuxant.org and linmodems.org."

For a conexant modem, you need to buy the drivers.  The company who makes the modem does not care about you or your right to run open source software in your computer.  There is no other driver.  It would be cheaper to just buy another modem.

---

### Post by Viro on 2005-03-09
[QUOTE=michelem]How i can make to configure kernel to detect and use my internal modem? 
I know that's difficult but i'd like to learn to do it...  :)   
I saw the site linuxant.org and linmodems.org but i haven't resolved the problem. I repeat, It's Conexant Rockwell Aztech MDP3858V-E.

Bye[/QUOTE]
 The first thing you need is a kernel source tree. Just download the kernel sources and learn to compile your own kernel. That'll make the instructions to install a kernel module much much much easier. Plus, it's always a good thing to know how to compile your own kernel anyway.

Then download the driver from linuxant, and the steps should be pretty straight forward from there. The only tricky bit is knowing about compiling kernel modules, which you will know how to if you compile your own kernel.

---

