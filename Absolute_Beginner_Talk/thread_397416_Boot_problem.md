---
title: "Boot problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by rahman-87 on 2007-03-30
Hey,
1.i wanted to install ubuntu.so i ordered the ubuntu 6.06 cd.After getting it i booted from the cd.Then there came a option run or install Ubuntu.So i selected the option.Then it started loading.Then this showed up
"uncompressing ubuntu-ok.Loading kernel...."
i waited for about one hour but nothing happened.Is the problem related to my pc or the cd?how can it be resolved.
ram:512mb
processor: core 2 duo 1.86 GHz x86 
cache : 2mb
mother board:  D946GZis essential series
sata hard drive

2.i installed fedora.how can i run .exe files there.I need to run .exe file cause all my drivers software is .exe file

---

### Post by mrmonday on 2007-03-30
I am not sure about no. 1, but for number 2 it is not possible. .exe files are for windows. Wht are you trying to install drivers for? there are usually linux drivers.

---

### Post by dstew on 2007-03-30
Problem no. 1 is probably related to your CD. Boot it again and select the option to check it for errors instead of "Start or Install".

---

### Post by dannyboy79 on 2007-03-30
try to use a boot option when you click to run from the live cd. how you handle this is
At install with edgy you have to add :
irqpoll noapic nolapic
before "--" to kernel options 
At first boot after install when you see grub menu :
press e
select the kernel line, go to the end of it and add the same sequence
press ENTER
press b

When boot is done from a terminal or console, do :
sudo nano /boot/grub/menu.lst
edit this line :
# defoptions=ro quiet splash
so it looks like this :
# defoptions=ro quiet splash irqpoll noapic nolapic
CTRL + O
CTRL + X
then type :
sudo update-grub

Now edgy will always boot with the required sequence you added

You're done


as far as running .exe. well you can run them if it's a program and it can be run thru emulation using WINE. otherwise if it's a driver install for windows than no, it won't work. in linux, we use modules to support various hardware. what kind of hardware do you have that you need drivers for? can you post the output from typing this into a terminal line

lspci -v

---

