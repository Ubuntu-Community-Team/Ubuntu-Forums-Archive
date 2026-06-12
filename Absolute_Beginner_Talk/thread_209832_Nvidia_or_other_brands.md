---
title: "Nvidia or other brands?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-07-05
What is the best video card brand to run Ubuntu?

There are a lot of companies having GeForce video cards.. Does it matter which company I choose? (Asus, Sapphire, etc.)


For NVIDIA video cards, are there good software support?
I know there is a driver called nvdia-glx or something. Is it developed by the open source community or the Nvidia company?
Why would people install nvidia-glx instead of the drivers in the nvidia website?

Thanks!

---

### Post by nalmeth on 2006-07-05
Nvidia has pretty good linux support. nvidia-glx is nvidia's proprietary driver, made into an ubuntu package to make it easier to install.

nv is the open-source nvidia driver, but to get the full use out of your card you'll want the proprietary one.

---

### Post by someusernoob on 2006-07-05
> What is the best video card brand to run Ubuntu?

There are a lot of companies having GeForce video cards.. Does it matter which company I choose? (Asus, Sapphire, etc.) Doesnt matter that much. The only difference between the companies is how they set the clock frequencies on the ram and the core. And sometimes one company puts a game in the package, while the other only fills it with manuals and air.


> For NVIDIA video cards, are there good software support?I own a n6600 (Asus) and it works without any problems under Ubuntu. Setup takes about 30 seconds.


> Why would people install nvidia-glx instead of the drivers in the nvidia website?Whenever you get a kernel update, all packages needed by the driver are updated too. When you manually download the driver you have to update it yourself. They work great btw. I'm running XGL/Compiz (everything enabled) & still can play games (Neverwinter Nights, Penguin Racer etc.) without problems.

---

### Post by richbarna on 2006-07-06
I vote for original nVidia cards. I've got a normal 5200 fx, and it works "out of the box" with every distro of linux that I have.

---

### Post by woedend on 2006-07-06
ive got the 5200fx 128mb also.  It works great with linux and has plenty of power for desktop effect(although in some particular new games it will show its ugly age...but im not a pc gamer). 
You can get them dirt cheap remanned off the net.
But if buying new/top of the line...i definetely like nvidia the best.  They at least work with the linux community, although not releasing their code.

---

### Post by BIZKeT on 2006-07-06
I know there is a command to 'automatically' update the nvida graphics driver from a repository, but is there one for the chipset driver?

On a similar note, how do I check to see what packages are in the repository?

---

### Post by richbarna on 2006-07-06
[QUOTE=BIZKeT]I know there is a command to 'automatically' update the nvida graphics driver from a repository, but is there one for the chipset driver?

On a similar note, how do I check to see what packages are in the repository?[/QUOTE]

I'm not sure about the chipset driver, but to check the repo you just use synaptic.
For more info, checkout my "sig" (nVidia Drivers HERE)
|
|
v

---

### Post by BIZKeT on 2006-07-06
[QUOTE=richbarna]I'm not sure about the chipset driver, but to check the repo you just use synaptic.
For more info, checkout my "sig" (nVidia Drivers HERE)
[/QUOTE]

I have read that page (found it from your link a while back :) ) but it deals with just the graphics driver. I need the chipset driver so I can get the onboard network connection working.

BIZKeT

---

### Post by nameiwantistaken on 2006-07-06
nVidia makes their own linux drivers and they offer more support than any other company pretty much.  In terms of what card you need, if you're just doing basic things (ie no gaming, 3d work, etc), just get the cheapest used card you can find.

---

