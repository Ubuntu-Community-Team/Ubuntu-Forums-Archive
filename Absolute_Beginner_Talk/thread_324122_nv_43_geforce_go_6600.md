---
title: "nv 43 geforce go 6600"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by jadda on 2006-12-23
the default resolution on my 15,4 " screen is 1200x800, but the highest resolution Ubuntu offers is 1024x768. I've innstalled the 915resolution package and the nvidia driver from 

sudo apt-get install nvidia-glx 

then i used the 

sudo gedit /etc/default/915resolution

command and completed the relevant details for xres and yres. nothing happend so i modified the  xorg.conf, but again, nothing happend. 

can anybody help me? I've been working with this problem for 2 days, I've got a serious headache because of the resolution, and I don't see the point of running linux when something as easy as changing the screen resolution should take 2-3 days.

---

### Post by Malta paul on 2006-12-23
Hi,
I am also using a Geforce 6600 video card, and have downloaded the latest Nvidia drivers using Automatik2. 

I would say your monitor with a max resolution of 1200 X 800 _will not_ give you a higher resolution than 1024 X 768.

I have just checked the resolutions available above 1024 X 768,it is 1152 X 864, then 1200 X 800, and 1280 X 1024.         

I use 1280 X 1024 @ 75HZ on a  15 Inch. TFT monitor with very good results. 
Hope this is of some help to you, Good luck ;)

---

### Post by jadda on 2006-12-23
where do I find automatik2?

---

### Post by Malta paul on 2006-12-24
[url]http://www.getautomatix.com/wiki/index.php?title=Installation

Follow the instructions and it will install in Applications>System Tools   :)

---

### Post by spockrock on 2006-12-24
have you tried using
sudo nvidia-xconfig

to setup create a new xorg.conf file??

---

### Post by closey on 2006-12-24
> **Malta paul said:**
> Hi,
I am also using a Geforce 6600 video card, and have downloaded the latest Nvidia drivers using Automatik2. 

I would say your monitor with a max resolution of 1200 X 800 _will not_ give you a higher resolution than 1024 X 768.

I have just checked the resolutions available above 1024 X 768,it is 1152 X 864, then 1200 X 800, and 1280 X 1024.         

I use 1280 X 1024 @ 75HZ on a  15 Inch. TFT monitor with very good results. 
Hope this is of some help to you, Good luck ;)

Firstly I think his resolution is probably 1280x800 which is a pretty standard laptop screen resolution, I had it on my old Nvidia Geforce 6600 Go. As mentioned above though, you should just install the latest Nvidia drivers. If automatix doesn't work too well you can try downloading the package from the official nvidia site but you will have to install it on the command line. If you do this though, make sure you don't have the linux-restricted-modules package installed because it will probably conflict with it. See [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) for more info.

---

