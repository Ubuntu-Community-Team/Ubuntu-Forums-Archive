---
title: "dual-boot windows without breaking existing ubuntu?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-19
i only have ubuntu on my system, but for a handful of reasons, i need windows on my computer for emergency purposes. how would i go about installing windows without messing things up? (boot record, etc)

---

### Post by happy-and-lost on 2006-09-19
Can't remember exactly, but I think that there's a util. somewhere on the Ububtu Dapper CD which allows you to reinstall the GRUB. Boot into the CD and take a looksie.

---

### Post by bodhi.zazen on 2006-09-19
It is easy. I like this guide, although there are others.

[Dual boot Ubuntu & Windows](http://users.bigpond.net.au/hermanzone/)

Did you ever get you monitor working?

---

### Post by shanepardue on 2006-09-19
> **bodhi.zazen said:**
> It is easy. I like this guide, although there are others.

[Dual boot Ubuntu & Windows](http://users.bigpond.net.au/hermanzone/)

Did you ever get you monitor working?
thanks man! you're solving all my problems! unfortunately, i haven't gotten the monitor fixed. i posted a reply this morning if you want to check that thread out. i'm feeling a little hopeless on the whole nvidia on the toshiba homefront.

---

### Post by rocknrolf77 on 2006-09-19
Also check out super grub. Just download it and burn the iso. [http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/)

---

### Post by shanepardue on 2006-09-19
this guide does, however, explain the process for people with windows systems wanting to dual-boot their ubuntu. mine would be reversed. would i just install windows and reinstall grub?

---

### Post by bodhi.zazen on 2006-09-19
> **shanepardue said:**
> this guide does, however, explain the process for people with windows systems wanting to dual-boot their ubuntu. mine would be reversed. would i just install windows and reinstall grub?

Yes.

---

### Post by shanepardue on 2006-09-19
right on. thanks for your help on this matter. i'll respond to the other thread this evening when i'm on that computer. thanks again for all your help!

---

### Post by Drakkor on 2006-09-19
Fastest way to reinstall grub to the mbr of windows to dual boot
OK,boot to the live Ubuntu CD
Open terminal type ```
sudo grub
```
At the **grub>**prompt enter these commands
```
find /boot/grub/stage1
```
This will return a location like (hd0,1)
still in terminal type
```
root (hd?,?) 
```use the values from the find command
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Enter ```
quit
```
reboot to the hard drive,and you will be given the grub menu to select what you want to boot Ubuntu is default and XP would be at the bottom,just hold down the down arrow key ! :-P

---

### Post by shanepardue on 2006-09-19
i appreciate that drakkor! i'll get on that. of course i'm still super apprehensive about putting windows back on my machine after about a year without micro$oft, but i feel i don't have a choice.

---

### Post by Drakkor on 2006-09-19
Lol,just make sure to not put windows on the Ubuntu partition ! :D

---

### Post by shanepardue on 2006-09-19
> **Drakkor said:**
> Lol,just make sure to not put windows on the Ubuntu partition ! :D
ha now you got me freaking out...i'll make sure to push the button while holding my finger with the other hand!!

---

