---
title: "Retrying to Dual Boot"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by lordmorg on 2006-03-13
I'm going to retry to dual boot with Ubuntu to my system. 

The following is my specs:
Intel p3 566mhz
128 ram
20 gb

I first try to dual boot with ubuntu but fail. Both windows and ubuntu were giving me errors and wouldn't start up 

My question is do you need a higher memory to achieve a perfect dual boot
, i'm not concern about the speed and performance but rather if you need a higher memory to have a dual boot set in your computer.

---

### Post by AtinLango on 2006-03-13
What errors?

---

### Post by patrick295767 on 2006-03-13
[QUOTE=lordmorg]I'm going to retry to dual boot with Ubuntu to my system. 

The following is my specs:
Intel p3 566mhz
128 ram
20 gb

I first try to dual boot with ubuntu but fail. Both windows and ubuntu were giving me errors and wouldn't start up 

My question is do you need a higher memory to achieve a perfect dual boot
, i'm not concern about the speed and performance but rather if you need a higher memory to have a dual boot set in your computer.[/QUOTE]
  
You may dual boot with any pc old or not ... prehistoric pc too... 
You could use the wingrub or grub of linux. The Grub (ubuntu linux installation) is installed in the MBR of your harddisk. 
  
I think the grub is the easiest solution 'cos when u install linux, it's automatic. 
You can use also dd function in order to make backup of ur MBR (....).
  
You should know what you have in ur MBR.
To remove Grub from the MBR, with a bootable CD or floppy disk, you may type: 
fdisk /MBR
  
Could you give more details ab. errors & content of ur MBR (grub?) ?
(fdisk /dev/hda -l) 

Greetings

---

### Post by meborc on 2006-03-13
for dual boot use guides from this page - [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

